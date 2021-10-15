# BASH 

## [bash -s](https://stackoverflow.com/questions/37224634/what-does-bash-s-do/51854728)
Tells bash to read the script to execute from Standard Input, and to exit immediately 
if any command in the script (from stdin) fails.

**A downloaded sourced can be run in bash adding arguments without actually copying the file to disk.**

Both are the same:
````bash
curl -sL https://git.io/_has | bash -s
bash -c "$(curl -sL https://git.io/_has)"
````

but it allows passing arguments:
````bash
curl -sL https://git.io/_has | bash -s git
````

or:
````bash
alias has="curl -sL https://git.io/_has | bash -s"
has git
type has
````

Otherwise, the following would be required:
````bash
curl -sL https://git.io/_has > /usr/local/bin/has
````

or:
````bash
curl -sL https://git.io/_has | sudo tee /usr/local/bin/has >/dev/null
````
