---
description: Bash/ZSH
---

# 💻 CLI

zsh & bash -  programs that runs in Terminal, interprets Unix commands, and interacts with OS

#### links

* Mac Shortcuts - [https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac](https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac)
* More shortcuts - [http://macmy.ru/pages/terminal-commands-macosx#](http://macmy.ru/pages/terminal-commands-macosx)
* Explain Shell - [https://explainshell.com/explain?cmd=curl+-fsSL+example.org](https://explainshell.com/explain?cmd=curl+-fsSL+example.org)
* Filesystem Hierarchy Standard - [https://ru.wikipedia.org/wiki/FHS](https://ru.wikipedia.org/wiki/FHS)
* Database and OS scripting - [https://ss64.com/](https://ss64.com)
* 60 commands - [https://www.youtube.com/watch?v=gd7BXuUQ91w](https://www.youtube.com/watch?v=gd7BXuUQ91w)&#x20;

## Syntax

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

Square brackets`[]` means optional. \
For 'say' program `-v` is an optional command like the others in example.

Pipe `|` means "OR" when there can only be one of two options. \
`[-f file | string ...]` it could be OR file OR string, not both

The value of an option is indicated by a space after the option value itself. If the option value contains special or space characters, it must be enclosed in quotation marks, double or single.

### params

Required parameters are written in angle brackets \<param> \
optional – in square brackets \[param]\
To indicate that a parameter can be repeated, ellipses are used \[params...]\
If only one of several parameters can be chosen, vertical bars are used: \[param 1|param 2]

### options

`--options` are **command line options** or **flags**, that modify the operation

short option `-o`

long `--option` (dash-dash-option)

### variables

```bash
TASK="project-1955"
TOKEN="bblablatoken64"
open https://main-url-$TASK.nl-k8s-stage.srv.local\?token=$TOKEN
```

## Permissions

```
drwx------    38 my.username  staff   1.2K Mar  4 13:07 .zsh_sessions
```

In addition to the user name and group, each file has associated access rights: r - read, w - write and x - execute. These permissions are set for three types of users: the Owner, users belonging to the same group (Group), and Other (those who are not included in the previous two groups).

![](<../../.gitbook/assets/image (14) (1).png>)

## Built-in commands

To display all available built-in system commands, type `man builtin`\
To quit manual press q,  f (forward),  b (backward).

```bash
# cd - change directory
cd {folder/path} 
cd ~/.ssh

# go home
cd
cd ~

# go up
cd ..

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
* `env` - current shell env vars. [link](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)
* `head` output the first part of textfiles
* `tail` - output the last part of textfiles
* `cp` & `mv` - copy & move. syntax - \<target file> \<destination>
* `compgen -c | less` - all available commands&#x20;

### History

stores in `.zsh_history` / `.bash_history`&#x20;

```bash
# show history
history

# clear history
history -c 
```

```bash
# create file and add text
echo "insert text here" > myfile.txt
```

#### pipe

&#x20;\| pipe - connect output first command to input next command

```bash
# copy public key to clipboard 
cat ~/.ssh/id_rsa.pub | pbcopy

# find keyword in ls results
ls ~/.ssh | grep digital

# check last commands in history
history | tail -20
```

### Multiple commands in one line

<pre class="language-bash"><code class="lang-bash"># No matter the first command run successfully or not, run the second command cmd2:
<strong>cd; ls
</strong><strong>
</strong><strong># Only when the first command cmd1 run successfully, run the second command cmd2
</strong><strong>cd &#x26;&#x26; ls
</strong><strong>
</strong># Only when the first command cmd1 failed to run, run the second command cmd2
cd || ls
</code></pre>

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

## Terminal Shortcuts

* `Ctrl + r`  → fast history search
* Ctrl+A → Go to front of line&#x20;
* Ctrl+E → Go to end of line dsfkjewi j
* Ctrl+C → Kill active process&#x20;
* Ctrl+K → Exit shell&#x20;
* Ctrl+L → Clear the screen&#x20;
* Ctrl+Z → Put process in bg&#x20;
* !! → Run previous command&#x20;
* ! → Run prev matching cmd&#x20;
* Ctrl+F → Go forward one character&#x20;
* Ctrl+x Ctrl+e → Open line in SEDITOR&#x20;
* Ctrl+B → Go back one character
* Alf+F → Go forward one word&#x20;
* Alt+B → Go back one word

## Shell Scripts

### Positional parameters

null parameter `$0` is always the name of the script, and then follows user parameters passed to a script

#### syntax

`$#` total number of the parameters

`$* , $@` - all parameters&#x20;

Example

.sh file

`personal_data.sh`

```bash
#!/usr/bin/env bash

echo "You provided $# facts about yourself!"
echo "Your name is $1"
echo "Your age is $2"
echo "All parameters in one var: $*"
echo "All parameters by words in var: $@"
```

run

```bash
bash personal_data.sh Pepe 13
>>
You provided 2 facts about yourself!
Your name is Pepe
Your age is 33
All parameters in line: Pepe 33
All parameters by words: Pepe 33
```

### Functions

#### syntax

`function function_name {}`&#x20;

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

## Shell config

* [https://github.com/ptrpl4/dotfiles](https://github.com/ptrpl4/dotfiles)

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

### PATH

`$PATH` environment variable. It sets the directories that the shell searches for executable files\
It's a list of directory paths, separated by colons (`:`)

`/bin` - default system executable files

`/usr/bin`  - default user executable files

`/usr/local/bin` - bins for manually installed user-apps (docker, WARP, etc)

`/opt/homebrew/bin` - created and maintained by Brew

```
# a default $PATH looks like
# search order from left /usr/local/bin to right /sbin
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

### alias - Aliases&#x20;

```bash
# to save it in shell zsh - ~/.zshrc
nano ~/.bashrc

# add alias, add ssh key, save file
alias key='ssh-add --apple-use-keychain ~/.ssh/id_rsa'

# reset shell environment
source ~/.bashrc
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

### **TLDR**

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
