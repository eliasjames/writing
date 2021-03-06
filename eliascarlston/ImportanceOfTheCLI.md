The importance of the Command Line Interface
Mar 7, 2018

I have taught programming to the entire range of developer experience, from complete novices to experienced engineers. Both groups have a harder time learning javascript-stack development if they do not develop fluency with the command line interface (abbreviated CLI, also called the terminal).

I use the word fluency intentionally, just like language. If you can’t “speak” CLI, you’ll struggle with many of the tasks js-stack development requires. Once you establish CLI fluency, you can switch to one or more graphical user interface (GUI) based tools, but you need to establish fluency first.

Even the switch to GUI tools illustrates why CLI fluency is so important. You may need three or four different programs to cover the common tasks that the CLI handles. Picture those three programs, with an average of, say, five menus, and fifteen commands per menu. That’s 225 different places to look to find the action you need. Worse, once you learn where to find the action, the tool gets rearranged in the next version and you have to re-learn it. And I didn’t even mention the time cost of installing and supporting those tools.

More fundamentally, GUI tools are a layer on top of the CLI. Whenever you add a layer, you also add the potential for gaps between them. Every experienced programmer has had a situation where some layer fails to accurately capture its underneath.

It’s not the fault of any specific tool, fixable by switching to another, but instead a fixed cost that comes from introducing extra complexity. GUI tools simplify visually, but have to connect to the same API the CLI does. The complexity comes from that connection.

To resolve a discrepancy between any GUI tool and the CLI, you have no choice but to look at the CLI. This holds true for nothing more strongly than version control application Git. If you are not comfortable with the Git CLI, then you will struggle with any GUI tools.

That’s worth restating more strongly. If you do not understand the Git CLI, then you don’t understand Git.

I see users of Git GUIs performing cargo cult rituals, like fetching before pulling, in the hopes (wishes, prayers) that will solve some entirely unrelated problem. Common and easily solved issues like merge conflicts or uncommitted work become major, painful obstacles. If you don’t understand Git at the CLI level, your actions in the GUI are just guesses.

So you have to understand the CLI before using a GUI, and some tasks will require you to leave the GUI and go back to the CLI. Switching back and forth between the two approaches has a cost: you spend mental energy. Costs associated with everyday tasks like these add up fast.

Finally, front-end development is web development, and the web has a strong bias towards Linux. The structure of URLs reflects this: they use the forward slash character because it corresponds to the Linux directory separator (as opposed to Windows’ backslash). Even if you develop completely in a stack like .NET or IBM Java, you’ll have to deal with that Linux bias once you start working with the frameworks and libraries that front-end now requires. Having CLI fluency within Windows through a tool like Git BASH or PowerShell makes a huge difference.

Hopefully I’ve convinced you of the importance of CLI fluency. Like a spoken language, nothing except practice produces fluency. In the next post, I’ll show you some tips for how to do just that.
