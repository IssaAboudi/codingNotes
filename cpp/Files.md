# Reading and Writing Files in C++

When we covered [Input and Output in C++](./InputOutput.md), we allowed
the user to enter data directly into the program. But what if we have a
database of information that we want to pull from? To simulate this, we
will open up a text file.

### talk about
- opening a file
- reading a file
  - `>>`, getline , read
- writing to a file
  - `<<`, write
- looping through a file
- fail, eof

## Getting started

The very first thing you'll need to do is `#include <fstream>`.
"fstream" stands for "**f**ile **stream**". (recall that we briefly
discussed "streams" in the section on [Input and Output](./InputOutput.md))


