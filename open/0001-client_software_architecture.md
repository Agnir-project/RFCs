- Feature Name: Client architecture
- Start Date: 2019-08-21
- RFC Number: 0001
- Tracking Issue: 

# Summary
[summary]: #summary

This RFC explain choices in client software architecture.

# Motivation
[motivation]: #motivation

The client architecture is extremly important to let the player have the best experience in the game.
We need at least:
- low latency inputs
- interpolation
- decents fps

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

The client architecture is not destined to end user.

# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

## Data

To make a modern client software we need to use properly the multiple cores of our processors.


To do so:
`World` data structure will be the main data entry.
The data have to be deployed between multiple thread so a `Arc<Mutex<World>>` will be used to share data across them.

## Logic

The whole logic will be handled by 3 threads. We choose 3 threads because most of the today processors have 4 cores
The idea is that at any time one of the 3 threads can spawn another thread to handle an heavy computation with the help of another thread.

- The server listener thread
- The input listener thread
- The render thread

### Server listener thread

The server listener thread listen to UDP packet from the server and update accordingly the `Arc<Mutex<World>>` state.

```Rust
fn handle_map_update(req: Request, world: Arc<Mutex<World>>) -> RequestResult {
    let unlocked_world = world
        .lock()
        .ok_or(HandlerError::CannotAquireWorld)?;
    
    let world_update_request = req.parse::<WorldUpdate>();

    let updated_chunk = unlocked_world
        .map
        .get_chunk(world_update_request.updated_chunk)
        .ok_or(HandlerError::BadRequest)?;

    updated_chunk
        .update(unlocked_world.updated_chunk)
        .map_err(HandlerError::from)?;
    Ok(())
```

For example this request handler will be launched when the server notify the client with a chunk update in the world.

### Input listener thread

The input listener thread will notify the server for protocol specified actions. ([RFC #????](https://www.youtube.com/watch?v=dQw4w9WgXcQ))

All actions are listed in the previously linked RFC.

### Render thread

The render thread read the `World` data structure and draw the whole word with the [Rendering library (code name `render-lib`)](https://gitlab.nwmqpa.com/Agnir/render-lib) project.

# Drawbacks
[drawbacks]: #drawbacks

Their is no drawbacks

# Rationale and alternatives
[alternatives]: #alternatives

Their is plenty of alternatives that we should discuss in comments.

# Prior art
[prior-art]: #prior-art

- This approch is great on multi cores processors but. not really good on others. The concept of shared mutable state across threads is maybe not the modernest option!
- This approch will let users use 100% of their processors to run a fluid game in multipler.

# Unresolved questions
[unresolved]: #unresolved-questions

- Where should we add interpolation. In `World` update or in rendering ?
