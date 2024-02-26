---
description: Bash/ZSH
---

# 💻 CLI

zsh & bash -  programs that runs in Terminal, interprets Unix commands, and interacts with OS

#### links

* Shortcuts - [https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac](https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac)
* Explain Shell - [https://explainshell.com/explain?cmd=curl+-fsSL+example.org](https://explainshell.com/explain?cmd=curl+-fsSL+example.org)
* More shortcuts - [http://macmy.ru/pages/terminal-commands-macosx#](http://macmy.ru/pages/terminal-commands-macosx)
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

## Buit in

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
```

* `pwd` - **p**rint **w**orking **d**irectory
* `ls` - list directory contents
* `stat` - display file or file system status
* `hier` or `man hier` - layout of filesystems
* `cat` - concatenate and print files
* `grep` - (**g**lobal **r**egular **e**xpression **p**rint) searching
* `touch` - file creating (not main function, but typical)
* `env` - current shell env vars. [link](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)
* `tail` - output the last part of files

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
</strong><strong># Only when the first command cmd1 run successfully, run the second command cmd2
</strong><strong>cd &#x26;&#x26; ls
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

### Delete

```bash
rm folder/filename

# -r recursion, -f all without question
rm -rf foder/foldername
```

### Shortcuts

`Ctrl + r`  - fast history search

## Permissions

Кроме имени пользователя и группы, с каждым файлом ассоциированы права доступа: **r** — чтение, **w** — запись и **x** — исполнение. Причём эти права задаются для трёх типов пользователей: владельца (Owner), пользователей, входящих в ту же группу (Group) и остальных (Other) — тех, кто не попал в предыдущие две.

![](<../../.gitbook/assets/image (14) (1).png>)

## Shell config

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

### PATCH

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

### Aliases

```bash
# to save it in shell zsh - ~/.zshrc
nano ~/.bashrc

# add alias, add ssh key, save file
alias key='ssh-add --apple-use-keychain ~/.ssh/id_rsa'

# reset shell environment
source ~/.bashrc
```

## Processes

```bash
# report a snapshot of the current processes
ps 

# turn off proccess
kill 123321
```

## **TLDR program**

**TLDR** stands for **T**oo **L**ong **D**idn'**t R**ead and is described as "a collection of simplified and community-driven man pages."

```bash
brew install tldr
tldr ls
tldr cd
```
