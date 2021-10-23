# Scrap Shell Docs
Scrap Shell is a very simplistic shell like language used by the ScrapMechanic mod [ScrapComputer](https://steamcommunity.com/sharedfiles/filedetails/?id=2634124102).  
The ScrapShell interpreter written in Lua can be found [here](https://github.com/RedCubeDev-ByteSpace/ScrapShellLua), and there is a [VScode Extension](https://marketplace.visualstudio.com/items?itemName=RedCubeDev.scrap-shell-language-support) for highlighting available.
This Website will cover the Scrap Shell scripting language.

### Table Of Contents
- [Note](#note)
- [Input-Output](#input-output)
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

# Expressions and Operations
test2

# Goto
test2

# Subroutines
test2