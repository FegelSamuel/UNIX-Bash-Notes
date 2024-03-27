# Intro
Remember in C, you need a main to actually have a program **execute**.
```C
#include <stdio.h>
#include <unistd.h>

int main(void)
{
// We traverse the program line by line in order
  printf("This is statement 1.\n");
  printf("This is statement 2.\n");
  return(0);
}
```
## Output
```bash
This is statement 1.
This is statement 2.
```
# Fork()
```C
#include <stdio.h>
#include <unistd.h>

int main(void)
{
  printf("statement1\n");
  fork();
  print("statement2\n");
  return(0);
}
```
## Output
```bash
  statement1
  statement2
  statement2
```
* When I make a `fork()` call, I make another engine/process and the second process will execute the rest of my code
* Both are executing the same code and running at the same time
##
```C
  printf("s1\n"); // runs once
  fork();
  printf("s2\n"); // runs twice
  fork();
  printf("s3"\n"); // runs four times
```
## Output
```bash
  s1
  s2
  s2
  s3
  s3
  s3
  s3
```
## Explanation of fork()
* Normally, you program in a single process, but when `fork()` is reached:
  * A new process is created: `child`
      * Execute the rest of program
      * The new process has new memory it can access now (new process space assigned)
  * Old process stays alive: `Parent`
      * Execute rest of program
  * Parent/child get their own copies of variables initialized
  * Parents and children are parallel processes and not necessarily slower or faster than the other
* You should know who is executing what is not a good idea

# The point
* The idea of multiprocessing is that you get your task done faster (NOT NECESSARILY TWICE AS FAST BECAUSE INTERNAL ARCHITECTURE)
* You're still sharing your resources between multiple processes. Oftentimes
```C
#include <stdio.h>
#include <unistd.h>
int main(void) {
  pid_t childpid; // pid_t is basically int in C
  childpid = fork();  
  if(childpid == -1) { // fork might fail, which it will return -1
    perror("fork");
    exit(1);
  }
  if(childpid == 0) { // child entered to the stack
    /* Send "string" through the output side of pipe */
    printf("%d: This is the child process.\n", childpid);
    exit(0);
  }
  else { // parent process is some positive integer
    // read in string from pipe
    printf("%d: This is the child process.\n", childpid);
    exit(0);
  }
return (0);
}
```
# Pipes
* Initially, our processes are isolated
* Processes sometimes need to communicate with each other
  * Low level mechanism
  * `pipe()` call: create a pipe
  * Returns two descriptors
      * first for reading
      * second for writing
  * Think of pipes as a multivalue variable
* A special file/buffer that stores a limited amount of data in a FIFO manner
* Pipes are commonly used from within shells to connect the stdout of one utility to the stdin of another
```bash
ps -ef | grep "3376"
```
* See the `|` I used? `ps -ef` is its own process and `grep "3376"` is its own process
## Pipe synchronization
* If a process tries to write to a full pipe, it is blocked until the reader process consumes some data
* If a process tries to read from an empty pipe, it is blocked until the writer produces some data
## Types of Pipes
### Unnamed Pipes
* Used only with related processes
* Parent/child
* Child/child
* The pipe exists only as long as the processes using it are alive
### Named pipes
* Actually exist as directory entries (`ls` will show them)
* Have file access permissions (`chmod` required? hope not, can be done in the API)
* Can be used by unrelated processes
## READ/WRITE
* Data is written to and read from the pipe using the unbuffered system calls `write` and `read`

```C
#include <stdio.h>
#include <unistd.h>
int main(void)
{
   char    string[] = "Hello!\n";
   char    readbuffer[80];
   int fd[2];
   pipe(fd);
   write(fd[1], string, (strlen(string)+1));
   nbytes = read(fd[0], readbuffer,   sizeof(readbuffer));
   printf("Received string: %s", readbuffer);
}
```



