What makes a scripting language different than other languages is that you can make a scripting language run programs like a linux command

<Best practice to use only ONE `#!` operator at the top of your python or bash files
`#!bin/bash`
`#!bin/python3`

I can name a file test.py and run it with the bash command `./test.py`

Within `test.py`:

`#!bin/python3`
`print("Hello World");`
`#end of file`

Because of the first line, we don't have to manually compile it when we run the shit like how we had to do `g++` sorcery with the helloworld.cpp C++ file

