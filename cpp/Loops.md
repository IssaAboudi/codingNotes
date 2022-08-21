# Repeating Code with Loops

Loops are how we repeat blocks of code multiple times over and over, without manually typing them out every time. Take the following code:

```c++
  std::cout << "Hello" << std::endl;
```

If we want this code to print "Hello" five times, we could copy and paste those lines of code five times:

```c++
  std::cout << "Hello" << std::endl;
  std::cout << "Hello" << std::endl;
  std::cout << "Hello" << std::endl;
  std::cout << "Hello" << std::endl;
  std::cout << "Hello" << std::endl;
```

But this is incredibly messy and clutters up the code. Loops let us do this code in a much more elegant and clean way.

## "For" loops

"For" loops or "iterating" loops are loops that run code X amount of times. In our above example of printing "Hello" five times to the console, we can use a for loop:

```c++
  for(int i = 0; i < 5; i++){
    std::cout << "Hello" << std::endl;
  }
```

### Structure of a "for" Loop

In a "for" loop, there are three parts:

- `Counter Initialization` - We declare a counter for the loop to keep track of how many times we've looped.

- `Condition` - A condition sets how many times the loop will run

- `increment / decrement` - increase the counter

In my above code, I created a counter called `i` that starts at 0. Everytime the loop runs, `i` will be increased by 1. So after the first loop, `i` will be 1, and the second, 2... etc. The loop will loop until `i` is no longer less than 5 - when `i` = 5

The output of the code will be:
```
    Hello
    Hello
    Hello
    Hello
    Hello
```

## "While" loops

Another type of loop is a "while" loop. Unlike a for loop, which will loop a certain amount of times because of the `counter`, a "while" loop only has a condition.

While loops are useful when you are waiting for a change to happen, and you don't know how long it'll take until that change occurs. An example of this would be a desktop application/games, which generally keep running until you exit the program.

Lets make a while loop:

```c++
    bool flag = true;
    while(flag == true){
        std::cout << "I am looping" << std::endl;
    }
```

Running the above code gives us an output of:

```
    "I am looping"
    "I am looping"
    "I am looping"
    "I am looping"
    "I am looping"
    "I am looping"
    "I am looping"
    "I am looping"
    "I am looping"
    ...
```

Uh oh! We've accidentally created an **Infinite Loop**

### Infinite Loops

If a condition always evaluates to true, then the loop will never stop and the program won't end - in an IDE we can forcibly close that program by clicking the red stop button, but on your computer, you'll have to use something like "task manager" or power off the computer completely to end a program with an infinite loop

It's recommended to always have some sort of way to break the loop. Speaking of breaking the loop - There is a keyword called `break` that does what it sounds like. It breaks out of the loop that it's in.

```c++
    for(int i = 0; i < 5; i++){
        if( i == 2){
            break;
        }
        std::cout << i << std::endl;
    }
```

What do you think the output will look like? 

```
    0
    1
```

## Other loops:

There are a couple other types of loops in C++ that you should know about.

Firstly is the `Do While` loop. This is exactly like a while loop, except it runs code before it checks the condition. 

### Do While **Loops**
**Do While:**

```c++
    int x = 0; //counter

    do {
        std::cout << "We've run code" << std::endl;
        x++;
    } while(x < 5);
```

**While:**

```c++
    int x = 0; //counter

    while(x < 5){
        std::cout << "We've run code" << std::endl;
        x++;
    }
```

As you can see, this seems to output exactly the same:

```
    We've run code
    We've run code
    We've run code
    We've run code
    We've run code
```

It's really a matter of efficiency. Technically the do while is a bit more efficient in printing a message to the screen because it doesn't do that initial condition check until the end. This could be an advantage in menu systems where you need to show menu options for a user to select from before checking what they've selected.


### For Each loops

Another variation of the "for loops" is the "foreach loop". These are typically used with containers like arrays and vectors. (If you haven't learned about arrays, I highly recommend checking out my notes [here](./Arrays.md).) 

```c++
    int array[5] = {1,2,3,4,5};

    for(int element : arary){
        std::cout << element << std::endl;
    }
```

In the foreach loop, we make a copy of the element in the array. So for example for the first element array[0], we copy the value in there and create a variable "element" that has the value of array[0] - which is `1`. And it does that for each element in the array until we reach the end of the array.

This is slightly less efficient than accessing each element using a regular for loop because we are performing an extra copy instruction for each element. But the advantage of a foreach loop is in the ease to use.

----
# [Go back to the home page](../home.md)
