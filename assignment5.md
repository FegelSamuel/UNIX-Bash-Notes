# This is not a cheat sheet
```C
// file: onepipe.cpp
// author: M. Amine Belkoura
// date: 03/04/2020
// purpose: CS3377
// description:
// this program executes "ls -ltr | grep 3376", by dividing the two command 
among the child and parent process
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
int main(int argc, char **argv){
int status;
int childpid;
char *cat_args[] = {"ls", "-ltr", NULL};
char *grep_args[] = {"grep", "3376", NULL};
// create one pipe to send the output of "ls" process to "grep" process
int pipes[2];
pipe(pipes);
// fork the first child (to execute cat)
if((childpid = fork()) == -1){
 perror("Error creating a child process");
 exit(1);
} 
if (childpid == 0) {
 // replace cat's stdout with write part of 1st pipe
 dup2(pipes[1], 1);
 // close all pipes (very important!); end we're using was safely copied
 close(pipes[0]);
 close(pipes[1]);
 execvp(*cat_args, cat_args);
 exit(0);
}
else {
 // replace grep's stdin with read end of 1st pipe
 dup2(pipes[0], 0);
 close(pipes[0]);
 close(pipes[1]);
 execvp(*grep_args, grep_args);
}
return(0);
 
}
```
Here is how to make two children from one parent
```C
pid_t child_a, child_b;

child_a = fork();

if (child_a == 0) {
    /* Child A code */
} else {
    child_b = fork();

    if (child_b == 0) {
        /* Child B code */
    } else {
        /* Parent Code */
    }
}
```
