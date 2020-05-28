Agile Demystified
Mar 4, 2020

There’s an old joke that goes, “If there’s such a thing as a good toupee, I’ve never seen one.” An open secret in Hollywood: leading-man actors such as Ted Danson and Burt Reynolds wear toupees. But not raccoon rugs — extremely expensive, finely crafted ones that no one can identify as different from natural hair.

Agile shares this quality: when it’s good, you don’t notice it. In fact the original Agile manifesto asserts this in its principles: “Prefer people over process.” But too often, organizations bend Agile process to avoid changing difficult internal dynamics. This leads to what Agile manifesto signatory Kent Beck calls ‘Scrum But’, as in, “We practice Scrum, *but*…” (Scrum — discussed later — is so closely related to Agile that they’re often used interchangably).

Software has no physical constraints, and consequently, any software project can rapidly get as complicated as its participants’ wildest imaginations. Sometimes this leads to wonderful new products, but often, it leads to bloated, broken experiences, behind schedule and over budget, burnt out team members. Agile provides an alternative method to triage the scarce resource of team member time. It can be summed up super simply:

Deliver the most important features as soon as possible.

Simple, right? Of course, simple ain’t easy! People frequently overcomplicate Agile because, like a good toupee, they’ve never seen it done right.

The most comprehensive way for me to show you the right way to do simple Agile would be to have you join a project at the beginning, and to “ride along” as we go through the steps. Since that’s not possible in an article, I’ll have to describe the process instead. In the spirit of Agile, I’ll do it as simply as possible, but since simple ain’t easy, it won’t be short. Let’s break it up into three parts:
1. Basic principle
2. Daily practice
3. Story points: estimating software development
Basic principle

In watchmaking, anything except for the hour and minute hand — say, a chronometer, or the date — is called a complication. It makes the mechanism more difficult to implement. But this doesn’t make a watch with only the hour and minute simple! That operation is complex enough, without any added complications.

Simple and complex are not opposites. Simple is the opposite of complicated; complicated means to be more complex than necessary.

Agile strives to deliver features as soon as possible by keeping process to an absolute minimum. But there are minimums, below which lie failure. One of those minimum components is testing.

What is the single most important feature of your project, anyway? There’s a saying some sports folks use: “Second place is just ‘first loser’.” Kind of a rough sentiment, but Agile requires ruthless prioritization. If your most important feature doesn’t work, then does anything else in your project have value?

You might think of the ‘special sauce’ that makes your app a killer. But that’s useless if your users can’t get to it. So features like “log in”, and before that, “create an account”, are actually more important.

The most important feature in all software projects is something along the lines of “it needs to run.” If the website or app or library doesn’t compile and execute, none of the other features matter.

Agile projects require automated testing, full stop. If you’re not testing, you’re not Agile. As we add more and more features down the line, the features delivered previously — by definition more important than later ones — have to remain functional. If a less important/later feature breaks a more important/earlier one, we’ve violated our priorities.

Manual testing can work at first, but as the project grows it becomes inefficient. Also, decades of best practices have shown that code written to be easily testable has immense advantages: drastically fewer bugs, greater support for additional features, and much more. Writing testable code starts out very difficult, but eventually gets easier. Not doing it from the beginning is not an option though, unless you want “development hell” at the end of the project, when changing any one part of the code causes problems somewhere else.

Start with a so-called “smoke test”. The name comes from electronics hardware: if you put power on a circuit and the solder joints start smoking, something basic is terribly wrong. A smoke test just asserts that the page loads, or an object exists, or some other super basic criteria. It also asserts that the test setup works! As the project evolves to support more complex features, the smoke test still has a benefit: when many feature tests fail at the same time, the state of the smoke test helps to quickly determine whether or not the problem affects the entire system.

Pro tip: tests which appear trivially simple can still have a great benefit. Don’t judge a test by its coverage :)

Another place where it appears tempting to cut process actually subtly connects the development and business teams: the handoff from design to development. Newcomers to Agile process often suggest that instead of having business stakeholders write acceptance criteria, developers should work off of mockup images that come from the design team. This seems like an easy way to save time, but it introduces a lot of risk.

“A picture is worth a thousand words” is true; but the value of most of those thousand words is about how the design should look. When you give a developer a picture and ask them to invent how the software should behave, you’re asking them to make business decisions. Developers should know how to program — asking them to perform so far outside their area is inefficient.

Some developers are really good at understanding the business, interpreting business requirements into UI design, and so forth. If you have someone like that, count yourself lucky, but you may still be vulnerable to the greater threat.

“Premature Optimization” is software jargon that means “solving a problem you don’t yet have.” Developers notoriously think about all the requirements the software might ever have. Sometimes they focus on performance, calculating load times based on an imaginary projected number of future users; sometimes it’s about features, making every element of the app infintely configurable “just in case”.

Developers can waste spectacular amounts of time on premature optimization, and the complications added to the codebase can quickly grind progress on valid features to a halt. But they fixate on these points because they’ve gotten burned in the past. Acceptance criteria serve as a guarantee and a guideline for developers, a plan they can stick to with confidence.

The basic principle comes down to making process as simple as possible, but no simpler. Next time we’ll talk about how to do this on a daily basis.
