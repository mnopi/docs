# GLOBALS 

```bash
####################################### XDG
# https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
# XDG_CACHE_HOME      Base directory relative to which user-specific non-essential data files should be stored.
#                     If $XDG_CACHE_HOME is either not set or empty,
#                     a default equal to $HOME/.cache should be used.
# XDG_CONFIG_DIRS     Defines the preference-ordered set of base directories to search for configuration
#                     files in addition to the $XDG_CONFIG_HOME base directory.
# XDG_CONFIG_HOME     Base directory relative to which user-specific configuration files should be stored.
#                     If $XDG_CONFIG_HOME is either not set or empty,
#                     a default equal to $HOME/.config should be used. (system "{prefix}/etc").
# XDG_DATA_DIRS       Defines the preference-ordered set of base directories to search for data files in
#                     addition to the $XDG_DATA_HOME base directory.
# XDG_DATA_HOME       Base directory relative to which user-specific data files should be stored.
#                     If $XDG_DATA_HOME is either not set or empty,
#                     a default equal to $HOME/.local/share should be used (system "/usr/local/share").
# XDG_RUNTIME_DIR     Base directory relative to which user-specific non-essential runtime files and
#                     other file objects (such as sockets, named pipes, ...) should be stored.
#                     The directory MUST be owned by the user, and he MUST be the only one having read and
#                     write access to it. Its Unix access mode MUST be 0700
# XDG_STATE_HOME      Base directory relative to which user-specific state files should be stored.
#                     If $XDG_STATE_HOME is either not set or empty,
#                     a default equal to $HOME/.local/state should be used (system "/usr/local/share").
export XDG_CACHE_HOME
export XDG_CONFIG_DIRS
export XDG_CONFIG_HOME
export XDG_DATA_DIRS
export XDG_DATA_HOME
export XDG_RUNTIME_DIR
export XDG_STATE_HOME

####################################### GOOGLE CLOUD CONFIG
# https://cloud.google.com/compute/docs/gcloud-compute
# https://cloud.google.com/sdk/gcloud/reference/config
# CLOUDSDK_<SECTION>_<PROPERTY>:
# CLOUDSDK_CONFIG.                Google Cloud config directory.
# CLOUDSDK_CORE_PROJECT:          Google Cloud SDK core project.
# CLOUDSDK_COMPUTE_REGION:        Google Cloud compute region.
# CLOUDSDK_COMPUTE_ZONE:          Google Cloud compute zone..
export CLOUDSDK_CONFIG="${XDG_CONFIG_HOME}/gcloud"
export CLOUDSDK_CORE_PROJECT="jose-lumenbiomics"
export CLOUDSDK_COMPUTE_REGION="EUROPE-WEST1"
export CLOUDSDK_COMPUTE_ZONE="EUROPE-WEST1-B"

###################################### DOCKER
# https://docs.docker.com/develop/develop-images/build_enhancements/#to-enable-buildkit-builds
# https://docs.docker.com/engine/reference/commandline/cli/
# DOCKER_BUILDKIT:       If set, enables building images with BuildKit. performance, storage management,
#                        feature functionality, and security.
# DOCKER_CONFIG:         The location of your client configuration files.
# DOCKER_CONTEXT:        Name of the docker context to use (overrides DOCKER_HOST env var and default
#                        context set with docker context use).
# DOCKER_HOST:           Daemon socket to connect to, i.e.: ssh://mini.com.
export DOCKER_BUILDKIT="1"
export DOCKER_CONFIG="${XDG_CONFIG_HOME}/docker"
export DOCKER_CONTEXT
export DOCKER_HOST

###################################### GH
# https://cli.github.com/manual/gh_help_environment
# GH_CONFIG_DIR:        Directory where gh will store configuration files.
#                       Default: "$XDG_CONFIG_HOME/gh" or "$HOME/.config/gh".
# GH_HOST:              GitHub hostname for commands that would otherwise assume the "github.com" host
#                       when not in a context of an existing repository.
# GH_TOKEN:             Authentication token for github.com API requests. Setting this avoids being prompted
#                       to authenticate and takes precedence over previously stored credentials.
# GLAMOUR_STYLE.        Style to use for rendering Markdown.
export GH_CONFIG_DIR="${XDG_CONFIG_HOME}/gh"
export GH_HOST="github.com"
export GLAMOUR_STYLE="dark"

###################################### GIT
# https://git-scm.com/docs/git-config
# https://git-scm.com/docs/git-init
# GIT_COMPLETION_SHOW_ALL:  Show --arguments in completions.
# GIT_CONFIG_COUNT:     If GIT_CONFIG_COUNT is set to a positive number, all environment pairs
#	                      GIT_CONFIG_KEY_<n> and GIT_CONFIG_VALUE_<n> up to that number will be
#	                      added to the process's runtime configuration.
#                       Test: git config --get-regexp "user.*"
#                       https://github.com/git/git/blob/d8d77153eafd
# GIT_CONFIG_GLOBAL:        Configuration from the given file instead from global configuration.
# GIT_CONFIG_SYSTEM:        Configuration from the given file instead from system configuration $(prefix)/etc/gitconfig.
export GIT="${XDG_CONFIG_HOME}/git"
export GIT_COMPLETION_SHOW_ALL
export GIT_CONFIG_COUNT=3
export GIT_CONFIG_KEY_0="user.name"
export GIT_CONFIG_VALUE_0="${GIT}"
export GIT_CONFIG_KEY_1="user.email"
export GIT_CONFIG_VALUE_1="${GIT_EMAIL}"
export GIT_CONFIG_KEY_2="user.username"
export GIT_CONFIG_VALUE_2="${GIT}"
export GIT_CONFIG_GLOBAL="${GIT}/gitconfig"
export GIT_CONFIG_SYSTEM
export GIT_STORE
export GIT_TEMPLATE_DIR="${GIT}/templates"

####################################### GITHUB
# GITHUB:           GitHub login user.
# GITHUB_EMAIL:     GitHub email.
# GITHUB_ID:        GitHub organization ID.
# GITHUB_ORG:       GitHub organization name.
export GITHUB="j5pu"
export GITHUB_EMAIL="63794670+${GITHUB}@users.noreply.github.com"
export GITHUB_ID="4379404"
export GITHUB_ORG="lumenbiomics"
export GITHUB_RAW="https://raw.githubusercontent.com/${GITHUB}"

###################################### GO
# https://go.dev/blog/go116-module-changes
# GO111MODULE:    The go command now builds packages in module-aware mode by default, even when no go.mod is present.
#                 It’s still possible to build packages in GOPATH mode by setting the GO111MODULE
#                 environment variable to 'off'.
#                 You can also set GO111MODULE to 'auto' to enable module-aware mode only when a go.mod file is present
#                 in the current directory or any parent directory (before behaviour, that's why '1' was needed).
export GO111MODULE

###################################### HOMEBREW
# https://docs.brew.sh/Manpage#bundle-subcommand
# HOMEBREW_BAT:                                If set, use bat for the brew cat command.
# HOMEBREW_CACHE:                              Use this directory as the download cache.
# HOMEBREW_CASK_OPTS:                          Append these options to all cask commands. All --*dir options,
#                                              --language, --require-sha, --no-quarantine and --no-binaries are
#                                              supported. For example, you might add something like the following
#                                              to your ~/.profile, ~/.bash_profile, or ~/.zshenv.
# HOMEBREW_CLEANUP_PERIODIC_FULL_DAYS:         If set, brew install, brew upgrade and brew reinstall will cleanup all
#                                              formulae when this number of days has passed.
# HOMEBREW_DOCKER_REGISTRY_TOKEN:              Use this bearer token for authenticating with a Docker registry
#                                              proxying GitHub Packages.
# HOMEBREW_FORCE_HOMEBREW_CORE_REPO_ON_LINUX:  If set, running Homebrew on Linux will use homebrew-core instead
#                                              of linuxbrew-core.
# HOMEBREW_FORCE_BREWED_CA_CERTIFICATES:       If set, always use a Homebrew-installed ca-certificates rather than the
#                                              system version. Automatically set if the system version is too old.
# HOMEBREW_FORCE_HOMEBREW_ON_LINUX:            If set, running Homebrew on Linux will use URLs for macOS and will use
#                                              homebrew-core instead of linuxbrew-core. This is useful when merging pull
#                                              requests for macOS while on Linux.
# HOMEBREW_GITHUB_API_TOKEN:                   Use this personal access token for the GitHub API, for features
#                                              such as brew search.
# HOMEBREW_GITHUB_PACKAGES_TOKEN:              Use this GitHub personal access token when accessing the GitHub Packages
#                                              Registry (where bottles may be stored).
# HOMEBREW_GITHUB_PACKAGES_USER:               Use this username when accessing the GitHub Packages Registry
#                                              (where bottles may be stored).
# HOMEBREW_GIT_EMAIL:                          Set the Git author and committer email to this value.
# HOMEBREW_GIT_NAME:                           Set the Git author and committer name to this value.
# HOMEBREW_NO_ANALYTICS:                       If set, do not send analytics. For more information.
# HOMEBREW_UPDATE_REPORT_ONLY_INSTALLED:       If set, brew update only lists updates to installed software.
# HOMEBREW_SIMULATE_MACOS_ON_LINUX:            If set, running Homebrew on Linux will simulate certain macOS code paths.
#                                              This is useful when auditing macOS formulae while on Linux.
#                                              Implies HOMEBREW_FORCE_HOMEBREW_ON_LINUX.
export HOMEBREW_BAT="1"
export HOMEBREW_CACHE
export HOMEBREW_CASK_OPTS
export HOMEBREW_CLEANUP_PERIODIC_FULL_DAYS="7"
export HOMEBREW_COLOR="1"
export HOMEBREW_DOCKER_REGISTRY_TOKEN
export HOMEBREW_FORCE_BREWED_CA_CERTIFICATES
export HOMEBREW_FORCE_HOMEBREW_ON_LINUX
export HOMEBREW_GITHUB_API_TOKEN
export HOMEBREW_GITHUB_PACKAGES_TOKEN
export HOMEBREW_GITHUB_PACKAGES_USER
export HOMEBREW_GIT_EMAIL
export HOMEBREW_GIT_NAME
export HOMEBREW_NO_ANALYTICS="1"
export HOMEBREW_UPDATE_REPORT_ONLY_INSTALLED="1"
export HOMEBREW_SIMULATE_MACOS_ON_LINUX

export BREW_PREFIX="/usr/local"
export BREW_CELLAR="${BREW_PREFIX}/Cellar"
export BREW_ETC="${BREW_PREFIX}/etc"
export BREW_OPT="${BREW_PREFIX}/opt"
export BREW_REPOSITORY="${BREW_PREFIX}/Homebrew"
export BREW_SHARE="${BREW_PREFIX}/share"
export HOMEBREW_TAPS="${BREW_REPOSITORY}/Library/Taps"

export BREW_COMPLETIONS="${BREW_ETC}/bash_completion.d"
export BREW_PROFILE="${BREW_ETC}/profile.d"
export BREW_INFO="${BREW_SHARE}/info"
export BREW_MAN="${BREW_SHARE}/man"

###################################### JETBRAINS
# https://www.jetbrains.com/help/pycharm/tuning-the-ide.html
# PYCHARM_PROPERTIES          Platform-specific and application properties.
#                             (default: /Applications/PyCharm.app/Contents/bin/idea.properties)
# PYCHARM_VM_OPTIONS          Preferred JVM options.
#                             (default: /Applications/PyCharm.app/Contents/bin/pycharm.vmoptions)
export PYCHARM_NAME="PyCharm"
export PYCHARM_APP="/Applications/${PYCHARM_NAME}.app"
export PYCHARM_CONTENTS="${PYCHARM_APP}/Contents"
export PYCHARM="${PYCHARM_CONTENTS}/Contents/bin"

###################################### PIP
# https://pip.pypa.io/en/stable/topics/configuration/
# PIP_<UPPER_LONG_COMMAND_LINE_OPTION_NAME>  Dashes (-) have to be replaced with underscores (_).
# PIP_CACHE_DIR:                             "1" to use "--no-cache-dir" in pip site install.
# PIP_DISABLE_PIP_VERSION_CHECK:             If set, don’t periodically check PyPI to determine whether
#                                            a new version of pip is available for download.
export PIP_CACHE_DIR
export PIP_CONFIG_FILE="${XDG_CONFIG_HOME}/pip/pip.conf"
export PIP_DISABLE_PIP_VERSION_CHECK="1"

###################################### PYTHON
# https://docs.python.org/3/using/cmdline.html
# PYTHONASYNCIODEBUG:       If this environment variable is set to a non-empty string,
#                           enable the debug mode of the asyncio module.
# PYTHONDONTWRITEBYTECODE:  If set, python won’t try to write .pyc files on the import of source modules.
#                           This is equivalent to specifying the -B option.
# PYTHONNOUSERSITE:         If this is set, Python won’t add the user site-packages directory to sys.path.
# PYTHONPATH:               Augment the default search path for module files.
# PYTHONPROFILEIMPORTTIME:  If this environment variable is set to a non-empty string, Python will show how long
#                           each import takes. This is exactly equivalent to setting -X importtime on the command line.
# PYTHONPYCACHEPREFIX:      If this is set, Python will write .pyc files in a mirror directory tree at this path,
#                           instead of in __pycache__ directories within the source tree.
#                           This is equivalent to specifying the -X pycache_prefix=PATH option.
# PYTHONSTARTUP:            If this is the name of a readable file, the Python commands in that file are executed
#                           before the first prompt is displayed in interactive mode.
#                           The file is executed in the same namespace where interactive
#                           commands are executed so that objects defined or imported in it
#                           can be used without qualification in the interactive session.
#                           You can also change the prompts sys.ps1 and sys.ps2 and the hook
#                           sys.__interactivehook__ in this file.
# PYTHONUNBUFFERED:         If this is set to a non-empty string it is equivalent to specifying the -u option.
# PYTHONUSERBASE:           Defines the user base directory, which is used to compute the path of the user site-packages
#                           directory and Distutils installation paths for python setup.py install --user.
# PYTHONWARNINGS:           This is equivalent to the -W option. If set to a comma separated string,
#                           it is equivalent to specifying -W multiple times, with filters later in the
#                           list taking precedence over those earlier in the list.
#                           PYTHONWARNINGS=default  # Warn once per call location
#                           PYTHONWARNINGS=error    # Convert to exceptions
#                           PYTHONWARNINGS=always   # Warn every time
#                           PYTHONWARNINGS=module   # Warn once per calling module
#                           PYTHONWARNINGS=once     # Warn once per Python process
#                           PYTHONWARNINGS=ignore   # Never warn
export PYTHONASYNCIODEBUG="0"
export PYTHONDONTWRITEBYTECODE="1"
export PYTHONNOUSERSITE="0"
export PYTHONPATH
export PYTHONPROFILEIMPORTTIME
export PYTHONPYCACHEPREFIX
export PYTHONUNBUFFERED="1"
export PYTHONUSERBASE
export PYTHONSTARTUP
export PYTHONWARNINGS

###################################### STDLIB
# BASH_SILENCE_DEPRECATION_WARNING:     If set suppress macOS bash deprecation warning.
# CDPATH:                               Once the CDPATH is set, the cd command will search only in the directories
#                                       present in the CDPATH variable only. It SHOULD always be the first
#                                       component of the CDPATH.
# FIGNORE:                              A colon-separated list of suffixes to ignore when performing filename
#                                       completion. A filename whose suffix matches one of the
#                                       entries in 'FIGNORE' is excluded from the list of matched
#                                       filenames.  A sample value is '.o:~
# HISTSIZE:                             equivalent to 'set history-size' maximum number of history entries
#                                       saved in the history list.
# INPUTRC:                              Inputrc file to use, $include /etc/inputrc can be added to the inputrc to 
#                                       include another file.
# LS_COLORS:                            GNU
# LSCOLORS:                             macOS
export BASH_SILENCE_DEPRECATION_WARNING="1"
export CDPATH="${CDPATH}:${HOME}/GitHub"
export CLICOLOR="1"
export CLICOLOR_FORCE="1"
export GCC_COLORS="error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01"
export EDITOR="vi"
export FIGNORE=".o:~:Application Scripts"
export GREP_COLORS="ms=01;31:mc=01;31:sl=:cx=:fn=35:ln=32:bn=32:se=36"
export HISTSIZE="999999"
export HISTFILESIZE="999999"
export INPUTRC="/etc/inputrc"
export LANG="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"
export LESS="-R -F ${LESS}"
export LSCOLORS="ExGxBxDxCxEgEdxbxgxcxd"  # macOS
export PAGER="most"
export PROMPT_COMMAND="history -a;history -r"
export TERM="xterm-256color"
export TERM_PROGRAM="iTerm.app"
export VISUAL="vi"

```

