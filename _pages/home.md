---
title: "OKComputer Language Reference"
permalink: /
toc: true
toc_label: "Contents"
toc_icon: "cogs"
---

OKComputer (abbreviated as "okc") is a programming language written for beginners. The author is a fan of Radiohead, and the name is a reference to Radiohead's album "OK Computer".

It encapsulates the bare minimum functionality a programming language needs to be useful. It's written with the intent to strike a balance between easy-to-understand syntax and introducing the novice to some of the paradigms of programming that are less intuitive.

It is based on Python 3.5 and borrows most of its syntax from there, with some minor additions. The intent of using Python as the base is this language is to be a kind of "training wheels" that makes it easy to learn the basics. Once the learner is comfortable with the basics, they can start using more advanced, "full" Python syntax right in in the okc interpreter.

## Installation

For now, this is only a fictional language that has not been implemented, so a distribution for installation does not exist.

## The Interpreter

okc (and its parent language Python) are what are called interpreted languages. This means to use them, you open up a Unix or Windows terminal on a machine with okc installed, enter the command `okc`, and you're now in the interpreter. The okc interpeter shows you it's awaiting a command by beginning a line with `>>>`.

The interpreter interprets the text you type into it and, if you've entered proper okc syntax, performs the actions you're telling it to do. Entering improper syntax returns errors.

## Storing Data

The most basic building block of programs is variables. Variables store data. In okc, they are created just by typing a word in the interpreter that is not a keyword and assigning some value to it with the equals sign:

```
>>> apple = 5
5
>>>
```

Here, we see the interpreter returns the value we just assigned to the variable. You can then recall the value of any variable just by entering its name on the interpreter:

```
>>> apple
5
>>>
```

If you enter the name of a variable that hasn't been defined yet, you'll get an error:

```
>>> pear
Error: 'pear' is not defined
>>>
```

__Fine details:__ Variable names must start with either an upper or lowercase letter, and after that can only contain letters and/or numbers. So _apple_ is a valid variable name, _apple1_ is too, but _1apple_ is not, nor is _apple!_.

### Numbers

