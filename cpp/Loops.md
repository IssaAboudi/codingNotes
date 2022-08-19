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

But this is incredibly messy and "spaghetti" coding. Loops let us do this code in a much more elegant and clean way.

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

While loops are useful when you are waiting for a change to happen, and you don't know how long it'll take until that change occurs. An example of this would be a desktop application. Most desktop applications will keep running until you press the X button to close the program.

