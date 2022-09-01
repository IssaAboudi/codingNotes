# Text, Numbers, and Variables in C++

There are several types of variables. 
Most of these variables exist across most coding languages
(Java, Python, C, C++, C# etc...) - If you learn them in one 
language they mostly translate to other languages.

---

## What are variables?

Variables are "containers", much like boxes in the real world hold items.
Except in this case, they contain values (numbers, text, etc) in programs.
Variables let the programmer keep track of certain values -
sometimes unknown values to the programmer, such as user input.

To **declare** a variable, you'll generally follow this format:
```
data_type name;
```
**Data types** tell the compiler what kind of variable you want to
declare. The **name** is how you reference the variable when you code.
You can name your variables whatever you would like. 

_Note: you are encouraged to name variables according to what they are used
for. If you make a variable to hold the user's name, a good name might be `name`. A more confusing name would be `x` or `var` since you cannot tell what they are on first glance_

---

## The different data types

Lets start with numbers

There are several different data types for numbers in C++ (and other languages).

### `int` or integers

Integers store whole numbers, both positive or negative. You declare them like:

```c++
int x; //declared an integer x;
```

 *Note I would strongly encourage initializing all variables when you declare them.
To initialize, simply assign it a starting value. See below:* 

```c++
int y = 0; //declared an integer y and initialized it to 0
```

By initializing, we ensure that we know exactly what x is when the program run
and we avoid any funky behavior such as the declared variable x having some value
other than what we expect it to have.

The last thing to mention about integers is that they can be signed (regular)
or `unsigned`. unsigned means that the compiler will throw you a warning if you
try to assign a negative value into the variable.

```c++
unsigned int z = 1; //declares and initializes an unsigned integer z to 1.
z = -1; 

```

If we attempt to print out z to the console, we will get a really large number:
4294967295. This is the largest number we can store in an unsigned integer before
it "overflows" - we will talk more about this later.


### `float`s and `double`s
Floats and doubles contain decimal values (both positive and negative). You declare
them very similarly to how you declare integers. My general rule of always initializing
your variables when you declare them comes into play here too:
```c++
float x = 2.5; //declare and initialize a float to the value 2.5;
double y = 2.5; //declare and initialize a double to the value 2.5;
```
The above two lines look identical. So why are there two? The answer comes down to
precision. A float is about half the size of a double, meaning that the float can't
store as large of numbers as a double can. To prove this to you, I will run the following:

```c++
#include <iostream>
#include <limits>
int main() {

    std::cout << "float max: "<< std::numeric_limits<float>::max() << std::endl;
    std::cout << "double max: " << std::numeric_limits<double>::max() << std::endl;

    std::cout << "Program Ending" << std::endl;
    return 0;
}
```

the output will look like:

```
float max: 3.40282e+38
double max: 1.79769e+308
Program Ending
```

In an academic environment, you might not care about or need that much precision
but if you were working at NASA, where they calculate with long decimal places
(think the first 20 decimals of pi!)
you'll want that extra precision.

### Text in C++

There are two variables that deal with text directly. The first one we'll talk
about is extremely useful and you will probably work with this very often.

`strings` are variables that contain words and sentences. You can declare a 
string variable just as you did integers, doubles and floats:

```c++
string name = "Issa"; //declared a string and initialized it to "Issa"
string sentence = "I am having a great day"; //strings can contain sentences
```

#### `char`s

Lastly, lets talk a little bit about "characters" or`char`s as they are known in
C++. `string`s and `char`s are really interesting and we will explore them in more
depth in the future.

As normal, we declare chars and initialize them just as any other variable:

```c++
char letter = 'a'; //declare and initialized a char to the lowercase letter "a"
```

There are a couple things to notice about the first line of code:
- Firstly, I used ' ' (single quotes) rather than " " (double quotes). This is
because `char`s only store single letters, whereas words/sentences (`strings`)
use " " (double quotes).
- I specifically said "to the lowercase letter a". Capitalization matters in
`char`s and by extension `string`s. We will talk more in depth about how the
computer interacts with characters.

I strongly encourage playing around with these different data types and getting
used to their differences. Try storing numbers in a `char` as a challenge!

---

# [Go back to the home page](../home.md)
