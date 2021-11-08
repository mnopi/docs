# [READLINE](https://tiswww.case.edu/php/chet/readline/readline.html#SEC1)
The name of this file is taken from the value of the **INPUTRC** environment variable. 
If that variable is unset, the **default** is _~/.inputrc_.  
If that file  does not exist or cannot be read, the **ultimate default** is _/etc/inputrc_.


- **line feed**: moving cursor one line _forward_ (**\n**) - **Signals end of line** (does not move cursor to next line)
- **carriage return**:  moving cursor to _beginning_ of line (**\r**) - (move to next line)

The following **symbolic character name**s are recognized while processing key bindings: 
- DEL
- ESC
- ESCAPE
- LFD (line feed)
- NEWLINE
- RET
- RETURN
- RUBOUT (<- delete)
- SPACE
- SPC (space bar)
- TAB

### Key Bindings Specification: SYMBOLIC KEY NAME
keyname:function-name or macro 

**Keyname is the name of a key spelled out in English**
```bash
# make M-C-u execute the readline command universal-argument
M-Control-u: universal-argument  # or C-Meta-u: universal-argument
```

```bash
# When using the form keyname:function-name or macro, keyname is the name of a key spelled out in English.  For example:
Control-u: universal-argument  # C-u is bound to the function universal-argument
Meta-Rubout: backward-kill-word  # M-DEL is bound to the function backward-kill-word
Control-o: "> output"  # C-o is bound to run the macro expressed on the right hand side (that is, to insert the 
                       # text ``> output'' into the line).
                       
```
When entering the text of a macro, single or double quotes should be used to indicate a macro definition.  
Unquoted text is assumed to be a function name. In the macro body, the backslash escapes described above are expanded.  
Backslash will quote any other character in the macro text, including " and '.

### Key Bindings Specification: KEY SEQUENCE
"keyseq":function-name or macro

#### Emacs-style notation 

````bash
"\C-u": universal-argument  # C-u is again bound to the function universal-argument
"\C-x\C-r": re-read-init-file  # C-x C-r is bound to the function re-read-init-file
"\e[11~": "Function Key 1"  # ESC [ 1 1 ~ is bound to insert the text ``Function Key 1''.
````
The full set of GNU Emacs style escape sequences available when specifying key sequences is:
* **\C-**    _control prefix_
* **\M-**    _meta prefix_
* **\e **    an _escape character_
* **\\ **    _backslash_
* **\" **    literal _"_, a double quote
* **\' **    literal _'_, a single quote

In addition to the GNU Emacs style escape sequences, a second set of backslash escapes is available:
* **\a  **   _alert_ (bell)
* **\b  **   _backspace_
* **\d  **   _delete_
* **\f  **   _form feed_
* **\n  **   _newline_
* **\r  **   _carriage return_
* **\t  **   _horizontal tab_
* **\v  **   _vertical tab_
* **\nnn**   the eight-bit character whose value is the octal value nnn (one to three digits)
* **\xHH**   the eight-bit character whose value is the hexadecimal value HH (one or two hex digits)

Examples: 
* **C-n** means _Control-N_
* **M-x** means _Meta-X_
* **M-C-x** means _ESC-Control-x_


## Command for Moving 
       beginning-of-line (C-a)
              Move to the start of the current line.
       end-of-line (C-e)
              Move to the end of the line.
       forward-char (C-f)
              Move forward a character.
       backward-char (C-b)
              Move back a character.
       forward-word (M-f)
              Move forward to the end of the next word.  Words are composed of alphanumeric characters 
              (letters and digits).
       backward-word (M-b)
              Move back to the start of the current or previous word.  Words are composed of alphanumeric characters 
              (letters and digits).
       clear-screen (C-l)
              Clear the screen leaving the current line at the top of the screen.  With an argument, 
              refresh the current line without clearing the screen.
       redraw-current-line
              Refresh the current line.

