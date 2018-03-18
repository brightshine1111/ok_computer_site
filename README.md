# OKComputer Language Reference

## Introduction

(intent of language)

## The Interpreter

(will basically be the Python interpreter)

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

The most basic data a variable can store is a number, as shown in the examples in [Storing Data](#Storing-Data).

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

Most characters can be simply enlcosed in quotes to be stored in a variable:

```
>>> apple = "Je suis presé"
"Je suis presé"
>>> pear = "Comment ça va?"
"Comment ça va?"
>>> orange = "Here<>is!more#punc@tu&ation^"
"Here<>is!more#punc@tu&ation^"
>>>
```

Some characters need to be "escaped" in order to be interpreted as a string. Quotation marks, for example, since they are used to used to denote strings in code, need to be escaped, otherwise the interpreter will think you're just writing muptiple strings, which can result in some cryptic errors:

```
>>> apple = ""Did you really do that?" Margaret asked."
SyntaxError: Unknown operator 'Did'
>>>
```

What is happening here is an empty string is being defined (""), which is being followed by the text "Did you really do that?" _as code rather than as a string_. "Did" is not a keyword in okc, so it results in a syntax error.

To escape quotes, simply precede it with a backslash (\\):

```
>>> apple = "\"Did you really do that?\" Margaret asked."
'"Did you really do that?" Margaret asked.'
>>>
```

Now we can see the quotation marks within the string were properly interpreted, as they were displayed back to us.

Here is a list of common characters that need to be escaped when used in strings:

| Escape Sequence | Description                                        |
| --------------- | -------------------------------------------------- |
| "\\""           | Double quotation mark                              |
| "\\\\"          | The backslash itself                               |
| "\\n"           | Newline, if you want a string to be multiple lines |
| "\\t"           | Tab character                                      |

For those curious, here's an example of a multi-line string:

```
>>> "This string has\nmultiple lines"
'This string has
multiple lines'
>>>
```

__Advanced note:__ There are many more escape sequences supported by Python, and thus also by okc, but only the most useful to beginners are mentioned here. For those interested in more details, check out [Python's documetation on its Lexical Analysis](https://docs.python.org/3.5/reference/lexical_analysis.html).

### Boleans

Booleans are a sepecial type of data that can only contain one of two values: __true__ or __false__. It may not be immediately obvious why such a data type exists. You may ask "why not just use a number that's either 0 or not zero?" and you are correct in that a number can accomplish the same task. The boolean type is more useful on a conceptual level

### Lists

(About lists)

## Operations

### Arithmetic

All basic operations included:

- +
- -
- *
- /
- // (floor)
- % (remainder)
- ** (exponent)
- sqrt()

#### What about strings?

For your convenience, if a string contains only numbers, you can use it in an arrithmetic operation and it'll be treated just like a number varialbe.

```
example
```

(About string concatenation)

### Comparison

- equals, ==
- \>
- \<
- \>=
- \<=

### Advanced: Binary Operations

## Make The Computer Think For You with Control Structures

- if ... then:
- else:
- while ... do:

## Stop Repeating Yourself with Functions

So you know a bit about what you can do with data. How is this more useful than a calculator though? Here's how: functions.

Remember functions from way back in algebra class? They looked like _f(x) = x/2_ or _g(x) = x + 3_, and thus _f(10)_ = 5 and _g(10)_ = 13.

Functions in the world of code are the same idea: a recorded set of instructions you can call on any time you want, that will do the same thing every time.

### Input & Output

When functions are called from the interpreter, they don't automatically show you what's going on as they're running. If you want a function to "talk back" to you, you have to instruct it to do so.

OKC code can write back to the interpreter using the key word pair "tell me":

```
>>> define function HelloWorld() as:
...   tell me "Hello, world!"
>>> HelloWorld()
Hello, world!
```

OKC gets input from the interpreter with the key word pair "ask me". After you hit return after entering "ask me" on the interpreter, it will start a new line and wait for you to hit return again to signal the end of your input.

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

## Stop Forgetting Everything with Scripts

(About scripts)

### Structure

### Invocation

### Using Code From Outside Your Script

You can include other scripts in yours by using the "import" keyword in your script.

(Example of function written in one script, another script uses it and calls the function)

### Comments

(About comments, made with pound symbol)

## Example script: Find area of triangle

```
# file: ta.okc
# ----------------------------------------------------
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