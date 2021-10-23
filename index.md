# Scrap Shell Docs
Scrap Shell is a very simplistic shell like language used by the ScrapMechanic mod [ScrapComputer](https://steamcommunity.com/sharedfiles/filedetails/?id=2634124102).  
The ScrapShell interpreter written in Lua can be found [here](https://github.com/RedCubeDev-ByteSpace/ScrapShellLua), and there is a [VScode Extension](https://marketplace.visualstudio.com/items?itemName=RedCubeDev.scrap-shell-language-support) for highlighting available.
This Website will only cover the Scrap Shell scripting language.

### Table Of Contents
- [Input-Output](#input-output)
    - [Writing to the Console](#writing-to-the-console)
    - [Clearing the Console](#clearing-the-console)
    - [Getting and Setting Cursor Position](#getting-and-setting-cursor-position)
    - [Getting Input from the Console](#getting-input-from-the-console)
- [Expressions and Operations](#expressions-and-operations)
    - [Building more complex Expressions](#building-more-complex-expressions)
- [Variables](#variables)
- [Goto](#goto)
- [Subroutines](#subroutines)
- [If Statements](#if-statements)
    - [Else Clause](#else-clause)
- [Stop the Program](#stop-the-program)
- [Comments](#comments)

# Note
ScrapShell is a loosly typed language, meaning there are no datatypes.  
Adding a numeric value with a string will result in the string being converted into a number.  
Concatinating a string with a number will convert the number into a string.

# Input-Output
### Writing to the Console
ScrapShell has 2 functions for Outputting: `print` and `write`.  
The `print` function will output the given value to the screen and then add a line break to start a new line.  
```
print "Hello World!"
print 2.25
```

The `write` function will output the given value without beginning a new line.
```
write "Hello World!"
write 10
```

### Clearing the Console
To completely clear the computers Console you can use the `clear` function.
```
clear
```

### Getting and Setting the Cursor Position
To get the Cursors X and Y coordinates you can use the `cursorx` and `cursory` function.
```
write "Your Cursor is at: "
write [cursorx]
write ", "
write [cursory]
```

To set the Cursor coordinates you can use the `setcursor` function.
```
setcursor 10 10
```

### Getting Input from the Console
Getting input in ScrapShell is split up into multiple functions.  
One of them executing the input prompt, the other being for getting the value that was entered.

#### Line Input
This type of input is for getting a line of text from the User. The prompt will finish when the User presses the Enter key.  
For this kind of input we use the `input` function.
```
input
```

#### Key Input
This type of input is for getting a keypress from the User. The prompt will finish as soon as any key is pressed. The function will capture the keycode responding to the pressed key.
For this kind of input we use the `inputaction` function.
```
inputaction
```

#### Getting the Input Value
To actually get the value the User entered, we can use the `lastinput` function. It will return the value of the last input event.
```
input
print "You entered:"
print [lastinput]
```

# Expressions and Operations
In Scrap Shell everything is done using Shell Function, this also applies to expressions.  
For basic math you can use the functions `add`, `sub`, `mul`, and `div`.
```
add 1 2
sub 4 3
mul 5 5
div 4 2
```

To concatinate two string you can use the `con` function.
```
con "this is " "a string"
```

### Building more complex Expressions
This is where it gets a bit more interesting.  
You can feed the output of a function into the input of another using square brackets `[]`. This allows you to create more complex Expressions.
```
add 1 [mul 2 3]
; meaning: 1 + (2 * 3)

div [add 10 15] [mul 3 2]
; meaning: (10 + 15) / (3 * 2)
```

# Variables
In Scrap Shell, Variables can be set using the `set` keyword followed by an identifier, equal sign, and a value.
```
set somevar = 10
```

Instead of an identifier you can also pass in an expression allowing for procedurally created variables.
```
set [con "var" "name"] = "value"
```

To use the value stored in a Variable just use its name as the input.
```
set sometext = "this is a string"
print sometext
```

This of course also works when feeding functions into eachother.  
Heres a small program asking for a name and then telling the person hello as an example:
```
print "Whats your name?"

input                                ; letting the user type their name

set name = [lastinput]               ; getting what the user typed and storing it in a variable
print [con [con "Hello " name] "!"]  ; printing "Hello " + name + "!"
```

You can also get a Variables value by using the `get` function and passing in the variables name as an expression.
```
set somevar = "value"
print somevar          ; both of these will output the same thing.
print [get "somevar"]
```

# Goto
Goto is very important in Scrap Shell because its the base of all flow control Scrap Shell has.  
To use goto, declare a label by using `:` followed by your label name. You can now jump to that label.
```
:label

print "this is an infinite loop!"

goto label
```


# Subroutines
Subroutines are a kind of fancier version of Goto. They can jump to a label and then return to back where they came from.
To enter a subroutine you can use the `gotosub` function.
```
print "This will be run first."

gotosub someSub                    ; enter subroutine
print "This will be run last."

die                                ; forcefully stop the program so we dont accidentally run the subroutine again

:someSub
    print "This will be run second."
return
```

# If Statements
In Scrap Shell, If Statements are just conditional Gotos / Gotosubs.  
To create an If Statement, use the `if` keyword followed by an expression, an operator and a second expression.  
After that you need to supply a label or subroutine to jump to. For a normal goto do `:` followed by a label, for a subroutine do `>` followed by a label.  

Allowed operators for an If Statment are: `=`, `!=`, `<`, `>`, `>=`, and `<=`.  

Heres are some examples for If Statements:  
```
if 1 = 1 :somelabel         ; will goto to the given label if 1 = 1
if "a" != "b" >somesub       ; will run the given subroutine if "a" != "b"
```

### Else Clause
You can also add an Else Clause to your If Statement which will be run if the condition isnt true.  
To add an Else Clause just add an `else` keyword followed by a label or subroutine to the end of your If Statement.
```
if 1 > 2 :jumpHere
    else :jumpHereInstead

if 1 > 2 >runThisSub
    else >runThisSubInstead
```

# Stop the Program
To stop the current program you can use the `die` function.
```
die
```

# Comments
To comment in Scrap Shell you can use the `;` or `#` character.
```
; This is a comment!
# This is a comment as well!
```