## Commands for Changing Text
       end-of-file (usually C-d)
              The character indicating end-of-file as set, for example, by ``stty''.  
              If this character is read when there are no characters on the line, and point is at the
              beginning of the line, Readline interprets it as the end of input and returns EOF.
       delete-char (C-d)
              Delete the character at point.  If this function is bound to the same character as the tty EOF character, 
              as C-d commonly is, see above for the effects.
       backward-delete-char (Rubout)
              Delete the character behind the cursor.  When given a numeric argument, 
              save the deleted text on the kill ring.
       forward-backward-delete-char
              Delete the character under the cursor, unless the cursor is at the end of the line, 
              in which case the character behind the cursor is deleted.
       quoted-insert (C-q, C-v)
              Add the next character that you type to the line verbatim.  
              This is how to insert characters like C-q, for example.
       tab-insert (M-TAB)
              Insert a tab character.
       self-insert (a, b, A, 1, !, ...)  
              Insert the character typed.
       transpose-chars (C-t)
              Drag the character before point forward over the character at point, moving point forward as well.  
              If point is at the end of the line, then this transposes the
              two characters before point.  Negative arguments have no effect.
       transpose-words (M-t)
              Drag the word before point past the word after point, moving point over that word as well.  
              If point is at the end of the line, this transposes the last two words
              on the line.
       upcase-word (M-u)
              Uppercase the current (or following) word.  With a negative argument, 
              uppercase the previous word, but do not move point.
       downcase-word (M-l)
              Lowercase the current (or following) word.  With a negative argument, 
              lowercase the previous word, but do not move point.
       capitalize-word (M-c)
              Capitalize the current (or following) word.  With a negative argument, 
              capitalize the previous word, but do not move point.
       overwrite-mode
              Toggle overwrite mode.  With an explicit positive numeric argument, switches to overwrite mode.  
              With an explicit non-positive numeric argument, switches to
              insert mode.  This command affects only emacs mode; vi mode does overwrite differently.  
              Each call to readline() starts in insert mode.  In overwrite mode,
              characters bound to self-insert replace the text at point rather than pushing the text to the right.  
              Characters bound to backward-delete-char replace the
              character before point with a space.  By default, this command is unbound.


##    Killing and Yanking
       kill-line (C-k)
              Kill the text from point to the end of the line.
       backward-kill-line (C-x Rubout)
              Kill backward to the beginning of the line.
       unix-line-discard (C-u)
              Kill backward from point to the beginning of the line.  The killed text is saved on the kill-ring.
       kill-whole-line
              Kill all characters on the current line, no matter where point is.
       kill-word (M-d)
              Kill from point the end of the current word, or if between words, to the end of the next word.  
              Word boundaries are the same as those used by forward-word.
       backward-kill-word (M-Rubout)
              Kill the word behind point.  Word boundaries are the same as those used by backward-word.
       unix-word-rubout (C-w)
              Kill the word behind point, using white space as a word boundary.  
              The killed text is saved on the kill-ring.
       unix-filename-rubout
              Kill the word behind point, using white space and the slash character as the word boundaries.  
              The killed text is saved on the kill-ring.
       delete-horizontal-space (M-\)
              Delete all spaces and tabs around point.
       kill-region
              Kill the text between the point and mark (saved cursor position).  This text is referred to as the region.
       copy-region-as-kill
              Copy the text in the region to the kill buffer.
       copy-backward-word
              Copy the word before point to the kill buffer.  The word boundaries are the same as backward-word.
       copy-forward-word
              Copy the word following point to the kill buffer.  The word boundaries are the same as forward-word.
       yank (C-y)
              Yank the top of the kill ring into the buffer at point.
       yank-pop (M-y)
              Rotate the kill ring, and yank the new top.  Only works following yank or yank-pop.

##    Miscellaneous
       re-read-init-file (C-x C-r)
              Read in the contents of the inputrc file, and incorporate any bindings or 
              variable assignments found there.
       abort (C-g)
              Abort the current editing command and ring the terminal's bell (subject to the setting of bell-style).
       do-uppercase-version (M-a, M-b, M-x, ...)
              If the metafied character x is lowercase, run the command that is bound to the corresponding 
              uppercase character.
       prefix-meta (ESC)
              Metafy the next character typed.  ESC f is equivalent to Meta-f.
       undo (C-_, C-x C-u)
              Incremental undo, separately remembered for each line.
       revert-line (M-r)
              Undo all changes made to this line.  This is like executing the undo command enough times to 
              return the line to its initial state.


### INPUTRC or BASHRC 
```bash
bind 'set colored-stats on'
```

````bash
# shellcheck shell=sh
## /etc/inputrc - global inputrc for libreadline
## See readline(3readline) and `info rluserman' for more information.

### https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Command-Line-Editing
## Keybinding (Control): \C
## Keybinding (Option): \e
## Keybinding (Command/Meta Left Side): \M
## (TAB): [Z
"\Cs": 'echo Control\015'
"\es": 'echo Option\015'
"\Ms": 'echo Command\015'

## https://github.com/iridakos/goto - Nov 2021
set colored-completion-prefix on

## https://hiltmon.com/blog/2013/03/12/better-bash-shell-expansion - Nov 2021
# makes symlinks look better
set mark-symlinked-directories on

## Avoid overwrite the line
# set horizontal-scroll-mode off

## De macos
set colored-stats on
set visible-stats on
set expand-tilde on
## This line sets the completions to be listed immediately instead of ringing the bell,
## when the completing word has more than one possible completion
set show-all-if-ambiguous on
## This line sets the completions to be listed immediately instead of ringing the bell,
## when the completing word has more than one possible completion but no partial completion can be made. Nov 2021
set show-all-if-unmodified on

## This line sets auto completion to ignore cases. Nov 2021
set completion-ignore-case on

