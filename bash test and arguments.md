# Shell

## [getoptions](https://github.com/ko1nksm/getoptions)

[References](https://github.com/ko1nksm/getoptions/blob/master/docs/References.md)
* [Global functions](https://github.com/ko1nksm/getoptions/blob/master/docs/References.md#global-functions): getoptions, getoptions_abbr, getoptions_help and getoptions_parse.
* [Option parser](https://github.com/ko1nksm/getoptions/blob/master/docs/References.md#option-parser): Option parser definition function, custom error handler and prehook.
* [Helper functions](https://github.com/ko1nksm/getoptions/blob/master/docs/References.md#helper-functions): Data types & initial values, setup, flag, param option, disp, msg, cmd and attributes related to the help display.

````bash
VERSION="0.1"

parser_definition() {
  setup   REST help:usage -- "Usage: example.sh [options]... [arguments]..." ''
  msg -- 'Options:'
  flag    FLAG    -f --flag                 -- "takes no arguments"
  param   PARAM   -p --param                -- "takes one argument"
  option  OPTION  -o --option on:"default"  -- "takes one optional argument"
  disp    :usage  -h --help
  disp    VERSION    --version
}

eval "$(getoptions parser_definition) exit 1"

echo "FLAG: $FLAG, PARAM: $PARAM, OPTION: $OPTION"
printf '%s\n' "$@" # rest arguments
````

````bash
example.sh -f --flag -p VALUE --param VALUE -o --option -oVALUE --option=VALUE 1 2 3
````

````bash
$ example.sh --help

Usage: example.sh [options]... [arguments]...

Options:
  -f, --flag                  takes no arguments
  -p, --param PARAM           takes one argument
  -o, --option[=OPTION]       takes one optional argument
  -h, --help
      --version
````

### Usage as generator
The arguments of @gengetoptions are the same as the arguments of the gengetoptions command, 
which allows you to embed the library as well as the parser.
````bash
#!/bin/sh

set -eu

# @getoptions
parser_definition() {
  setup   REST help:usage -- "Usage: example.sh [options]... [arguments]..." ''
  msg -- 'Options:'
  flag    FLAG    -f --flag                 -- "takes no arguments"
  param   PARAM   -p --param                -- "takes one argument"
  option  OPTION  -o --option on:"default"  -- "takes one optional argument"
  disp    :usage  -h --help
  disp    VERSION    --version
}
# @end

# @gengetoptions parser -i parser_definition parse
# @end

parse "$@"
eval "set -- $REST"

echo "FLAG: $FLAG, PARAM: $PARAM, OPTION: $OPTION"
printf '%s\n' "$@" # rest arguments
````

````bash
gengetoptions embed --overwrite example.sh
````

### Examples
  * [Basic](https://github.com/ko1nksm/getoptions/blob/master/examples/basic.sh)
  * [Advanced with Custom error handler and helper functions](https://github.com/ko1nksm/getoptions/blob/master/examples/advanced.sh) -  Change the standard error messages, respond to additional error messages, and change the exit status. For example, getoptions does not have a helper function to assign to the array, but it can be easily implemented by a custom helper function.
  * [Subcommand](https://github.com/ko1nksm/getoptions/blob/master/examples/subcmd.sh) - When using subcommands in getoptions, parse the arguments multiple times. (For example, parse up to the subcommand, and then parse after it. This design is useful for splitting shell scripts by each subcommand.
  * [Prehook](https://github.com/ko1nksm/getoptions/blob/master/examples/prehook.sh) - f you define a prehook function in the parser definition, it will be calledbefore helper functions is called. This allows you to process the arguments before calling the helper function.
  * [ShellSpec optparser practical example `shellspec -h`](https://github.com/shellspec/shellspec/tree/master/lib/libexec/optparser)

## [hyperfine - A command-line benchmarking tool.](https://github.com/sharkdp/hyperfine)
````bash
hyperfine 'sleep 0.3'
hyperfine --min-runs 5 'sleep 0.2' 'sleep 3.2'
````
If the program execution time is limited by disk I/O, the benchmarking results can be heavily influenced by disk caches and whether they are cold or warm.

If you want to run the benchmark on a warm cache, you can use the -w/--warmup option to perform a certain number of program executions before the actual benchmark:
````bash
hyperfine --warmup 3 --ignore-failure 'grep -R TODO *' 2>/dev/null
hyperfine --warmup 3 ls 2>/dev/null
````

## [shellspec](https://github.com/shellspec/shellspec)

[Info](https://shellspec.info/)

### [Tutorial](https://github.com/shellspec/shellspec#tutorial)
Write hello function:
````bash
at<<HERE >lib/hello.sh
hello() {
  echo "Hello ${1}!"
}
HERE
````

Initialize:
````bash
shellspec --init
````

Write your first specfile (of course you can use your favorite editor):
````bash
cat<<HERE >spec/hello_spec.sh
Describe 'hello.sh'
  Include lib/hello.sh
  It 'says hello'
    When call hello ShellSpec
    The output should equal 'Hello ShellSpec!'
  End
End
HERE
````

Test:
````bash
shellspec
````
If you want to test with a specific shell, 
use the -s (--shell) option. You can specify the default shell in the .shellspec file.

### [CLI](https://github.com/shellspec/shellspec#shellspec-cli)
````bash
shellspec -h
````

### [Project directory](https://github.com/shellspec/shellspec#project-directory)

#### [Options file](https://github.com/shellspec/shellspec#options-file)
1. $XDG_CONFIG_HOME/shellspec/options
2. $HOME/.shellspec-options (version >= 0.28.0) or $HOME/.shellspec (deprecated)
3. <PROJECT-ROOT>/.shellspec
4. <PROJECT-ROOT>/.shellspec-local (Do not store in VCS such as git)

#### [Specfile test file](https://github.com/shellspec/shellspec#specfile-test-file)
In ShellSpec, you write your tests in a specfile. By default, specfile is a file ending with _spec.sh under the spec directory.

The specfile is executed using the shellspec command, but it can also be executed directly. 
See [self-executable specfile](https://github.com/shellspec/shellspec#self-executable-specfile) for details.
````bash
Describe 'lib.sh' # example group
  Describe 'bc command'
    add() { echo "$1 + $2" | bc; }

    It 'performs addition' # example
      When call add 2 3 # evaluation
      The output should eq 5  # expectation
    End
  End
End
````
You can embed shell functions (or shell script code) in the specfile. This shell function can be used for test preparation and complex testing.

Note that the specfile implements scope using subshells. Shell functions defined in the specfile can only be used within blocks (e.g. Describe, It, etc).

If you want to use a global function, you can define it in spec_helper.sh.

### [DSL syntax](https://github.com/shellspec/shellspec#dsl-syntax)
### [Directives](https://github.com/shellspec/shellspec#directives)
Directives (`%directive`) are instructions that can be used in embedded shell scripts. It is used to solve small problems of shell scripts in testing.
### [Mocking](https://github.com/shellspec/shellspec#mocking)
There are two ways to create a mock, (shell) function-based mock and (external) command-based mock. The function-based mock is usually recommended for performance reasons. Both can be overwritten with an internal block and will be restored when the block ends.
### [Support commands](https://github.com/shellspec/shellspec#support-commands)
Support commands are helper commands that can be used in the specfile. For example, it can be used in a mock function to execute the actual command. It is recommended that the support command name be the actual command name prefixed with @.
### [Tagging](https://github.com/shellspec/shellspec#tagging)
The example groups or examples can be tagged, and the --tag option can be used to filter the examples to be run. The tag name and tag value are separated by :, and the tag value is optional. You can use any character if quoted.
### [altshfmt - Syntax formatter](https://github.com/shellspec/shellspec#syntax-formatter-altshfmt)
`````bash
brew tap j5pu/tools
brew install j5pu/tools/altshfmt
`````

PyCharm update:
`Preferences -> Languages & Frameworks -> BashSupport Pro -> shift Formatter -> Path to shfmt: /usr/local/bin/altshfmt`

### [How to test a single file shell script](https://github.com/shellspec/shellspec#how-to-test-a-single-file-shell-script)
If the shell script consists of a single file, unit testing becomes difficult. However, there are many such shell scripts.

ShellSpec has the ability to testing in such cases with only few modifications to the shell script. `run script` or `run source`

### [Examples](https://github.com/shellspec/shellspec/blob/master/examples/spec)
#### [getoptions](https://github.com/ko1nksm/getoptions/tree/master/spec)
````bash
shellspec --shell bash
````
## Sourced or Executed 

````bash
if (( ${BASH_LINENO:-0} == 0 )); then
  echo "${0} - executed with args: ${@}"
  exit
else
  echo "${BASH_SOURCE[0]} - sourced with args: ${@}"
  return
fi
````

## See also

### Completion 
  * [Automatically generate ZSH/Bash completion files](https://unix.stackexchange.com/questions/417054/automatically-generate-zsh-bash-completion-files) 
  * [10 Useful Bash Complete Command Examples](https://www.thegeekstuff.com/2013/12/bash-completion-complete/) 
  * [Shell Completion: Python Click](https://click.palletsprojects.com/en/7.x/bashcomplete/) 
  * [Shell Completion: Python Argparse](https://kislyuk.github.io/argcomplete/) 
  * [GNU: Programmable Completion](https://www.gnu.org/software/bash/manual/html_node/Programmable-Completion.html) 
  * [GNU: Programmable Completion Builtins](https://www.gnu.org/software/bash/manual/html_node/Programmable-Completion-Builtins.html) 
  * [GNU: A Programmable Completion Example](https://www.gnu.org/software/bash/manual/html_node/A-Programmable-Completion-Example.html) 
  * [github.com/scop/bash-completion](https://github.com/scop/bash-completion) - bash-completion is a collection of command line command completions for the Bash shell, collection of helper functions to assist in creating new completions, and set of facilities for loading completions automatically on demand
  * [Bash Completion, Part 2: Programmable Completion](https://spin.atomicobject.com/2016/02/14/bash-programmable-completion/) 

### Readline - Inputrc
  * [GNU: Command Line Editing](https://www.gnu.org/software/bash/manual/html_node/Command-Line-Editing.html) 
  * [GNU: Bindable Readline Commands](https://www.gnu.org/software/bash/manual/html_node/Bindable-Readline-Commands.html) 
  * [GNU: Bindable Readline Commands - Commands-For-Completion](https://www.gnu.org/software/bash/manual/html_node/Commands-For-Completion.html) 
  * [Useful Command Line Bash Shortcuts](https://www.tecmint.com/linux-command-line-bash-shortcut-keys/) 
  * [Alt+key not working in embedded terminal](https://intellij-support.jetbrains.com/hc/en-us/community/posts/115000013224-Alt-key-not-working-in-embedded-terminal) 

### Shell 
  * [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)

### Docs 
  * [Command-line interface description language](http://docopt.org/) 
