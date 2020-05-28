A Beginner’s Guide to Debugging
Mar 30, 2016

Software engineers practice debugging over the course of their entire career. However, it is a prime example of tacit knowledge: an engineer who can expertly solve a bug in record time may have a difficult time explaining the process they used.

The results I found when googling for debugging described how to use a particular tool, but assume the user already has a debugging process. This guide is intended for novice programmers who need help getting started, regardless of the technology involved. I am primarily a web developer, so I’ll give mostly web-based examples, but the principles apply to any complex system. The system doesn’t even have to be a computer — keep reading to find an automotive example.
A guide, because no map exists

Software engineering seems to the beginner like a totally “hard” scientific discipline, and much of it is. In daily practice though, extenuating requirements like time and resource constraints make success a function of craftsmanship, and therefore an art.

No guide can give you explicit step by step instructions to solve your particular problem, so that’s not what you’ll find here. Instead, these principles illustrate good habits which will make you a better debugger faster. Read them, put them into practice, and then revisit later.
Anatomy of a bug

A good general definition of a software bug is a condition where an operation results in undesired behavior. Note the critical term in that definition is undesired behavior. You can describe every bug as a discrepancy between the desired behavior and the system’s actual behavior.

That point is so important it bears restating.

    Every bug stems from some difference between your conception of how the program works and how the program actually works.

The computer behaves with absolute determinism. That’s a ten dollar word that simply means non-random: the same input always produces the same output. If a computer’s behavior appears illogical or chaotic, it’s only because we don’t have enough information about all of the input to identify the pieces responsible for the behavior. Remember the term “input” isn’t limited to user actions, or even system data like program instructions and variable values; it extends to any and all things that affect the system, like hardware and temperature.

I’ve heard so many programmers exclaim “That’s impossible!” when confronted with some behavior, even though the stark fact of the behavior’s existence proves not only its possibility, but also its inevitability. In reality, the behavior is only impossible within their mental model.

This explains exactly why finding the cause of a bug can be so difficult and frustrating: your mental model has to change.
Mnemonic

A mnemonic helps to keep our objectives in mind at all times. I like three (pseudo) E’s: empirical, unequivocal, and efficient.

Empirical means basing everything on observable evidence — no speculation, hunches, or theories.

Unequivocal means there can be no underlying or alternative explanation — rule out all other possible causes.

Efficient seems obvious, but it’s actually the most difficult element. Remember the definition of a bug hinges on something you don’t know. Finding what you don’t know in the shortest possible period of time is quite a challenge.
Empirical means ‘prove it’

How you find out what you don’t know? Just like in school, you test. However in school, you tested on a single subject. When doing social studies, you weren’t expected to catch examples of incorrect math.

In a complex system like modern software apps, different layers interact in subtle ways. Since your bug could hide at different (and possibly multiple) levels within the software stack, you have to test everything.
Prove it

The first rule of debugging is absolute skepticism. Adopt the attitude that you will accept nothing as a fact until you have proven it empirically.

Think your jQuery selector is returning the correct element? Prove it. Think the server is returning a certain piece of data in an ajax response? Prove it. Positive that some subroutine is getting called? Prove it.

It follows that the best weapon in your debugging arsenal is the log statement. Log everything. Prove that all values are what you think they are. When I help novice programmers debug, the most common errors they make involve assumptions:

- treating a variable as if it contained a different value; for example, an object nested inside an array

- mistaken identifiers: similar names, right name but wrong context, id instead of class

- operation not actually getting called, typically because it’s inside a conditional which never gets satisfied

- making changes in the wrong file, failing to restart the server after changes, etc.

To prove you’re looking in the right place, try intentionally breaking code. The program should now fail at that point. If not, investigate that first.
Prove it again

If everything looks correct at first glance, go back and look closer. A single character can make all the difference, but novices have a tendency to see what they want to see. The best technique to support double checking is character-by-character, line-by-line comparison.

Go ahead and put your finger on the screen. Don’t be embarrassed — after almost twenty years, I still do it — it’s necessary to help your eyes identify minute differences. For each character, ask “why is this here?”. Pay close attention to the display of each character. Common offenders include so-called smart quotes, and whitespace generated by non-printing ASCII characters.

Read the first error message returned, google it, and learn what it means. Don’t skip to the second or third error message just because it contains a word you recognize and the first one doesn’t.
Unequivocal means ‘prove it in isolation’

Back in high school, my ’78 Malibu had trouble starting. The battery would die if the car sat for as little as one day. I measured the current with the engine running and found it on the low side. Obviously, the battery wasn’t getting charged, so I replaced the alternator. A few days and eighty bucks later, the battery died again. So frustrating!

The running current now tested fine, so I went on to test the current with the car shut off. Lo and behold, it showed a current drain even with the ignition and accessories off. Come to find out the switch controlling the interior passenger door light had shorted, so the light stayed on constantly… even when the door was shut, where I couldn’t see the light.

Bugs in complex systems can have complex causes. Don’t allow your excitement at discovering an important fact to mislead you into assuming it is the root cause of the problem. Instead, devise a test that will prove it (sound familiar?) before investing time and effort.
Efficiency means prioritize