The most basic data a variable can store is a number, as shown in the examples in [Storing Data](#storing-data).

Numbers can be either positive or negative (or zero), and can use a decimal point if wished.

### Strings

A string is a block of literal text. Strings are defined in okc by surrounding text with quotation marks (").

Strings can contain any character that can be displayed on a screen. This includes:

- The standard Latin alphabet, upper and lower case
- Numbers
- Punctuation
- Accented characters (é, Â, ü, etc.)
- Non-Latin characters, like Greek, Arabic, and Chinese
- Even emojis 😯 😄

Most characters can be simply enlcosed in quotes to be stored as a string variable:

```
>>> apple = "Je suis presé"
'Je suis presé'
>>> pear = "Comment ça va?"
'Comment ça va?'
>>> orange = "Here<>is!more#punc@tu&ation^"
'Here<>is!more#punc@tu&ation^'
>>>
```

Some characters need to be "escaped" in order to be interpreted as a string. Quotation marks, for example, since they are used to used to denote strings in code, need to be escaped, otherwise the interpreter will think you're just writing muptiple strings. This can result in some cryptic errors:

```
>>> apple = ""Did you really do that?" Margaret asked."
SyntaxError: Unknown operator 'Did'
>>>
```

What is happening here is an empty string is being defined (""), which is being followed by the text "Did you really do that?" _as code rather than as a string_. "Did" is not a keyword in okc, so it results in a syntax error.

To escape quotes, simply precede them with a backslash (\\):

```
>>> apple = "\"Did you really do that?\" Margaret asked."
'"Did you really do that?" Margaret asked.'
>>>
```

Now we can see the quotation marks within the string were properly interpreted, as they were displayed back to us.

Here is a list of common characters that need to be escaped when used in strings:

| Escape Sequence | Description                                        |
| :-------------: | -------------------------------------------------- |
| `"\""`          | Double quotation mark                              |
| `"\\"`          | The backslash itself                               |
| `"\n"`          | Newline, if you want a string to be multiple lines |
| `"\t"`          | Tab character                                      |
| `"\#"`          | Pound/hash symbol (used in writing scripts)        |

For those curious, here's an example of a multi-line string:

```
>>> "This string has\nmultiple lines"
'This string has
multiple lines'
>>>
```

### Booleans

Booleans are a sepecial type of data that can only contain one of two values: __True__ or __False__ (note the capitalization). It may not be immediately obvious why such a data type exists. You may ask "why not just use a number that's either 0 or not zero?" and you are correct in that a number can accomplish the same task. The boolean type is useful on a mostly conceptual level. Computers operate on what is called _binary logic_: decisions are made on if things are true or false. Thus it is useful to have a datatype that can store this simple true/false information.

The usefulness of this is shown in more detail in the [Control Structures](#make-the-computer-think-for-you-with-control-structures) section.

### Updating Variables

Once a variable is defined, it can be reassigned a new value an unlimited number of times, and the original type doesn't even need to be used again:

```
>>> apple = 5
5
>>> apple = "Macintosh"
'Macintosh
>>>
```

## Lists

Say you want to store several related values together in a single variable. This is achieved with __lists__.

### Defining Lists

Lists are defined by enclosing multiple values in square brackets ("[ ]"):

```
>>> apples = ["Red Delicious","Macintosh","Granny Smith"]
['Red Delicious', 'Macintosh', 'Granny Smith']
>>> ages = [2, 3, 12, 49]
[2, 3, 12, 49]
>>>
```

Lists are extremely versatile. A single list can contain contain multiple data types. Here you can see a single list containing all three of the data types described:

```
>>> a_list = ["Macintosh", 3.45654, -234, True]
['Macintosh', 3.45654, -234, True]
>>>
```

Existing variables can also be used to store values in a list:

```
>>> apple = "Macintosh"
'Macintosh'
>>> a_list = [apple, 3.45654, -234, True]
['Macintosh', 3.45654, -234, True]
>>>
```

### Accessing Lists

Now that you've got a list defined, you're probably going to need to access the elements of the list individually at some point. This is done by using the same square brackets in a different way. Take a look at the example below:

```
>>> a_list = ["Macintosh", 3.45654, 234, True]
['Macintosh', 3.45654, -234, True]
>>> a_list[0]
'Macintosh'
>>> a_list[1]
3.45654
```

Note how the brackets are appended to the end of the list's name with a number between them. That number is called the __index__. Also note that the first element in the list is accessed with index 0. This is standard practices across almost all programming languages; lists are "zero-based", their index starts at 0.

#### Variable Index

In the same way that existing variables can be used in list definition, a variable can be used as the index when accessing list elements:

```
>>> a_list = ["Macintosh", 3.45654, 234, True]
['Macintosh', 3.45654, -234, True]
>>> idx = 1
1
>>> a_list[idx]
3.45654
>>>
```

#### Range

Lists have finite length; this length gets defined when the list is defined. In the example above, `a_list` has length 4, because it has 4 elements. The length of lists can be accessed in okc with the `lengthOf()` function\*:

```
>>> a_list = ["Macintosh", 3.45654, 234, True]
['Macintosh', 3.45654, -234, True]
>>> lengthOf(a_list)
4
>>>
```

\*_Functions are introduced [later in this manual](#make-the-computer-think-for-you-with-control-structures)_

If you try to access a list element with an index beyond the elements the list actually contains, an error is returned:

```
>>> a_list = ["Macintosh", 3.45654, 234, True]
['Macintosh', 3.45654, -234, True]
>>> a_list[6]
IndexError: list index out of range
>>>
```

Note that because lists are zero-based, the final element of a list has index _lengthOf(list)-1_. Using lengthOf(list) directly as the index when accessing a list will return the same IndexError specified above:

```
>>> a_list = ["Macintosh", 3.45654, 234, True]
['Macintosh', 3.45654, -234, True]
>>> a_list[lengthOf(a_list)]
IndexError: list index out of range
>>>
```

Because of this, careful attention must be paid when using variables as list indicies. There are ways to guard against this using [comparison operators](#comparison-operators) and [control structures](#make-the-computer-think-for-you-with-control-structures), discussed later in the manual.

## Input & Output

okc gets input from the interpreter with the key word pair "ask me". After you hit return after entering "ask me" on the interpreter, it will start a new line and wait for you to hit return again to signal the end of your input.

```
>>> answer = ask me
This is some text [return]
This is some text
>>> answer
This is some text
>>>
```

Notice it sent back the input we gave it because we were assigning a value to answer.

You can include a value after "ask me" that the interpreter will prompt the user with before getting their input:

```
>>> answer = ask me "How old are you? "
How old are you? 23 [return]                 # 23 has now been stored in answer
23
>>> answer
23
>>>
```

You can also explicitly instruct the interpreter to display the value of a variable using the keyword pair "tell me":

```
>>> hello = "Hello World"
'Hello World'
>>> tell me hello
'Hello World'
>>>
```

When using the interpreter directly, this is redundant as just typing in a variable's name then hitting enter will also return its value. The `tell me` keywords are useful when creating [functions](#stop-repeating-yourself-with-functions).

## Operations

So we know how to store and manipulate data. Now lets do stuff with data.

### Arrithmetic

okc includes the basic operations one would find on a standard calculator:

| Symbol | Operation |
| ------ | --------- |
| \+ | Addition |
| \- | Subtraction |
| \* | Multiplication |
| / | Division |
| ** | Exponent |
| sqrt() | Square root (note this is actually a function) |

If you've ever used a scientific calculator where you type out the entire expression you want to solve and then hit the "=" button to solve it, the okc interpreter works in the same way, just think of the return button as the equals button:

```
>>> 5 + 10
15
>>>
```

Parenthesis can be used just like in standard algebra, and standard order of operations is obeyed.

Standard order of operations, listed from which is executed first to last:

1. Parenthesis-enclosed expressions. Parenthesis can be nested ( 5 * ((2 + 8) * (6 - 2) - 1) ); the innermost parenthesis are evaluated first. All function calls within expressions are considered parenthetical expressions, e.g. sqrt() falls into this category.
1. Exponential expressions.
1. Multiplication and Division (left to right).
1. Addition and Subtraction (left to right).

In the same way that variables can be used as the index to access the elements of a list, variables containing numbers can be used directly in arrithmetic:

```
>>> x = 5
5
>>> y = 10
10
>>> y/x
2
>>>
```

Variables can also directly be assigned the result of an expression:

```
>>> x = 2 ** 4
16
>>> x
16
>>>
```

#### Strings as Numbers

For convenience, if a string contains only numbers, it can be used in an arrithmetic operation with number variables and it'll be treated just like a number varialbe:

```
>>> x = "54"
'54'
>>> y = 9
9
>>> x/y
6
>>>
```

If you attempt to use a string that does not contain only numbers in an arrithmetic operation, an error occurs:

```
>>> x = "fish"
'fish'
>>> x/5
TypeError: unsupported operand type(s) for /: 'str' and 'int'
>>>
```

### String Concatenation

There is one operator that does work with non-numeric strings: the "\+" operator. For strings, this is called the "concatenation" operator; it will join multiple strings together into a single string:

```
>>> a = "This "
'This '
>>> b = "is a "
'is a '
>>> c = "string concatenation"
'string concatenation.'
>>> d = a + b + c + "."
'This is a string concatenation.'
>>>
```

Notice how both string variables and string literals can be joined together within the same expression.

## Make The Computer Think For You with Control Structures

We will now get into the part of programming that actually makes programs useful: __control structures__. This is code that makes the computer do different things based on the values of variables while the program is running.

### "if" blocks

The most basic control structure is a so-called `if` or `if ... else` block, called so because this is literally what it looks like:

```
>>> condition = True
>>> variable = 1
>>> if condition is True:
...   variable = 5
... else:
...   variable = 0
...
5
>>> variable
5
>>>
```

The `else` statement doesn't have to be used:

```
>>> condition = False
>>> variable = 1
>>> if condition is True:
...   variable = 5
...
>>> variable
1
>>>
```

This is where boolean variables become useful: the condition following the `if` statement must evaluate to the boolean True or False values. It is possible to derive boolean values from non-boolean variables (discussed below in [Comparison Operators](#comparison-operators)), but first a couple major concepts must be addressed:

#### Logical Blocks

Notice the indentation on the lines following the "if" and "else" lines. This is how okc represents one of the core concepts of programming languages: __logical blocks__. Logical blocks are blocks of code "nested" within another block of code that get executed based on the result of a condition evaluatiion (i.e. "if condition is True:").

The "outermost" logical block is when the cursor is all the way to the left on the interpreter. A new block is indented two spaces in from its parent block. Logical blocks can be nested infinitely in theory:

```
>>> if condition1 is True:
...   if condition2 is True:
...     if condition3 is True:
...       if condition4 is True:
```

The number of spaces used when indenting blocks __does matter__. The interpreter will throw an error if an unexpected or incorrect indentation is used:

```
>>> if condition is True:
... x = 5
IndentationError: expected an indented block
>>>
```

```
>>> if condition is True:
...   x = 5
...     y = 10
IndentationError: unexpected indent
```

#### What is this "..." ?

You'll notice something new from the interpreter in the examples above: the lines beginning with "...".

When a statement is entered into the interpreter that expects a new logical block to follow (like an `if` statement), after hitting enter, instead of executing the statement, the interpreter will move to a new line starting with "..." and wait for input. This is the interpreter's way of saying "Hey, the code isn't finished yet!".

Note that hitting enter after typing a line inside a logical block _still_ will not make the interpreter start executing - notice there's a blank line staring with "..." in the two completed `if` statement examples above before the result is displayed. While inside a logical block, the interpreter allows you to keep writing statements. You finally tell it to close the block by hitting enter twice.

### Comparison Operators

As noted above, `if` statements must be followed by an expression that evaluates to the boolean True or False values. The way to do this with non-boolean values is with __comparison operators__ - operators that compare two values and return True or False.

The operators supported by okc are:

| Symbol | Operation |
| ------ | --------- |
| equals, is, == | Equal to (all three are valid syntax) |
| \> | Greater than |
| \< | Less than |
| \>= | Greater than or equal to |
| \<= | Less than or equal to |

Just like arrithmetic operations, variables can be assigned the results of comparisons:

```
>>> x = 5
5
>>> y = 10
10
>>> z = x > y
False
>>> z
False
>>>
```

Note, though, that booleans can only be compared to booleans, and non-booleans to non-booleans. Trying to mix the two will produce an error:

```
>>> x = 5
5
>>> y = True
True
>>> x > True
TypeError: unsupported operand type(s) for >: 'int' and 'bool'
>>>
```

Note also that booleans can only be compared using the equals operators, as there's no logical way for "True" to be greater or less than "False".

#### String Comparisons

Strings are partially supported by the comparison operators. Like with arrithmetic operators, if a string containing only numbers is comapred with a number variable, the string will get converted to the numeric value it represents.

When strictly comparing strings to strings, only the equals operator is supported:

```
>>> "apple" == "apple"
True
>>>
```

Trying to use greater than or less than with strings will result in an error.

## Stop Repeating Yourself with Functions

So you know a bit about what you can do with data. How is this more useful than a calculator though? Here's how: functions.

Remember functions from way back in algebra class? They looked like _f(x) = x/2_ or _g(x) = x + 3_, and thus _f(10)_ = 5 and _g(10)_ = 13.

Functions in the world of code are the same idea: a recorded set of instructions you can call on any time you want, that will do the same thing every time.

### Anatomy of a Function

Here is an example function definition:

```
>>> define function add(a, b) as:
...   return a + b
...
>>>
```

The key parts of the syntax here are:

- The keywords denoting a function definition: _define function_
- The function's name: _add_
- The function's arguments _(a, b)_
- The keyword _as_ followed by colon
- The keyword _return_ inside the function body

Functions are another part of okc that use logical blocks. Just like with `if` statements, once inside a function definition, you can write as many lines of code as you wish before exiting the definition by hitting enter twice.

### The return statement

Any statements that can be written on the interpreter can be written inside a function's body, with the addition of the _return_ statement. This is how functions return values back to the environment they were called from. For example, calling the `add` function defined above would look like this:

```
>>> add(1, 2)
3
>>>
```

If the return statement were not present in the function definition, no value would be returned.

### Making Functions Talk

When functions are called from the interpreter, they don't automatically show you what's going on as they're running. If you want a function to "talk back" to you as its working, you have to explicitly instruct it to do so with the "tell me" keyword pair:

```
>>> define function HelloWorld() as:
...   tell me "Hello, world!"
...
>>> HelloWorld()
Hello, world!
```

## Stop Forgetting Everything with Scripts

Everything this manual has explained so far has existed within the confines of the interpreter. When the interpreter is closed, any work you've done disappears.

The way to preserve work is to save your okc code to script files.

Script files are just simple text files with the extension ".okc". Any text editor can be used to write them.

To write a script, open up a new text file and start writing okc code as if you were in the interpreter. The only difference will be the code will not get executed on-the-fly. This means you, the programmer, have to check for syntax errors yourself, as the text editor will not point them out for you before you attempt to run the script. The interpreter will display any syntax errors in the script when you try to run it.

To invoke a script, simply start the okc interpreter in the folder you have the script in, then simply enter the script's filename. For example, let's say we're in a directory with a script called example.okc that just tells us "Hello, world!":

```
>>> example.okc
Hello, world!
>>>
```

### Comments

Code can be annotated without interrupting its syntax with comments. A comment is started with the pound/hash sign "#". Once the hash sign has been typed on a line, all text following it becomes a comment. For example:

```
# This is a comment that takes up an entire line
a = 2 # This is a comment that starts after some valid code
```

### Example script: Find area of triangle

```
# file: ta.okc
# -------------------------------------
tell me "Let's determine the area of a triangle."
a = ask me "Length of first side? "
b = ask me "Length of second side? "
c = ask me "Length of third side? "
tell me "Area is: " TriangleArea(a, b, c)

define function TriangleArea(a, b, c) as:
  # calculate the semi-perimeter
  s = (a + b + c) / 2

  # calculate the area
  area = sqrt( ( s * (s-a) * (s-b) * (s-c) ) )
  return area
```

This would be invoked by:

```
>>> ta.okc
Let's determine the area of a triangle.
Length of first side? 3 [return]
Length of second side? 4 [return]
Length of third side? 5 [return]
Area is: 6
>>>
```

## Copyright

All parts of okc that are unmodified versions of the Python synatax are copyright © 2001-2018 Python Software Foundation; All Rights Reserved.

All original text copyright © 2018 Ben Faucher.