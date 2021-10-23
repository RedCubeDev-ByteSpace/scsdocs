# Scrap Shell Docs
Scrap Shell is a very simplistic shell like language used by the ScrapMechanic mod [ScrapComputer](https://steamcommunity.com/sharedfiles/filedetails/?id=2634124102).  
The ScrapShell interpreter written in Lua can be found [here](https://github.com/RedCubeDev-ByteSpace/ScrapShellLua), and there is a [VScode Extension](https://marketplace.visualstudio.com/items?itemName=RedCubeDev.scrap-shell-language-support) for highlighting available.
This Website will cover the Scrap Shell scripting language.

### Table Of Contents
- [Input-Output](#input-output)
    - [Writing to the Console](#writing-to-the-console)
    - [Clearing the Console](#clearing-the-console)
    - [Getting and Setting Cursor Position](#getting-and-setting-cursor-position)
    - [Getting Input from the Console](#getting-input-from-the-console)
- [Expressions and Operations](#expressions-and-operations)
- [Goto](#goto)
- [Subroutines](#subroutines)

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
test2

# Goto
test2

# Subroutines
test2