Given infinite time, you’ll always find the missing piece of knowledge that solves your mysterious bug. We want pretty much the opposite of infinite time though. Efficiency requires you to prioritize activities which have a higher likelihood of producing results.
Follow Best Practices

It sounds facetious, but the most efficient way to solve bugs is to not create them in the first place. Following software engineering best practices results in more understandable systems, which are therefore easier to debug.

Develop a strong, ethical commitment to good code. When you’ve identified the cause of a bug, always replace the problem with a solution that improves the quality of your code. Implementing a low quality solution is like cleaning using dirty equipment: you’re just moving the problem around.
Reproducibility

A bug is reproducible if you can re-produce it, or make it happen on demand. If you have a bug you can’t reproduce, don’t spend any time in code, but instead focus on collecting more information on how to reproduce it. You might need to go so far as to watch a screen share — users are notoriously bad at telling you what subtle thing they’re doing differently than you expect.
Simplest first

Once reproducible, always always always start by checking the simplest things. Think about how sad you’ll be if you spend hours pursuing some far-out theory, only to find a variable name was misspelled, or the server needed restarting, or some other quickly solved issue. Remember KISS (regardless of how awesome they were, I mean the acronym “Keep It Simple Stupid”, not the band).
Intermittents

If a bug happens some, but not all of the time, it’s called an intermittent. A computer is a deterministic device, meaning every bug must have a determinable cause, but finding the conditions which lead to an intermittent can consume breathtaking amounts of time. You’ll need to practice triage to decide how much time to spend.

Quickly assess how frequently the intermittent occurs: attempt to reproduce the bug, counting the ratio between positive and negative results. Repeat the test as few times as needed to gain a high statistical confidence in the frequency. If you find the bug occurs 4 out of 5 times, you can have reasonably high confidence the bug will continue to occur upwards of 50% of the time over a larger number of tests. But if you get a positive result 2 out of 5 times, you really need to test 5 more times, as the true rate could range from 20% (2 out of 10) to as much as 70% (7 out of 10).

One you have reasonable confidence in the frequency, perform a risk assessment: multiply how often the bug occurs by its severity, and weigh that factor against the time cost of investigating. For example, something that happens 15% of the time but only results in a cosmetic error doesn’t deserve spending as much time as something that happens at a 0.5% rate but results in a security breach or data corruption.
Check your self

Bugs are tiny little mysteries, and a lot of people feel they can not rest while a mystery remains unsolved. However, a lack of rest makes one tired, and performing any kind of task while tired increases the risk of making a mistake.

Any activity will tire you to some degree, but debugging also has the potential to increase frustration in a way that other activities can’t. A bug’s defiant refusal to obey (your version of ) rules and logic can take on an almost insulting quality.

Frustration can sneak up and overwhelm you while all your attention is devoted to debugging. Take your mental temperature frequently. Ask yourself how you’re feeling. It seems paradoxical, but in order to remain efficient on longer problems you have to step away when needed.

Take a break and do something unrelated and physical. Go for a walk, wash the dishes, whatever. The physical element is critical: if you lay on the couch and watch TV your mind will stay stuck in its rut. You might still think about the bug while washing dishes but there is something special about physical movement that enables your mind to free itself. You’ll be astounded how often you come back to the problem after a break and see the cause immediately.
Write everything down and (maybe) ask for help

Sometimes the most efficient way to solve a bug is to get someone else to solve it. Sometimes. The more knowledge another programmer has, the more likely they are to be busy using that knowledge to their own benefit. Even if you post on a super awesome site like Stack Overflow, the answers that come back quickly have a much higher chance of being incorrect. And an incorrect answer can be disastrous to efficiency, let alone effectiveness.

If you’re just utterly stumped, write down everything you know about the bug. Everything: environment and conditions that cause it, when it started, a detailed description of the bug itself, everything you can possibly think of. Don’t edit or format, just let it pour out in a stream of consciousness.

There’s a marvelous phenomenon called Rubber Ducky Debugging. First printed in the book The Pragmatic Programmer, the story goes that a programmer kept a rubber duck on his desk, and when confronted with a problem, he would ‘explain’ it to the toy, realizing the cause during the process. While most certainly apocryphal, it does describe an experience that every programmer has at some point (my theory about the origin: just like most people don’t know that Bert is evil, Ernie is actually a l33t hax0r).

Same thing happens when you write everything down: as you pour out all the details, one of them sizzles with crackling energy in your mind. Something about the mental process of describing the bug unlocks a connection you just couldn’t make consciously.

There’s a second benefit to writing it down: even if you don’t get the eureka moment, you have written great documentation! Take some time now to edit and clean it up before using it to ask for help (and if you’re not familiar with the ettiquette of asking for help, read up on that first too).
Thank you sir, may I have another?

Like any skill, debugging requires devotion to practice. You solved the big gnarly bug? Congratulations, now get started on the next one! Learn to see the never ending supply of bugs as A Good Thing. The opportunity to expand and refine your understanding never ends.

In that spirit, I will update this guide as needed. If I’ve missed something important, please let me know.
