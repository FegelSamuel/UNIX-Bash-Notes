# Intro
* Firstly, there are no types in Bash
```bash
HELLOWORLD=Hello World
```

# Environment Variables
```bash
HOME=/users/ZachLeach
```
* The Home Directory is now `ZachLeach`
* Typing in `cd` will take you to `ZachLeach` instead of whatever you had previously
```bash
HOME=/
```
* Home Directory is now root directory
```bash
PS1=">"
```
* Instead of `%` like how MacOS will often use for command prompting, you will be greeted with `>`
```bash
PS2="secondaryPrompt: "
```
* `PS2` basically happens when you have to be prompted twice for the same process
