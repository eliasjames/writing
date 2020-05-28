Software is made of tiny differences
Apr 22, 2020

Programming involves working with data. Computers process data natively, but humans process information, which is data arranged in an understandable format.

The more similarities two pieces of data have, the harder it can be for humans to see the differences. `diff` is a tool which shows the differences between two files, on a line by line basis.

There’s three ways a line can differ between two files. It can be present in the first file and not the second; the opposite, present in the second but not the first; or present in both but slightly different.
Example

The squishy word in that description is “present”. How does it get decided whether or not two different lines are matching? Imagine two files:

a b c d e     r t x f rf g h i j     a b c d ek l m n o     k l o m np q r s t     p q r s t

- “a b c d e” is a full match in content, but not in position.

- “k l o m n” is a partial match; same line position, slightly different content.

- “p q r s t” is a full match, both in content and line position.

- “r t x f r” and “f g h i j” both have no match.

We need our tool to identify all these cases.
The Process

Enter the least danceable rhythm, the algorithm. Like algebra, the word algorithm comes from the name of an ancient Persian mathematician, al-Khwarizmi. Unlike algebra, everyone understands what an algorithm is: it’s a recipe or process for producing data. Long division is an algorithm — find the largest multiple of the divisor, subtract it, then repeat until the remainder is less than the divisor. Balancing a checking account is an algorithm (I said everyone understands what it is, not that it’s easy!).

In this case, the best suited algorithm is called the “longest common subsequence”. You can look up the details if you like, but the important part is that the algorithm needs to look for that subsequence anywhere in the second file, potentially even on an earlier line number. In our example, it needs to recognize “a b c d e” is a match even though it appears on different line numbers.

`diff` takes two file names as arguments. It compares the entire contents of the first file for the longest common subsequences for each line, and then repeats the process for the second file. Finally, it displays the results in a format which indicates where the matches were found.

Note that `diff` also operates on directories, but we’re going to focus only on files for now.
The Format

`diff` needs to present its results in a text-only format so that other command line tools can accept it, including STDOUT for display. The format consists of three basic elements. Let’s look at the output for our example:

$ diff this.txt that.txt0a1> r t x f r2,3c3< f g h i j< k l m n o— -> k l o m n

Any lines which match are not displayed. If all lines match, `diff` returns nothing.

For convenience, `diff` displays the content of the lines which were different. The angle bracket indicates which file the difference came from, corresponding to which argument the file name was passed as.

The first output element indicates the line numbers of the differences, and in what way they were different: ‘a’, ‘c’, or ‘d’, corresponding to Add, Change, and Delete. In the first group, diff recognizes the first line in ‘that.txt’ has no match in ‘this.txt’.

Numbers separated by a comma represent groups of lines. If `diff` finds a match which is spread out or mixed up across multiple lines, it reports the entire area as a difference. In this case, it recognizes the subsequence k+l+m+n in both files, it treats the line starting with ‘f’ as part of the same change.

Why did `diff` not report line ‘f’ as a deletion? Remember, diff is looking for the “longest possible subsequence”. `diff` can tell that the k+l+m+n line is similar, so it looks at its neighbors to see if they are also similar. It reports the line starting with ‘f’ as a change based on the comparison of the longest subsequence (using capitals to highlight):

“c d e F G H I J k l M/o N/m O/n p q r”
Using the format

`diff` is an indispensable tool when working with data files, including code. Getting comfortable with reading the format allows you to instantly see tiny discrepancies.

There is another use for the output of `diff` which doesn’t get used as much but helps to understand why it is the way it is. `diff` has a corresponding program, called `patch`. `patch` takes the output of a diff and applies the changes to one of the files. In other words, it reverses the diff; after a patch both files are identical.

`patch` used to be a very common task before automatic software updates, when users had to literally “patch” their own systems. It’s still useful today if you want to review and edit many changes before applying them all in one action.
Exercises

1. Perform the diff in the section “Example”

- create both text files using the text editor of your choice

- execute the diff command

- see something unexpected? Some programs like Word and Pages add their own formatting to the file. Try using Notepad or TextEdit.

2. Diff two HTTP sessions

- combine two previous lessons by piping the output of the `curl` command to a file

- Careful! Piping output can overwrite target files.

- `curl -v google.com &> first.txt`

- `curl -v google.com &> second.txt`

- `diff first.txt second.txt`

- what’s different between them?

- try again, but point `curl` at ‘www.google.com' instead
