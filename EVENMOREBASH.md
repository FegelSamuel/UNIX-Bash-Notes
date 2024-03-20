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
