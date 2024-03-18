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

















