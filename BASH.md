# BASH 

## BASH_ENV and ENV 

### sh/dash 
A *login shell* first reads commands
from the files `/etc/profile` and `.profile` if they exist.  If the
environment variable `ENV` is set on entry to an interactive shell,
or is set in the `.profile` of a login shell, the shell next reads
commands from the file named in `ENV`.  Therefore, a user should
place commands that are to be executed only at login time in the
`.profile` file, and commands that are executed for every *interactive*
shell inside the `ENV` file:
* `ENV` if in *login and in profile* - *reads after*. 
* `ENV` in every *interactive shell*.

`--rcfile` option has *no effect*.

### bash: 
When bash is started *non-interactively*, to run a shell script,
for example, it looks for the variable `BASH_ENV` in the environment,
expands its value if it appears there, and uses the expanded value
as the name of a file to read and execute.
* Interactive: `.bashrc`
* `BASH_ENV` in every *non-interactive*.

In sh: `--rcfile` option has *no effect*.

### Conclusion
* `ENV` is like having a `.bashrc` for *interactive* in *shell* (--rcfile no effect)
* `BASH_ENV` for *non-interactive*

## [ and ]
* Within [ and ], character classes can be specified using the syntax [:class:], 
where  class  is  one  of  the  following
*classes* defined in the POSIX standard:
*alnum alpha ascii blank cntrl digit graph lower print punct space upper word xdigit*
A character class *matches any character belonging to that class*.  The *word* character class 
matches *letters*, *digits*, and the character *_*.

* Within [ and ], an equivalence class can be specified using the syntax [=c=], 
which *matches all characters* with the same
collation weight (as defined by the current locale) as the character c.

* Within [ and ], the syntax [.symbol.] *matches the collating symbol* symbol

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
