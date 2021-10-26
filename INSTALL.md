# Install

## SYNC

### [watchman](https://facebook.github.io/watchman/)
Watch files and records, or triggers actions, when they change.

### [wfh](https://github.com/kzys/wfh)
Continuously watches your local directories and rsync them against a remote host.

### [gaze](https://github.com/wtetsu/gaze)
Runs a command, right after you save a file.

### [croc](https://github.com/schollz/croc)
Easily and securely send things from one computer to another.

### [watchexec](https://github.com/watchexec/watchexec)
Execute commands in response to file modifications.

### [modd](https://github.com/cortesi/modd)
A flexible developer tool that runs processes and responds to filesystem changes.

### [reflex](https://github.com/cespare/reflex)
Run a command when files change.

## DOTFILES

### [dotfiles](https://github.com/sobolevn/dotfiles)
Dotfiles for the developer happiness: macos, zsh, brew, vscode, codespaces, python, node, elixir.

### [homesick](https://github.com/andsens/homeshick/wiki/Myrepos)
Dotfiles synchronizer written in bash.

### [rcm](https://github.com/thoughtbot/rcm)
Management suite for dotfiles (allows users and hosts/os).

### [shallow-backup](https://github.com/alichtman/shallow-backup)
Create lightweight backups of installed packages, applications, fonts and dotfiles, and automatically
push them to a remote Git repository.

