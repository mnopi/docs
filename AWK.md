#  [AWK](https://www.tecmint.com/category/awk-command/) 

## Regular expressions are made of:
* Ordinary characters such as space, underscore(_), A-Z, a-z, 0-9.
* Meta characters that are expanded to ordinary characters, they include:
  * (.) it matches any single character except a newline.
  * (*) it matches zero or more existences of the immediate character preceding it.
  * [ character(s) ] it matches any one of the characters specified in character(s), one can also use a hyphen (-) to mean a range of characters such as [a-f], [1-5], and so on.
  * ^ it matches the beginning of a line in a file.
  * $ matches the end of line in a file.
  * \ it is an escape character.

In order to filter text, one has to use a text filtering tool such as awk. You can think of awk as a programming language of its own. But for the scope of this guide to using awk, we shall cover it as a simple command line filtering tool.
