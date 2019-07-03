# RFCs

RFCs for the Agnir project

## What exactly is an RFC?

RFC, meaning *Request For Comment*, is the name given to documents detailing ideas for changes within a project that may require non-trivial work to complete, or may affect an aspect of the project in a significant way.

In Agnir, RFCs are used as a way to propose changes to the game, engine, associated tools, protocols, and generally any other thing relating to the game including technical, gameplay, artistic, musical or publicising decisions.

RFCs are used in many other projects and organisations and have proven themselves to be an effective way of encouraging good design and engaging a community in productive discussion, as well as providing a history of past changes and the discussion that occured when making them.

## How does the RFC process work?

Generally speaking, RFCs go through several stages throughout their lifetime.

- **Submission**: At this stage, the RFC is written up by whomever first wanted to propose the change. They fork this repository, add the RFC to it, and then open a merge request to have the RFC included in the public repository.

- **Debate**: Members of the community comment on the proposals suggested by the RFC, critiquing it and considering whether the proposal fits with the technical and design goals of the project. This is an open discussion that occurs in a 'tracking issue' for the RFC on the repository. The original proposer is free to defend their idea, or even make changes to the RFC to suit the criticisms given.

- **Freeze period**: After a certain amount of time, usually at least several days (and often more for larger changes), and when a core developer has concluded that a clear consensus about the RFC has been reached by the community, the RFC is designated as entering a 'freeze period'. This usually lasts at least several days and is a time when changes to the RFC should not take place. This gives all interested members of the community a chance to review the suggestions and consider the effect they may have. If considerable disagreement still persists, the RFC may be 'unfrozen' to allow the original proposer to alter their proposals to suit the debate.

- **Acceptance**: If no serious objections are made during the freeze period, a core developer will mark the proposal as 'accepted'. At this point, a tracking issue for the RFC's implementation will be created in the main Agnir repository containing a checklist of changes that need implementing for the RFC to be considered fully implemented. It is now up to the community to implement these changes, and is considered an official part of the project roadmap. Additionally, the RFC may be assigned a milestone such that it is included in a specific future release.

## Civility

While we actively encourage as many people as possible to take part in the RFC process and to make their thoughts known on open RFCs, any aggression or hostilities are strongly frowned upon. Criticism should be impersonal, constructive, and should attempt to move the discussion closer to a solution.

Good RFC comments are clear, well-explained, and give examples that address consider the consequences of a change as objectively as possible.

It is also frowned upon to comment on a discussion thread more than once in a row. This is known as "double-commenting", and only crowds the discussion. If you want to add additional details to your response, use the 'edit' button.

## How can I create an RFC for a feature or idea I have?

Firstly, consider whether the feature is worthy of a full-on RFC. If you're looking for a minor change to the UI layout, it's probably better to open a normal issue on the main game repository.

Secondly, make sure that nobody else has already submitted a similar RFC that you could use to make your voice heard. If someone has a very similar idea, it might be worth adding your voice to theirs by working with them on their RFC.

If you still think your idea is worthy of an RFC, then submitting an RFC is as simple as forking this repository, committing your RFC to it (there is a template in this repository), and then opening a merge request for your RFC to be submitted. For those that are not used to using git, GitLab provides a 'Web IDE' feature that lets you fork, make your changes, and submit without ever leaving your web browser.

**Please note that we use Markdown formatting for RFCs. Refer to [https://www.markdownguide.org/getting-started](https://www.markdownguide.org/getting-started) for more information**

You should place your new RFC within the `open/` directory, naming it `xxxx-my_rfx_name.md`.

Once you've submitted your merge request, you'll be allocated an RFC number by a member of the core developer team. You'll need to rename your file to something following the format `xxxx-my_rfx_name.md`, replacing `xxxx` with the RFC number you were given. Once done, the core developers will accept your RFC submission and it will become a proper RFC, ready to be commented on!