### [zero.sh](https://github.com/zero-sh/zero.sh)
Create an identical installation on any **macOS** with a single command.
Replaces [cider](https://github.com/msanders/cider) which used `swift` for preferences.

### [dotdrop](https://github.com/deadc0de6/dotdrop)
It allows you to store your dotfiles in Git and automagically deploy **different versions**
of the same file on different setups.

### [dotbot](https://github.com/anishathalye/dotbot)
A tool that bootstraps your dotfiles.

## TASKS & BUILD

### [gitversion](https://gitversion.net/)
From git log to SemVer in no time.

### [git-extras](https://github.com/tj/git-extras)
Little git extras.

### [ini2toml](https://github.com/abravalheri/ini2toml)
Automatically conversion of `.ini/.cfg` files to TOML equivalents.

### [ppsetuptools](https://github.com/TheCleric/ppsetuptools)
Metadata in `pyproyect.toml`.

### [task](https://github.com/go-task/task)
It has releaser for debian and taps.

### [just](https://github.com/casey/just)
Handy way to save and run project-specific commands.

### [batou](https://github.com/flyingcircusio/batou)
Automate your application deployments.

### [prefect](https://github.com/PrefectHQ/prefect)
A new workflow management system, designed for modern infrastructure and powered by
the open-source Prefect Core workflow engine.
Users organize Tasks into Flows, and Prefect takes care of the rest.

### [python-decouple](https://github.com/henriquebastos/python-decouple)
Strict separation of config from code.
Helps you to organize your settings so that you can change parameters without having to redeploy your app.

### [taskipy](https://pypi.org/project/taskipy)
`task` conflicts with `brew go-task` which install `task`.
Complementary task runner for python, defines tasks in `pyproyect.toml`.

### [semver_bash](https://github.com/cloudflare/semver_bash)
Semantic Versioning in Bash.

## PROFILE & BTRAP

### [auto-auto-complete](https://github.com/maandree/auto-auto-complete)
Autogenerate shell auto-completion scripts.

### [apt-dater](https://github.com/DE-IBH/apt-dater)
Manage apt remotely.

### [envv](https://github.com/jakewendt/envv)
Envv is a shell-independent way of handling environment variables.

### [prefsniff](https://pypi.org/project/prefsniff)
Generate defaults commands for macOS.

````bash
prefsniff /Users/jose/Library/Preferences/.GlobalPreferences.plist
# defaults write NSGlobalDomain com.apple.swipescrolldirection -bool False
prefsniff /Users/jose/Library/Preferences --show-diffs
````

### [pyicloud](https://github.com/picklepete/pyicloud)
PyiCloud is a module which allows pythonistas to interact with iCloud webservices.
It's powered by the fantastic [requests](https://github.com/kennethreitz/requests) HTTP library.



## DIRECTORIES

### [zoxide](https://github.com/ajeetdsouza/zoxide)
Fast replacement for your cd command, inspired by z and autojump. It keeps track of the directories you use most frequently, and uses a ranking algorithm to navigate to the best match.


### [bashmarks](https://github.com/huyng/bashmarks)
Directory bookmarks for the shell.

### [goto](https://github.com/iridakos/goto)
Alias and navigate to directories with tab completion in Linux.

### [marker](https://github.com/pindexis/marker)
Marker is a command palette for the terminal. It lets you bookmark commands (or commands templates) and easily retreive them with the help of a real-time fuzzy matcher.


### [autojump](https://github.com/wting/autojump)
A faster way to navigate your filesystem.


## MULTI REPO

### [gita](https://github.com/nosarthur/gita)
Manage many git repos with sanity.

### [vcsh](https://github.com/RichiH/vcsh)
Version Control System for $HOME - multiple Git repositories in $HOME.

### [ghorg](https://github.com/gabrie30/ghorg)
Quickly clone all of an orgs, or users repos into a single directory.

### [mr](https://myrepos.branchable.com/)
Multiple Repository management tool.

### [tre-command](https://github.com/dduan/tre)
A modern alternative to the tree command.

### [broot](https://dystroy.org/broot/)
Get an overview of a directory, even a big one.

### [lsd](https://github.com/Peltoche/lsd)
This project is a rewrite of GNU ls with a lot of added features like colors, icons, tree-view, more formatting options etc.

## APPs

### [swiftbar](https://github.com/swiftbar/SwiftBar.git)
Menu bar actions, for instance: open atom-icon-associations.xml or build.

### [nativefier](https://github.com/nativefier/nativefier.git)
Generate macOS app from link.

### [servicestation](https://servicestation.menu/)
Customize your right-click menu with Service Station.

### [ccat](https://github.com/owenthereal/ccat)
Colorizing cat. It works similar to cat but displays content with syntax highlighting.



## PIPING & FILTER

### [luneta](https://github.com/fbeline/luneta)
Luneta is an interactive command-line filter that can be applied to any list, e.g., cat $(ls | luneta)

### [squeeze](https://github.com/aymericbeaumet/squeeze)
Exit if no output for piping.
Enables to extract rich information from any text (raw, JSON, HTML, YAML, man pages, etc).

### [Loop](https://github.com/Miserlou/Loop)
Write powerful, intuitive looping one-liners in your favorite shell! Finally, loops in Bash that make sense!.



## DEVELOPMENT

### [Docker Buildx](https://docs.docker.com/buildx/working-with-buildx/)
- build for target platforms.
- buildkit.
- outputs configuration.
- inline build cache.
- docker buildx bake: similar a docker-compose build.

### [xonsh](https://github.com/xonsh/xonsh)
Python-powered, cross-platform, Unix-gazing shell.

### [mo](https://github.com/tests-always-included/mo)
Mustache templates in pure bash.

### [niet](https://github.com/openuado/niet)
Parse/Read yaml or json files directly in your shell (sh, bash, ksh, ...).

### [sarge](https://sarge.readthedocs.io/en/latest/overview.html)
Subprocess.

### [buku](https://github.com/jarun/buku)
Powerful bookmark manager and a personal textual mini-web.

### [http-prompt](https://github.com/httpie/http-prompt)
An interactive command-line HTTP and API testing client built on top of HTTPie featuring autocomplete, syntax highlighting, and more.

### [hyperfine](https://github.com/sharkdp/hyperfine)
A command-line benchmarking (time) tool.

### [fd](https://github.com/sharkdp/fd)
Find entries in your filesystem. It is a simple, fast and user-friendly alternative to find.

### [exa](https://the.exa.website/)
A modern replacement for ls.

### [pueue](https://github.com/Nukesor/pueue)
Command-line task management tool for sequential and parallel execution of long-running tasks.

### [livepython](https://github.com/agermanidis/livepython)
Visually trace Python code in real-time.

### [fac](https://github.com/mkchoi212/fac)
Easy-to-use CUI for fixing git conflicts.

### [gitsome](https://github.com/donnemartin/gitsome)
A supercharged Git/GitHub command line interface (CLI).

### [sd](https://github.com/chmln/sd)
Intuitive find & replace CLI.

### [ripgrep](https://github.com/BurntSushi/ripgrep)
Search tool that recursively searches the current directory for a regex pattern.

### [procs](https://github.com/dalance/procs)
Replacement for ps.


## From my legacy

### Access

`/Users/jose/backups/data/Applications/Access.app/Contents/MacOS/Access`

## ToDo

* [git-sync](https://github.com/kubernetes/git-sync) look el git-sync y que genera las images con docker buildx
* [has](https://hub.docker.com/r/kdabir/has-test-containers) como synchronize los containers de GitHub con DockerHub.
* tests de etc e ir desarrollando uno a uno y que se actualice el setup.cfg.
* look si uso el makefile o el prefect o el taskipy o el task-go
* el getopt
* [man](https://docs.asciidoctor.org/asciidoctor/latest/manpage-backend/) colores y referencias y [color en map](https://felipec.wordpress.com/2021/06/05/adventures-with-man-color/)
* help/usage con man page de los scripts que estoy usando. hacer un script que sea de grep e los atributos y que pruebe primero si tiene man y luego si tiene --help.
* el puto servidor de gcloud crearlo de una puta vez.
* ahora  la mierda de hacer un paquete que sea jet para manejar jetbrains iconos etc.
*
