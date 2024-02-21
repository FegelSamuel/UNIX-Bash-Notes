# Command
```bash
ps
```
# Idea
* `ps` asks the Linux machine to display all the running *processes* on the machine owned by you
* The fields shown will be:
  * PID
    * Process Indentifier; It's just a number given to any running program on Linux
    * When you run `ps` at any time, the PID of `ps` (which will be shown) will be different every time
  * TTY
    * This is the terminal the given process is running on.
    * 
  * TIME
    * This is the timestamp
  * CMD
    * The name of the process, pretty much
  ```bash
  top
  ```
* The above command displays ALL processes in the machine including processes you don't own

