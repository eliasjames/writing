Command-line Plumbing: Pipes and Streams
Apr 1, 2020

When your internet goes out, you quickly realize your computer isn’t very interesting when it isn’t moving data from one place to another. Same with the command line. The way to move data around on the command line is to “pipe” a “stream” from a source to a destination.

The pipe character is the plain, upright bar, usually on the upper right hand side of the keyboard, between backspace and enter. It looks like an ‘l’ or an ‘I’ without decorations: ‘|’. In \*nixes — any of the flavors in the Unix family — the pipe represents a connection between two streams. Streams of what? Data!
Pipes and Streams

We’ve already seen an instance of a stream. When we executed the ‘curl’ command, data was delivered to the screen via a pipe. Anywhere data goes in a \*nix system — output to the screen, saved to disk — it goes via a pipe.

Piping data between programs gets super useful. We can take the output of ‘curl’ and send it to another program. A program named ‘wc’ handles tasks related to “word count”. We can combine the two like so: `curl www.google.com | wc`. The output of ‘curl’ is “piped” to the input of ‘wc’, which outputs the number of lines, bytes, and words by default.

Although it’s called “word count”, what ‘wc’ really does is count various types of data in a stream: words, characters, bytes. So if we want to count characters, we can pass an option to it, like so: `curl www.google.com | wc -m`.

As we learned before, you can use the ‘man’ command to find out more about the options ‘wc’ supports, by running `man wc` (to exit ‘man’, type ‘q’ to quit).
Exercise

Start by opening a terminal. On Mac or Linux you have one built in; on Windows I highly recommend (Git Bash) [https://gitforwindows.org/].

Pipe some stuff around:

— `ls | wc`
— `ls -la | wc`
— `curl www.google.com | wc`
— `curl www.google.com | wc -m`
— `man wc | wc`
