```bash
g++ main.cpp
```
* g++ is the command to invoke your g++ compiler on whatever
* main.cpp is compiled into an object file named `a.out`.
* To run an object file, type `./a.out` into the terminal.

```bash
g++ -o textr *.cpp
```
* -o flag allows us to name the object file created after the flag, so we make an object file named `textr`
* `*.cpp` is a placeholder for all cpp files in the working directory
* To run the created executable, type `./textr`

```bash
g++ -o myProg -L/user/class/cs193/danLib -lDansDns *.o
```
* Make object file named `myProg`
* `-L`

# INCOMPLETE
