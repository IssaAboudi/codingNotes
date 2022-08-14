# Input, Output and Text in C++

More often than not, you will want your program to display information to the
screen. Sometimes you will want the user to interact with your program.

Most programs will need some way of printing out information to the end user.
This can be as simple as spitting out the result to a calculation when the 
program is run, or it can be as complicated as a text adventure game, with
multiple responses and options to choose from.

In any case, you will need to understand how to use `cout`.

---

### What is cout?

[Cout](https://www.cplusplus.com/reference/iostream/cout/?kw=cout) 
(or **c**haracter **out**put) is a `stream object`. It deals with "streams" 
of data. You'll often see it accompanied with **streaming operators** (`<<`). 
The way you use the `cout` object is by "streaming" variables and/or raw values
to it, like so:

```c++
std::cout << "I am text";
```

The output looks something like:

```
I am text
```

The best way to think about `cout` is to think of it as a location. By using
the streaming operator (<<), we send the raw text "I am text" to cout. Where exactly
is cout?

![Terminal](https://i.imgur.com/zTKcxiu.png)

The top part of this code contains the code seen above. On the bottom is the 
console, where the output is shown. We can treat `cout` as a stand in for 
the console.

_NOTE: You can use `cout` with any variable to view the value held by that variable,
making it a very useful way to **debug** your code._

---

## Literals

In the above example, we sent the text "I am text" to the console. This is an
example of passing a string literal to the console with cout.

**Literals** are hardcoded values (words, characters or numbers) displayed to
the console or assigned to variables using the `assignment operator (=)`. You
will most likely use a lot of literals unless taking in user input.

_Literals can be thought of as the opposite to variables. Variables can be changed
and often store values that may be unknown to the programmer, but literals are
specifically set by the programmer and virtually never changed._

---

## New Line

In the vast majority of cases when printing text to the screen, there is a need
to separate characters, text, or numbers onto their own lines. There are two ways
to approach this:

### 1) `'\n'`
The newline character can be appended to the end of string literals to
put following text on a new line:
```c++
std::cout << "Hello \nMy Name is \nIssa\n";
```
Will result in:
```
Hello 
My Name is
Issa

```

_An easy way to think about the `\n` character is to think of it as your `enter`
or `return` key on your keyboard. When you press that key, in most text applications
it tells the computer that it has reached the end of the line and to start a
new line. Hence the name "**newline** character"._


### 2) `std::endl`
`endl` essentially does what `\n` does, but also flushes the buffer. This
makes `endl` much less performant than simply `\n`. There isn't a visual
difference between using `endl` or `\n`
```c++
std::cout << "example text with endl" << std::endl;
//or
std::cout << "example text with newline character\n";
```
There isn't going to be a visual difference:
```
example text with endl
example text with newline character

```

**Flush the buffer?** 
Generally speaking when `cout`ing, there is no point in using `endl` over `\n`.
You'll want to flush the buffer when working with files because sometimes your
data does not make it to the file and is held in the buffer. We'll cover this
more later  <!-- when we talk about [files](./Files.md) -->.

_As we are starting off in C++, this difference isn't going to be particularly 
meaningful but it is still a good idea to have some idea of what is happening 
under the hood._

---

## Escape Characters

Now seems like an opportune time to mention escape characters. We briefly
discussed the `newline escape character (\n)` which is used to separate
sentences into separate lines in the console.

There are multiple other kinds of escape characters with different purposes.
[GeeksforGeeks](https://www.geeksforgeeks.org/) has a nice table that shows
some escape characters you could use in your programs:

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20191129164033/C-CPP-Escape-Sequences-768x947.png" width="500"/>

They are called escape characters because they "escape" the string that contains
them. For example if you want to display a `"`, you will run into problems with:
```c++
std::cout << "Let us print a double quote " "; //will not work
```

**I challenge you to try this code above in your IDE.** 

You should get some sort of syntax error. It should work when you escape
the double quote `"` by preceding it with a `\ `:


```c++
std::cout << "Let us print a double quote \" "; //should work
```

These escape characters are incredibly situational but allow us to make
our programs look and feel intuitive on the user's end, even if it makes our
code look weirder on our end.

---


## User Input

The vast majority of programs use user input of some kind (Mouse, Keyboard, 
Controller). Since we are starting out, our programs are mostly going to run 
in the **command line** so our user input will be from the keyboard. There are a
couple of different methods to access user input, all of which rely on `cin`

_NOTE: There are other methods for inputting data into a program, and we will
touch on another method later <!-- when we discuss  [files](./Files.md) -->._

### Introducing cin

[Cin](https://www.cplusplus.com/reference/iostream/cin/?kw=cin)
(or **c**haracter **in**put) is a `stream object`much like cout except 
it works the other way. While c**out** acts as a stand in for the console where 
you **out**put your data, c**in** stands in for your keyboard and lets you 
**in**put text into the program.

When you use `cin`, you will need some [variable](./Variables.md) to store the
data coming in from the user. Take a look at the following code:

```c++
int userInput = 0; //declare and initialize integer to store user input into
std::cout << "Please enter a number: "; //prompt for the user
std::cin >> userInput;
```
The very first thing we do is create a `int` variable which we'll use to store
the number inputted by the user. Next, we'll **prompt** the user to enter a
number. Finally, we will actually take in the input by using `cin` and the
`>>` streaming operator.

_Recall that when we used `cout` we used the `<<` streaming operator. The arrows
show where the data is coming from and where it is being streamed to._

### Problems with the cin buffer

A common problem people have with cin comes from not clearing the cin buffer.
Copy and paste the following code into your IDE:

```c++
#include <iostream>
int main(){
    int input = 0;
    std::cout << "Enter a number" << std::endl;
    std::cin >> input;
    
    std::cout << "Enter another number" << std::endl;
    std::cin >> input;
}
```

Most likely, you'll notice you can enter a number the first time but it skips
over for the second `cin` field. This is because there is still some extra data
in the cin buffer.

To overcome this, we can use the following two functions:`

- `cin.clear()`
- `cin.ignore(INT_MAX, '\n')` 

`cin.clear()` empties anything and everything left over in the buffer. 
`cin.ignore(INT_MAX, '\n')` ignores any character in the buffer until 
either it reaches the end of the buffer, or the `'\n'` character in the buffer.


```c++
#include <iostream>
#include <climits>
int main(){
    int input = 0;
    std::cout << "Enter a number" << std::endl;
    std::cin >> input;
    std::cin.clear();
    std::cin.ignore(INT_MAX,'\n');
    
    std::cout << "Enter another number" << std::endl;
    std::cin >> input;
    std::cin.clear();
    std::cin.ignore(INT_MAX,'\n');
}
```


I would **strongly** encourage always cin.clear() and cin.ignore() after you
take in user input using `cin`.

Go ahead and play around with `cin` and test taking in input for different data
types. Also experiment with clearing the buffer. What happens if you don't clear
the buffer when taking in strings? doubles? chars?

---
# [Go back to the home page](HomePage.md)