## https://github.com/iridakos/goto
set colored-completion-prefix on

# Be 8 bit clean.
set input-meta on
set output-meta on

## To allow the use of 8bit-characters like the german umlauts, uncomment
## the line below. However this makes the meta key not work as a meta key,
## which is annoying to those which don't need to type in 8-bit characters.
set convert-meta off

## try to enable the application keypad when it is called.  Some systems
## need this to enable the arrow keys.
# set enable-keypad on

# see /usr/share/doc/bash/inputrc.arrows for other codes of arrow keys

## do not bell on tab-completion
# set bell-style none
# set bell-style visible

## https://hiltmon.com/blog/2013/03/12/better-bash-shell-expansion/ - Nov 2021
## Cycle completions one at a time instead of listing them all and requiring you to type characters
## until there’s only one match.
TAB: menu-complete

## https://brettterpstra.com/2011/09/25/quick-tip-some-inputrc-fun/ - Nov 2021
## SHIFT-TAB to complete in reverse (same as before in reverse)
"\e[Z": "\e-1\C-i"

### Option-z to go to previous directory and do an "ls".
## Keybinding (Option-z): \ez
## Command to run: 'cd -\015ls\015'
##    Return: \015 (after "cd -" and after "ls") so two commands are run.
"\ez": 'cd -\015ls\015'

### Option-x to go to the folder that was last argument in previous command.
###   i.e.: if I do "copy file.txt Desktop", then Option-X takes me to Desktop
## Keybinding (Option-x): \ex
## Command to run: 'cd !$\015ls\015'
##    cd !$ (last argument of previous command)
"\ex": 'cd !$\015ls\015'


### http://research.libd.org/rstatsclub/post/edit-your-bashrc-file-for-a-nicer-terminal-experience/#.YYUvHupKhhE - nov 2021
### History search (page up/page down)
##  cd /(option up and down to search in history of cd/)
#"\e[B": history-search-forward
#"\e[A": history-search-backward

## some defaults / modifications for the emacs mode
$if mode=emacs

  ## allow the use of the Home/End keys
"\e[1~": beginning-of-line
"\e[4~": end-of-line

  ## allow the use of the Delete/Insert keys
"\e[3~": delete-char
"\e[2~": quoted-insert

  ## mappings for "page up" and "page down" to step to the beginning/end
  ## of the history
# "\e[5~": beginning-of-history
# "\e[6~": end-of-history

  ## alternate mappings for "page up" and "page down" to search the history
#"\e[5~": history-search-backward
#"\e[6~": history-search-forward
"\C-p":history-search-backward
"\C-n":history-search-forward

  ### mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
  ## Keybinding (Option): \e
  ## Keybinding (right row): [1;5C
  ## Keybinding (left row): [1;5D
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

$if term=rxvt
"\e[7~": beginning-of-line
"\e[8~": end-of-line
"\eOc": forward-word
"\eOd": backward-word
$endif

  ## for non RH/Debian xterm, can't hurt for RH/Debian xterm
# "\eOH": beginning-of-line
# "\eOF": end-of-line

  ## for freebsd console
# "\e[H": beginning-of-line
# "\e[F": end-of-line

$endif

$if Bash
set colored-stats on
set visible-stats on
set colored-completion-prefix on
TAB: menu-complete
"\e[Z": "\e-1\C-i"

$endif

# Include other files
# $include /etc/inputrc

````

## DIRCOLORS

### [SYNTAX](https://linuxhint.com/ls_colors_bash/)
* KEY:CODE
* KEY:CODE;FG
* KEY:CODE;FG;BG
* KEY:CODE;FG;BG;NOT KNOE(Undlerline)

di=0:34  0 (normal), 34 (FG: green)
di=1:34  1 (bold), 34 (FG: green)
di=1:33:41  1 (bold), 33(FG: yellow) 34 (BG: red)

### KEYS
* **bd**: Block Device 
* **ca**: 
* **cd**: Character Device
* **di**: Directory
* **do**: 
* **ex**: Executable
* **fi**: Normal 
* **ln**: Link
* **mh**: 
* **no**: Global Default 
* **or**: Link (Broken)
* **ow**: 
* **pi**: 
* **sg**: 
* **so**: 
* **st**: 
* **su**: 
* **tw**: 

```bash
LS_COLORS="\
bd=38;5;68:\
ca=38;5;17:\
cd=38;5;113;1:\
di=38;5;30:\
do=38;5;127:\
ex=38;5;208;1:\
pi=38;5;126:\
fi=0:\
ln=target:\
mh=38;5;222;1:\
no=0:\
or=48;5;196;38;5;232;1:\
ow=38;5;220;1:\
sg=48;5;3;38;5;0:\
su=38;5;220;1;3;100;1:\
so=38;5;197:\
st=38;5;86;48;5;234:\
tw=48;5;235;38;5;139;3"
```
