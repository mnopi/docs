# Install

## SYNC

### [watchman](https://facebook.github.io/watchman/)

Watch files and records, or triggers actions, when they change.

### [watchexec](https://github.com/watchexec/watchexec)

Execute commands in response to file modifications.

#### [cargo-watch](https://github.com/watchexec/cargo-watch)

Watches over your project's source for changes, and runs Cargo commands when they occur

### [wfh](https://github.com/kzys/wfh)

Continuously watches your local directories and rsync them against a remote host.

### [gaze](https://github.com/wtetsu/gaze)

Runs a command, right after you save a file.

### [croc](https://github.com/schollz/croc)

Easily and securely send things from one computer to another.

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

### [nixos](https://nixos.org/)
Reproducible builds and deployments.

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

### [goto](https://github.com/iridakos/goto)

Alias and navigate to directories with tab completion in Linux.


## MULTI REPO

### [gita](https://github.com/nosarthur/gita)

Manage many git repos with sanity.

### [vcsh](https://github.com/RichiH/vcsh)

Version Control System for $HOME - multiple Git repositories in $HOME.

### [ghorg](https://github.com/gabrie30/ghorg)

Quickly clone all of an orgs, or users repos into a single directory.

### [mr](https://myrepos.branchable.com/)

Multiple Repository management tool [repository](git://myrepos.branchable.com/).

## Commands

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

### [finicky](https://github.com/johnste/finicky)
A macOS app for customizing which browser to start

## PIPING & FILTER

### [luneta](https://github.com/fbeline/luneta)

Luneta is an interactive command-line filter that can be applied to any list, e.g., cat $(ls | luneta)

### [squeeze](https://github.com/aymericbeaumet/squeeze)

Exit if no output for piping.
Enables to extract rich information from any text (raw, JSON, HTML, YAML, man pages, etc).

### [Loop](https://github.com/Miserlou/Loop)

Write powerful, intuitive looping one-liners in your favorite shell! Finally, loops in Bash that make sense!.

## DEVELOPMENT

### [darling](https://github.com/darlinghq/darling.git)
Darwin/macOS emulation layer for Linux.

### [infi.recipe.application_packager](https://github.com/Infinidat/infi.recipe.application_packager.git)
Buildout recipe for creating the platform-specific packages.

### [LTFinderButtons](https://github.com/lexrus/LTFinderButtons.git)

My Finder buttons collection for macOS.

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

### [github-release](https://github.com/github-release/github-release)

Commandline app to create and edit releases on GitHub (and upload artifacts).

### [linguist](https://github.com/github/linguist)

Language Savant. If your repository's language is being reported incorrectly, send us a pull request!

### [sd](https://github.com/chmln/sd)

Intuitive find & replace CLI.

### [ripgrep](https://github.com/BurntSushi/ripgrep)

Search tool that recursively searches the current directory for a regex pattern.

### [procs](https://github.com/dalance/procs)

Replacement for ps.

### [whalebrew](https://github.com/whalebrew/whalebrew)

Homebrew, but with Docker images.

### [hyperfine](https://github.com/sharkdp/hyperfine)

A command-line benchmarking (time) tool.

### [fzf](https://github.com/junegunn/fzf)

General-purpose command-line fuzzy finder.

### [envv](https://github.com/jakewendt/envv)

Envv is a shell-independent way of handling environment variables.

### [duf](https://github.com/muesli/duf)

Disk Usage/Free Utility - a better 'df' alternative.

### [jc](https://github.com/kellyjonbrazil/jc)

CLI tool and python library that converts the output of popular command-line
tools and file-types to JSON or Dictionaries.
This allows piping of output to tools like jq and simplifying automation scripts.
[parsers](https://github.com/kellyjonbrazil/jc#parsers)

### [doing](https://github.com/ttscoff/doing.git)
A command line tool for remembering what you were doing and tracking what you've done.

### [asimov](https://github.com/stevegrunwell/asimov)

Automatically exclude development dependencies from Apple Time Machine backups.

### [gget](https://github.com/dpb587/gget)

An easier way to find and automate file downloads from GitHub and GitLab repositories,[docs](https://gget.io/)

### [doppler]()

### [dust](https://github.com/bootandy/dust)

A more intuitive version of du in rust.

### [fd](https://github.com/sharkdp/fd)

A simple, fast and user-friendly alternative to 'find'.

### [vivid](https://github.com/sharkdp/vivid)

A themeable LS_COLORS generator with a rich filetype database.

### [complete-alias](https://github.com/cykerway/complete-alias)

Automagically shell alias completion.

### [emoji-cli](https://github.com/wfxr/emoji-cli.git)

Emoji CLI.

### [topgrade](https://github.com/r-darwish/topgrade.git)
Upgrade everything

### [github2mr](https://github.com/skx/github2mr.git)
Export all your github repositories to a form suitable for 'myrepos' to work with.

### [git-plus](https://github.com/tkrajina/git-plus.git)
Git utilities (semver, run one command in multiple repos, etc.)

### [gitbatch](https://github.com/isacikgoz/gitbatch.git)
Manage your git repositories in one place.

### [gita](https://github.com/nosarthur/gita)
Manage many git repos with sanity.

### [repo](https://android.googlesource.com/tools/repo)
Manage many Git repositories, does the uploads to revision control systems, and automates parts of the development 
workflow. Repo is not meant to replace Git, only to make it easier to work with Git. The repo command is an executable 
Python script that you can put anywhere in your path.
```bash
mkdir -p ~/.bin
PATH="${HOME}/.bin:${PATH}"
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo
chmod a+rx ~/.bin/repo

```

### [bashhub](https://bashhub.com/)
Bash history in the cloud. Indexed and searchable.

### [git-repo-updater](https://github.com/earwig/git-repo-updater.git)
A console script that allows you to easily update multiple git repositories at once.

### [m-cli](https://github.com/rgcr/m-cli)

```bash


m airdrop status
m appearance help 

m bluetooth status    # bluetooth status
m bluetooth on        # turn on bluetooth
m bluetooth enable    # turn on bluetooth
m bluetooth off       # turn off bluetooth
m bluetooth disable   # turn off bluetooth


m dir tree        # tree view of folders in the current path
m dir tree /path  # tree view of folders in a specific path
m dir delete empty          # delete empty folders recursively in the current path
m dir delete empty /path    # delete empty folders recursively in a specific path

m dir delete dsfiles        # delete .DS_Store files recursively in the current path
m dir delete dsfiles /path  # delete .DS_Store files recursively in a specific path
m dir dsfiles on   # restore generation of .DS_Store
m dir dsfiles off  # prohibit generation of .DS_Store
m dir size        # calculate current folder size
m dir size /path  # calculate folder size in a specific path

m disk ls                                 # list disks
m disk list                               # list disks
m disk list /dev/disk0                    # list a specific disk
m disk ejectall
m disk fs                                 # list available filesystems for formatting
m disk filesystems                        # list available filesystems for formatting

m display status   # status of displays
m display help     # show usage
m display up       # turn up the brightness
m display down     # turn down the brightness

m dns flush       # flushes local DNS

m dock help 

m finder showhiddenfiles           # get the current status
m finder showhiddenfiles YES       # show hidden files
m finder showhiddenfiles NO        # don't show hidden files
m finder showextensions            # get the current status
m finder showextensions YES        # show all file extensions
m finder showextensions NO         # don't show all file extensions
m finder showdesktop               # get the current desktop status
m finder showdesktop YES           # enable the desktop
m finder showdesktop NO            # disable the desktop
m finder showpath YES              # show the current opened folder path on the top bar of the Finder window
m finder showpath NO               # show the current opened folder name on the top bar of the Finder window

m firewall status
m firewall list

m flightmode off
m flightmode on 

m gatekeeper status
m gatekeeper disable

m group list                          # get list of groups
m group adduser jose staff        # add an user to a specific group
m group ismember jose staff       # show if the user is a member of a specific group

m hostname                # get the current hostname information (computername, hostname, localhostname and netbiosname)
m hostname newhostname    # set a new hostname (computername, hostname, localhostname, netbiosname)
m hostname help           # only shows this help

m info        #  print macOS operating system version information

m localhost ls                              # list current records in localhost
m localhost add 127.0.0.1 webpage.local     # add a new host to the localhost file
m localhost remove webpage.local            # remove a host from the localhost file

m lock     # lock session

m network ls                          # list network interfaces
m network location switch XYZ         # switch location
m network location switch XYZ         # switch location
m network location ls                 # list locations

m nosleep until 3600            # no sleep until 3600 seconds
m nosleep until my_script.sh    # no sleep until the script ends
m nosleep until pid 64377       # no sleep until the process id ends

m notification showcenter
m notification showcenter NO

m ntp status

m printer queue

m restart     # restart computer (needs confirmation)
m restart -f  # restart computer (without confirmation)

m safeboot status

m screensaver                         # launch screensaver
m screensaver status                  #  get the current status
m screensaver askforpassword          #  get password requirement to unlock
m screensaver askforpassword YES      #  enable password requirement to unlock
m screensaver askforpassword NO       #  disable password requirement to unlock

m service --status-all
m service --ls
m service --ls com.apple.sessionlogoutd
m service start com.apple.sessionlogoutd

m trash clean

m timezone                    # get current timezone
m timezone ls                 # list available timezones
m timezone set Europe/Berlin  # set timezone
    
m update list                                                 # list available updates
m update install all

m user ls
m user info jose

m volume up     # increase the volume by 6.25
m volume down   # decrease the volume by 6.25
m volume mute   # set mute
m volume unmute # unset mute
    
m vpn ls 

m wifi on 
m wifi off 
```

gatekeeper disable

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
