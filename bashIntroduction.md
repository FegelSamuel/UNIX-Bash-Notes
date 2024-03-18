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
You can also run `chmod 100` on `test` to make it executable (1~~ can be any odd octal number) 

| Variable |          Meaning                                |
|----------|-------------------------------------------------|
|    $0    | Contains name of script            |
|$1,$2...$9|Contains first through ninth parameters of script|
|    $#    |   Contains amount of parameters       |
|$@| Contains all parameters of script |
|$?| Contains exit status of last command |
|$*| Contains all command line parameters |
|$$| Contains PID of executing process |
