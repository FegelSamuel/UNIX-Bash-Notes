```bash
if [ -x /usr/bin/id ]; then # Check if the file named "id" is executable
  if [-x "$EUID]; then  # inline "thens" used with semicolons
    EUID=`/user/bin/id -u`
    UID=`/usr/bin/id -ru`
  fi
  USER="`/usr/bin/id/`"
else
  echo "/usr/bin/id not executable!"
  echo
fi
```
This command changes your prompt with its environment variable
```bash
PS1="{/h:/d:/w}" # Host Name:Date:Working Directory
```

# While Loops
```bash
echo                            # skip a line
count=1                         # initialize the count variable
while [ $count  -lt  10 ]       # start the while loop   
   do
      echo $count                       # display count value
      count=`expr $count + 1`           # increment count using the "expression" keyword
done                            # end of the while loop
```
