# Example
```C
#include <stdio.h>
#include <sys/types.h>
#include <fcnt1.h>
#include <sys/file.h>

main() {
  int fd1, fd2, fd3;  // file descriptors
  fd1 = open("test.txt", O_RDWR | O_TRUNC); // O_RDWR is a file opening flag 
  printf("fd1 = %i\n", fd1);
  write(fd1, "what's", 6);

  fd2 = dup(fd1);
  printf("fd2 = %i\n", fd2);
  write(fd2, " up", 3);

  close(0);
  fd3 = dup(fd1);
  print("fd3 = %i\n", fd3);
  write(0, " doc", 4);

  dup2(3,2);
  write(2, "?\n", 2);
}
```

# execvp() syscall
## Header
`int execvp(const char* file, char * const argv[]);`
## Description
* Executes a file/command
* replaces the current process image with a new process image specified by executing a file
  * file: construct a pathname to executable file
  * argv: An array of char pointers to NULL-terminated strings. Constitute the argument list available to the new process image. The value in argv[0] must point to a filename that's associated with the process being started.
```C
// Includes removed for slide clarity
int main(int argc, char **argv) {
  int status;
  int childpid;

  char *cat_args[] = {"ls", "-ltr", NULL};       //
  char *grep_args[] = {"grep", "3377", NULL};    // 

  // create 1 pipe to send the output of ls process to grep process
  int pipes[2]
  pipe(pipes);

  // fork the first child to execute cat
  if ((childpid = fork()) == -1) { // I should mention that childpid = fork() runs here
    perror("Error creating a child process");
    exit(1);
}
if (childpid == 0) { // if we are in the child process
  // replace cat command's stdout with write part of 1st pipe
  dup2(pipes[1], 1);

  close(pipes[0]);
  close(pipes[1]);
  execvp(*cat_args, cat_args);
  exit(0);
}
else {
  // replace grep's stdin with read end of 1st pipe
  dup2(pipes[0]. 0);

  close(pipes[0]);
  close(pipes[1]);
  execvp(*grep_args, grep_args);
}
return(0);
}
```
