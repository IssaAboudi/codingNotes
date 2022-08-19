# Loops, Files and Reading/Writing in C++

When we covered [Input and Output in C++](./InputOutput.md), we allowed the user to enter data directly into the program through the terminal. Sometimes rather than taking in input from the user directly, we can pull data from a file or database. 

## The importance of looping with files

I strongly encourage that you read about loops before continuing on with files. Looping - specifically with `while` loops are integral to reading files. I will briefly cover looping as it pertains to files, but for a more comprehensive explaination of how looping works, you should really checkout my notes on loops [here](./Loops.md)


## Why do we care about working with files?

When programs run, they run in a part of the computer called RAM (Random Access Memory). When we work with variables and perform calculations, those operations and variables are located in memory. When the computer is turned off, that memory is wiped and all data will be lost. Using files means that the data you're working with can persist between reboots.

Files are stored on the disk - hard drives/SSD (solid state drives). Read more about [hard drives](https://en.wikipedia.org/wiki/Hard_disk_drive) and [SSDs](https://en.wikipedia.org/wiki/Solid-state_drive).

### talk about
- opening a file
- reading a file
  - `>>`, getline , read
- writing to a file
  - `<<`, write
- looping through a file
- fail, eof


## Getting started

To begin, we will need some way to work with a file in C++.

The very first thing you'll need to do is `#include <fstream>`. "fstream" stands for "**f**ile**stream**". (recall that we briefly discussed "streams" in the section on [Input and Output](./InputOutput.md)). `fstream` will allow us to create variables that represent the files we want to interface with. Think of these variables as a stand-in for the actual file itself.

There are three types of file variables in `fstream`:

- `std::ifstream` or input filestream: This variable will allow you to input data from the file and load it into the program

- `std::ofstream` or output filestream: This will do the opposite, and write out data from the program to a file.

- `std::fstream` : Using this variable will allow you to both read from and write to files.

### So what do we do with our file variable?

As stated earlier, the file variable is a 