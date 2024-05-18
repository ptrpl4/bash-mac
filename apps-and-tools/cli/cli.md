# 💻 CLI

zsh & bash -  programs that runs in Terminal, interprets Unix commands, and interacts with OS

#### links

* Mac Shortcuts - [https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac](https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac)
* More shortcuts - [http://macmy.ru/pages/terminal-commands-macosx#](http://macmy.ru/pages/terminal-commands-macosx)
* Explain Shell - [https://explainshell.com/explain?cmd=curl+-fsSL+example.org](https://explainshell.com/explain?cmd=curl+-fsSL+example.org)
* Filesystem Hierarchy Standard - [https://ru.wikipedia.org/wiki/FHS](https://ru.wikipedia.org/wiki/FHS)
* Database and OS scripting - [https://ss64.com/](https://ss64.com)
* 60 commands - [https://www.youtube.com/watch?v=gd7BXuUQ91w](https://www.youtube.com/watch?v=gd7BXuUQ91w)
- ShellCheck - https://www.shellcheck.net/
## Syntax

### comments

```bash
# one line

git status # inline

: '
long
comment
'
```

### man

SYNOPSIS - most common options
OPTIONS - full list of options

```bash
# man examples
say
[-v voice] 
[-r rate] 
[-o outfile [audio format options] | -n name:port | -a device] 
[-f file | string ...]

# one more
command [params...] [-options…] | command_two <param> [-options…]

# another example
cmd [param 1|param 2] 
```

Square brackets`[]` means optional

Pipe `|` means "OR" when there can only be one of two option

`[-f file | string ...]` it could be OR file OR string, not both

The value of an option is indicated by a space after the option value itself. If the option value contains special or space characters, it must be enclosed in quotation marks, double or single

### params

Required parameters are written in angle brackets \<param> \
optional – in square brackets \[param]\
To indicate that a parameter can be repeated, ellipses are used \[params...]
If only one of several parameters can be chosen, vertical bars are used: \[param 1|param 2]

### options

`--options` are **command line options** or **flags**, that modify the operation

short option `-o`

long `--option` (dash-dash-option)

### variables

[how-to-read-and-set-vars](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)

```bash
# set
MY_TASK="project-1955"
TOKEN="bblablatoken64"

# check value
echo $TASK

# usage
open https://main-url-$MY_TASK.nl-k8s-stage.srv.local\?token=$TOKEN

# unset
unset MY_TASK

# check shell vars
set | less

# covert to env var
export TASK

# check env vars
printenv | less
```

### pipe

| pipe - connect output first command to input next command

```bash
# copy public key to clipboard 
cat ~/.ssh/id_rsa.pub | pbcopy

# find keyword in ls results
ls ~/.ssh | grep digital

# check last commands in history
history | tail -20

# grep all with "m"
echo -e "Hmm...\nBrr...\nMmm..." | grep "m"
```

### math

#### Arithmetic operators

| Op. | Function       | Description                                    | Example    | Result |
| --- | -------------- | ---------------------------------------------- | ---------- | ------ |
| +   | Addition       | Add two operands                               | $((10+3))  | 13     |
| -   | Subtraction    | Subtract two operands                          | $((10-3))  | 7      |
| *   | Multiplication | Multiply two operands                          | $((10*3))  | 30     |
| /   | Division       | Return quotient after division                 | $((10/3))  | 3      |
| %   | Modulo         | Return remainder after division                | $((10%3))  | 1      |
| **  | Exponential    | Raise the first operand to the power of second | $((10**3)) | 1000   |

```bash
#!usr/bin/env/bash

#Executing simple arithmetic operations
echo $(( 10*5+15 ))
echo $(( 40/6 ))
```

#### Operations with a variable
| Operator | Function                   | Description                     | Example     | Result |
| -------- | -------------------------- | ------------------------------- | ----------- | ------ |
| +=       | Addition by constant       | Add two operands                | $((_x_+=3)) | 13     |
| -=       | Subtraction by constant    | Subtract two operands           | $((_x_-=3)) | 7      |
| *=       | Multiplication by constant | Multiply two operands           | $((_x_*=3)) | 30     |
| /=       | Division by constant       | Return quotient after division  | $((_x_/=3)) | 3      |
| %=       | Modulo by constant         | Return remainder after division | $((_x_%=3)) | 1      |

```bash
#!usr/bin/env/bash

# Assigning value to variables
val1=$(( 10*3-15 ))
echo $val1

# Arithmetic operations using constants
# both `val=$(( 2 ))` and `$(( val = 2 ))` to assign values to vars
echo $(( val1 *= 3 ))
```


#### Relational and logical operations

`bc` utility provides us the ability to work with previously described operators as well as:
- Relational operators
- Logical or Boolean operators
- Math functions
- Conditional statements
- Iterative statements

| Op. | Example       | Evaluation logic                  | Result |
| --- | ------------- | --------------------------------- | ------ |
| &&  | bc <<< "5&&6" | 1; if all operands are non-zero   | 1      |
| \|  | bc <<< "5\|6" | 1; if any one operand is non-zero | 1      |
| !   | bc <<< "!5"   | 1; if the operand is 0            | 0      |

```bash
#!usr/bin/env/bash

# syntax command argument <<< "input"
# Less than operator
bc <<< "10 < 1"

# Is not equal to operator
bc <<< "10 != 11"
```

#### Math library

option `-l` enables the standard math library

| Math func. | Explanation                                                        | Example             |
| ---------- | ------------------------------------------------------------------ | ------------------- |
| sine       | Takes radian value as operand and gives its sine value             | bc -l <<< "s(30)"   |
| cosine     | Takes radian value as operand and gives its cosine value           | bc -l <<< "c(30)"   |
| tan-1      | Gives the inverse tangent in radians                               | bc -l <<< "a(1)"    |
| _ln_       | Gives the natural logarithm                                        | bc -l <<< "l(45)"   |
| _e_        | Raises _e_(euler's number i.e. 2.7182) to the power of the operand | bc -l <<< "e(1)"    |
| √          | Returns square root value                                          | bc -l <<< "sqrt(9)" |

```bash
#!usr/bin/env/bash

#Arithmetic operation that returns a floating-point number
bc -l <<< "(1 + 2)/7 * 2 ** 2"

#Using sine and cosine functions
bc -l <<< "s(1) + c(1)"

#Using logarithmic and exponential functions
bc -l <<< "e(1) + l(5)"

#Finding the square root of a number
bc -l <<< "sqrt(27)"

#Converting binary 10 to octal
bc -l <<< "ibase=2; obase=8; 10"

#Converting decimal 5 to binary
bc -l <<< "obase=2; 5"

#Using scale to control length of floating-point numbers
bc -l <<< "scale=3; a(30)"
```

## Permissions

```
drwx------    38 my.username  staff   1.2K Mar  4 13:07 .zsh_sessions
```

In addition to the user name and group, each file has associated access rights: r - read, w - write and x - execute. These permissions are set for three types of users: the Owner, users belonging to the same group (Group), and Other (those who are not included in the previous two groups).

![](../../aaa-assets/cli-2.png)

## Built-in commands

To check all available built-in system commands, type `man builtin`
To quit manual press q, f (forward), b (backward).

```bash
# cd - change directory
cd {folder/path} 
cd ~/.ssh

# go home
cd
cd ~

# go up
cd ..
cd ../../../

# go root
cd /

# go to previous dir
cd -

# ls - list directory contents

# l-longList a-all t-sortByTime r-sortReverse h-humanReadable
ls -latrh
```

* `pwd` - **p**rint **w**orking **d**irectory
* `stat` - display file or file system status
* `hier` or `man hier` - layout of filesystems
* `cat` - concatenate and print files
* `grep` - (**g**lobal **r**egular **e**xpression **p**rint) searching
* `touch` - file creating (not main function, but typical)
* `env` - current shell env vars
* `head` output the first part of textfiles
* `tail` - output the last part of textfiles
* `cp` & `mv` - copy & move. syntax - \<target file> \<destination>
* `compgen -c | less` - all available commands
* `file` - description of the type of the specified file. Works fine for files with no file extension

### History

stores in `.zsh_history` / `.bash_history`

```bash
# show history
history

# clear history
history -c 
```

### Navigation

```bash
# add dir to stack
pushd

# check stack list
dirs -v

# delete 0 dir from stack and open it
popd
```

### Multiple commands in one line

```bash
# No matter the first command run successfully or not, run the second command cmd2:
cd; ls

# Only when the first command cmd1 run successfully, run the second command cmd2
cd && ls

# Only when the first command cmd1 failed to run, run the second command cmd2
cd || ls
```

### Rename

```bash
# rename
touch file
mv file renamed-file

# make copy
cp renamed-file renamed-file-copy
```

### rm - Delete

```bash
rm folder/filename

# -r recursion, -f all without question
rm -rf foder/foldername
```

### eval

execute a string as a shell command

```bash
# example
command="echo \$(date)"
eval "$command"
```

### File redirections

`>>` appends new content to the file without removing the old information.

```bash
# adding new information to a diary
echo "Also my favorite things are ..." >> diary.txt
```

`>` overwrites the file, removing any old content.

```bash
# rewrite/create file content
echo "My new everlasting love is ..." > secret.txt
```

#### stdout, stderr redirections

```bash
# program.sh
echo "Just a normal message"
echo "it will goes to stdout"
# >&2 directs the "ERROR!" message to stderr, represented by descriptor 2
echo "ERROR!" >&2
echo "one more error" >&2
echo "it will goes to stdout too"
echo "one last error" >&2
```

```bash
# 1> redirects all stdout (non-error) output to file
# 2> redirects all stderr output to file
bash program.sh 1> log.txt 2> errors.txt
```

## Terminal Shortcuts

* Ctrl+R → fast history search
* Ctrl+A → Go to front of line
* Ctrl+E → Go to end of line
* Ctrl+C → Kill active process
* Ctrl+K → Exit shell
* Ctrl+L → Clear the screen
* Ctrl+Z → Put process in bg
* !! → Run previous command
* ! → Run prev matching cmd
* Ctrl+F → Go forward one character
* Ctrl+x Ctrl+e → Open line in SEDITOR
* Ctrl+B → Go back one character
* Alf+F → Go forward one word
* Alt+B → Go back one word
### Nano
- Ctrl+K → delete a line

## Shell Scripts

### Therms

`#!` - "shebang"
Directive for the Linux program loader that specifies a program that will run the script

`#!/usr/bin/env python3` - python example

### Run a script

* open the corresponding directory with file and type `bash hello_world.sh`
* make the file executable by typing `chmod +x hello_world.sh`
  Then can run it `./hello_world.sh`

### Positional parameters

null parameter `$0` is always the name of the script, and then follows user parameters passed to a script

Syntax

`$#` total number of the parameters
`$* , $@` - all parameters

Example
`personal_data.sh`

```bash
#!/usr/bin/env bash

echo "You provided $# facts about yourself!"
echo "Your name is $1"
echo "Your age is $2"
echo "All parameters in one var: $*"
echo "$@" # All arguments passed to the script
```

run

```bash
$ bash personal_data.sh Pepe 13

stdout:
You provided 2 facts about yourself!
Your name is Pepe
Your age is 33
All parameters in line: Pepe 33
All parameters by words: Pepe 33
```

### Functions

syntax

`function function_name {}`
or
`function_name() {}`

example

```bash
#!/usr/bin/env bash

personal_data() {
    echo "You provided $# facts about yourself!"
    echo "Your name is $1"
    echo "Your age is $2"
}

personal_data "Elden Lord" 200026
```

### Case statement

case statement is easy to read when there are multiple conditional statements

```bash
#!/usr/bin/env bash

# if example

if [[ "${1}" == "" ]]; then
	echo "No option was selected."

elif [[ "${1}" == "1" ]]; then
	echo "You selected '1'."

elif [[ "${1}" == "2" ]]; then
	echo "You selected '2'."

elif [[ "${1}" == "3" ]]; then
	echo "You selected '3'."
    
else
	echo "Unknown number '${1}'."

fi

# same logic using case statement

case "${1}" in

    "")       # condition 
        echo "No option was selected." 
        ;; # end of the command
    1)     
        echo "You selected '1'." 
        ;;
    2)     
        echo "You selected '2'." 
        ;;
    3)     
        echo "You selected '3'." 
        ;;
    *)     # default case == else
        echo "Unknown number '${1}'." 
        ;;

esac

# syntax example
case $variable in
    condition-1 )
        commands;;
    condition-2 )
        commands;;
    condition-3 )
        commands;;
    condition-N )
        commands;;
    * )
        commands;;
esac

```


### Shift statement

`shift` - command that helps to iterate within list of arguments in function. like `i++` statement

example

```bash
#!/usr/bin/env bash

answers=("a" "d" "c" "a" "a")
total_score=0

for (( i = 0; i < 5; i++));
do
    case "${1}" in

        ${answers[i]})
            ((total_score++))
            ;;
        "-"|"--") # `|` bitwise operator 'OR'
            ;;
        *)
            ((total_score--))
            ;;

    esac
    shift 1 ## equal i + 1
done

echo "Total score is: $total_score"
```

### if-statement

```bash
# syntax
if [conditions]; then
   commands
fi

```

### Error handling

default, bash does not halt the execution of the script. 
if any command in the pipeline fails (returns a non-zero exit status), the entire pipeline is considered to have failed, even if some commands in the pipeline were successful

`set -euo pipefail` # shell options
	-exit on error
	-undefined vars caused exit
	-output will show last successful command 

## Shell config

* [https://github.com/ptrpl4/dotfiles](https://github.com/ptrpl4/dotfiles)

![](../../aaa-assets/cli-1.png)

### PATH

`$PATH` environment variable. It sets the directories that the shell searches for executable files
It's a list of directory paths, separated by colons (`:`)

`/bin` - default system executable files

`/usr/bin`  - default user executable files

`/usr/local/bin` - bins for manually installed user-apps (docker, WARP, etc)

`/opt/homebrew/bin` - created and maintained by Brew

```bash
# a default $PATH looks like
# search order from left /usr/local/bin to right /sbin
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin

# update PATCH data for current shell session
PATH=$PATH:/path-to-your-directory
export PATH
```

### alias - Aliases

```bash
# to save it in shell zsh - ~/.zshrc
nano ~/.bashrc

# add alias, add ssh key, save file
alias key='ssh-add --apple-use-keychain ~/.ssh/id_rsa'
alias any-key='any-thing'

# reset shell environment
source ~/.bashrc

# check current list of aliases
alias

# to remove (for aliases added by command, not file)
unalias key
```

## OS programs

### ps - Processes

```bash
# report a snapshot of the current processes
ps 

# turn off proccess
kill 123321
```

### MacOS - softwareupdate

```bash
/usr/sbin/softwareupdate

# list
softwareupdate -l

# update all -R => restart if needed (sudo for -R option)
sudo softwareupdate -i -a -R
```

## Third-party programs

### TLDR

**TLDR** stands for **T**oo **L**ong **D**idn'**t R**ead -  a collection of simplified and community-driven man pages.

```bash
brew install tldr
tldr ls
tldr git
```

### Sublime

```bash
brew install sublime-text

# open current dir
subl .


# sublime merge
brew install sublime-merge

# open dir
smerge .
```

### htop

user friendly top command

```bash
brew install htop
```

### **fonts**

```bash
# for mac
brew tap homebrew/cask-fonts
brew install --cask font-fira-code
```

### gping

for debugging multiple hosts at once

```bash
brew install gping
gping 1.1.1.1 8.8.8.8 192.168.100.1 192.168.100.38
```

source - [https://t.me/zhovner\_hub/1991](https://t.me/zhovner\_hub/1991)