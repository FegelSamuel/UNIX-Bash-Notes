# Test
Let's say we make a file named `test`
```bash
# this is a basic shell script
who | wc -l
```
In the terminal, I will run
```bash
sh test
```
```bash
bash test
```
`who | wc -l` will run in the terminal
You can also run `chmod 100` on `test` to make it executable with `./` (1~~ can be any odd octal number) 

| Variable |          Meaning                                |
|----------|-------------------------------------------------|
|    $0    | Contains name of script            |
|$1,$2...$9|Contains first through ninth parameters of script|
|    $#    |   Contains amount of parameters       |
|$@| Contains all parameters of script |
|$?| Contains exit status of last command |
|$*| Contains all command line parameters |
|$$| Contains PID of executing process |

```bash
#  BOX
# Sample program to show the shell variables
echo                      # skip a line
echo "This script's name is $0 and here is its output: "
echo "Total number of command line arguments: $#"
echo "The first parameter is $1"
echo "The second parameter is $2"
echo "This is a list of all the parameters: $* "
echo
```

In the command line, I can type: `BOX IS EMPTY`
The output will be:
```txt
This script's name is BOX and here is its output:
Total number of command line arguments: 2
The first parameter is IS
The second parameter is EMPTY
This is a list of all the parameters: IS EMPTY 
```

```bash
# kb_read
# Sample program to show read command

echo                      # skip a line
echo "Enter your name:\c" # fake prompt
read name                 # actual prompt, stores keyboard input into label named "name"
echo "Your name is $name" # output
echo                      # skip a line
```

# If Statements
If you have done any scripting language before, this is not scary
```bash
if [ condition ]  # Just like a C++ if statement
then              # YOU NEED THE THEN AFTER YOUR IF
  true-commands
  ...
  last-true-command
else                 # just like a C++ else
  false-commands
  ...
  last-false-commands 
fi                    # if backwards to close out the if statement
```
```bash
if [ condition ]
then
  commands
  ...
  last_command
fi
```
```bash
if [ condition ]
then
  commands
  ...
  last_command
elif [ condition ]
then
  commands
  ...
  last_command
else
  else_command
fi
```
## Example
```bash
# svi3
# Save and invoke vi
# Sample program
DIR=$HOME/keep
if [ $# = 1 ] # I want only one argument passed in because a filepath contains one string
then
  cp $1 $DIR  # copy inputted file into the directory
  vi $1       # call vi on inputted file
else          # If I have more or less than 1, the user input the filepath wrong or didn't put an input
  echo "You need exclusively one argument to run this script! Number of arguments you passed: $#
  echo
fi
```
As a reminder, arguments are what's passed in when a function is called and parameters are defined in the funtion definition

# Numerical Boolean Operations
| Operator |  Example                                        |        Meaning           |
|----------|-------------------------------------------------|--------------------------|
|-eq|number1 -eqnumber2 | Are these two numbers equal? |
|-ne|number1 -nenumber2 | Are these two numbers not equal? |
|-gt|number1 -gtnumber2 | number1 > number2 | 
|-ge|number1 -genumber2 | number1 >= number2 |
|-lt|number1 -ltnumber2 | number1 < number2 |
|-le|number1 -lenumber2 | number2 <= number1 |

```bash
if [$1 -eq $2]
then
  echo
  echo "Your inputs are equal"
  echo
else
  echo
  echo "Your inputs are not equal"
  echo
fi
```

# String Operations
| Operator |  Example                                        |        Meaning           |
|----------|-------------------------------------------------|--------------------------|
|=|string1=string2|Check for equality|
|!=|string1!=string2|Does string1 **not** match string2?|
|-n|-n str|Does str contain a *nonzero* length of numbers|
|-z|-z str|Does str contain *zero* chars (is string empty)?|
Regarding strings, we need to use the `test` command
```bash
# Date Checker
DATE1= `date`
DATE2= `date`
if test "$DATE1" = "$DATE2"
then
  echo "STOP! The computer clock is dead!"
  echo
else
  echo "Everything is fine"
  echo
fi
```

