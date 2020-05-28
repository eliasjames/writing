Redirecting Standard Streams to Files
Apr 8, 2020

The art of programming requires “standing on the shoulders of giants.” We take for granted so much work that needed to come before to make the modern programming environment possible. Sometimes things that seems ridiculous or complex make much more sense once we understand the history of how they came to be.
Background

So far, with all the command line exercises, we’ve typed commands and the results output on the screen. In the beginning of programming, this was not a given. All programs had to explicitly make their own connection to the operating system in order to receive input and transmit output. You can imagine this was incredibly tiresome, error prone, and also prevented programs from being moved between operating systems.

Unix invented a concept called “standard streams”. In the last lesson, we played around with piping streams from one program to another. There were two streams we were using without being aware of it: ‘standard in’ and ‘standard out’, often referred to as STDIN/STDOUT (there’s a third one we’ll cover later).

When a process starts, it inherits standard streams from its parent process. If they haven’t been changed from the defaults, STDIN will come from your keyboard, and STDOUT will display data on the terminal screen. Not having to set up these common connections makes it super easy for us to get started with whatever job we want to do.
Streams and Files > Abstractions

Sometimes we want to do other things with data. The most common case is to save the results of an operation; we want to write STDOUT to a file. With complicated or repetitive input, we might want to store the input in a file and send it to the program instead of using the keyboard.

From the point of view of the operating system, standard streams are always files. In order to make the reading and writing process standard, the keyboard and the terminal are treated as if they were files (the specific terms are ‘file handle’ or ‘file descriptor’, depending on the context).

This is an example of abstraction. To abstract something is to separate what’s similar from what’s different. Abstraction has a cost — it increases conceptual difficulty. In this example, we now have to keep in mind the concept of files. But the cost is greatly offset by the savings in setup (above).

Pro tip: When used correctly, abstraction should always simplify more than it complicates. Unfortunately, some programmers really enjoy abstraction, and apply it everywhere regardless of cost/benefit. Always view abstraction skeptically, but embrace it when it genuinely provides value.
A Character Of Their Own

Because we’re dealing with file handles, standard streams get their own characters for piping. The angle brackets, ‘<’ and ‘>’, indicate which stream is being redirected (in or out). So reading a file as input into the “word count” program looks like so: `wc < file.txt`. And saving the result of a command to a file: `curl google.com > capture.txt`. Both together: `wc < input > output`.

Pro tip: the single right bracket overwrites the target file. To keep the existing file, and append the new content, use double brackets: `curl google.com >> multi-capture.txt`.
Murphy’s Law

In the ’70s, Unix started getting used for commercial purposes, including big industrial printing operations. A couple of those early print jobs got ruined: the gigantic machine started up, ran a bunch of paper through, but instead of news headlines or book pages, there was some garbled computerese. Expensive mistake — what happened?

The printing program failed to start, but having only one output, was forced to write its error message to the printer stream. Later versions of Unix introduced the third standard stream: STDERR, standard error. STDERR allows us to send error messages to a different place than ordinary output. This supports lots of neat uses, like writing log files, and keeping STDOUT clean.

To redirect STDERR, use this symbol: ‘2>’. Why 2? It’s the file descriptor. The file descriptor for STDOUT, 1, gets inserted by default when you use ‘>’ by itself. The append rules still apply for ‘>>’. All these settings can be mixed: `command 1> overwrite-output-file 2>> append-to-error-file`. To send STDERR to STDOUT, as if it was a file, use an ampersand followed by ‘1’ to indicate the file descriptor: `command > any-output-file 2> &1`.
Exercises

Start by opening a terminal. On Mac or Linux you have one built in; on Windows I highly recommend (Git Bash) [https://gitforwindows.org/].

Caution: sending output to a file changes data on your drive. To minimize risk of modifying an existing file, first create a new directory to work in: `mkdir exercises && cd !$` (we’ll explain that command in a future article!).

- Send output to a file: `ls > directory-contents.txt`
- Read input from a file: `cat < directory-contents.txt`
- Redirect output and error: `cat directory-contents.txt nonexistentfilename > output 2> errors`

`curl www.google.com | wc -m` will produce an error “wc: stdin: Illegal byte sequence”. Try assigning output and errors to separate files.
