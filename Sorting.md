For this example, we are going to be using the Pipe operator `|`, which takes a left input and puts its output into the right function's arguments

```bash
ls -ltr | sort
```
* `-l` Uses a long listin format
* `-t` Sorts by modification time
* `-r` Reverse order when searching
* Pretty simple stuff, right? Just display a list with some options/flags sorted. Remember that using the `-` allows you to add multiple options in the same field
## Something More
```bash
ls -ltr | sort -n
```
* sorts by numeric value
```bash
ls -ltr | sort -k3
```
* Sorts by third field, which is what you think it is
```bash
ls -ltr | -rnk3
```
* Sorts by third field by numeric value, reversed.
```bash
ls -ltr /usr/bin | sort -nk5 | tail -1
```
* Grabs the last file sorted by the fifth field

