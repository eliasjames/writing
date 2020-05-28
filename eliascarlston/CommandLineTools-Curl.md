Command-line text tools: See URLs
Mar 26, 2020

#Text is King

One of the great things about web development — almost everything is text based. You don’t need a special program to view or edit information. Open source software development, \*nix, is built around a core of many small text tools. These tools share conventions; that is, they expect to be used in similar ways. Learning the conventions gives you a lot of power to use many tools.

Previously, we looked at how the whole Internet Protocol suite delivers content, but stopped before looking at the content. Today we’ll take that step using a program named `curl`. On Mac or Linux you have `curl` built in; on Windows I highly recommend Git Bash.
How to “See URLs”, and instructions, as text

HTTP is a text-based protocol. When resources get sent from the server to the client, they’re wrapped up in HTTP’s text format.

Normally, the browser calls the server to request a resource, and when the server responds, the browser handles it. We’re going to have to make the call ourselves if we want to look at the raw response.

`curl` (commonly pronounced like the word meaning ‘not straight’, but named as a pun: “see url”) will make the HTTP call for us. The command looks like this:

curl -v example.com

The first element is the program name, curl. Everything that comes after the program name are called arguments. All arguments change how the program executes, but there are some conventions around how they’re used.
Arguments, Options, Parameters

The elements that come directly after the command name are usually of a type called “options”. In our example, ‘-v’ is an option. By convention, options come in a pair of formats, short and long. The short version is a single dash followed by a single letter; the long is two dashes followed by one or more full words. The long version is almost always lowercase; the short version is case sensitive, meaning ‘-v’ is a completely different option than ‘-V’.

In `curl`, ‘-v’ shortens the long form ‘ — verbose’. Using this option means curl will output as much info as it can. As the name implies, options are always optional. When not specified, an option will default to some standard behavior. In the case of the ‘-v’, you could think of as the opposite of verbose, like “succinct” or “brief”.

Arguments which are not options are called parameters. Parameters (often referred to casually as ‘params’) are pieces of data the command will use. Parameters are different for every command, because each command needs different data.

Some options are common across commands, like ‘-a’ often means “show all”. There’s no explicit standard though, so never assume you know what an option does.

Instead, there’s a different text tool we can use to learn options: `man`, the command that displays manuals. Execute the command `man curl` to see the options for `curl`. Note that in this example, “curl” is now an argument, the name of the command we want to see the manual for. For any \*nix command, you can run `man` — try `man ls`, or even `man man` (to see the instructions for the ‘man’ command itself). To exit ‘man’, type ‘q’ for quit.
Real World Example & Exercises

Remember separation of concerns? Somewhere inside the browser, there’s code that does the same thing as curl: check DNS to get the IP address for the host, call the IP address and ask for the resource. However, the browser goes a step farther, and attempts to interpret and render what it gets back. `curl` stops, and outputs whatever it gets back as text.

Exercises:
— curl with and without the verbose option, long and short form
— curl a few of these sites:
— http://google.com
— http://www.google.com
— https://www.google.com
— https://duckduckgo.com/
— use the `man` command
— `man curl`
— `man ls`
— keep using `man` as we look at other tools
