---
description: Bash/ZSH
---

# 💻 Shell

### links

Shortcuts - [https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac](https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac)

Explain Shell - [https://explainshell.com/explain?cmd=curl+-fsSL+example.org](https://explainshell.com/explain?cmd=curl+-fsSL+example.org)

More shortcuts - [http://macmy.ru/pages/terminal-commands-macosx#](http://macmy.ru/pages/terminal-commands-macosx)

Filesystem Hierarchy Standard - [https://ru.wikipedia.org/wiki/FHS](https://ru.wikipedia.org/wiki/FHS)

Database and OS scripting - [https://ss64.com/](https://ss64.com)

60 commands - [https://www.youtube.com/watch?v=gd7BXuUQ91w](https://www.youtube.com/watch?v=gd7BXuUQ91w)&#x20;

## Syntax

### man example

```bash
$ say [-v voice] [-r rate] [-o outfile [audio format options] | -n name:port | -a device] [-f file | string ...]

# one more
$ command [params...] [-options…] | command_two <param> [-options…]

# another example
$ cmd [param 1|param 2] 
```

Квадратные скобки `[]` обозначают необязательность. Например, опция `-v` необязательна, то же самое касается и любых других опций этой программы. Вертикальная черта `|` обозначает операцию "или", причём именно **исключающее или**. Посмотрите на последний блок `[-f file | string ...]`. Он означает, что `say` может либо произносить текст из файла, либо произносить строчку, переданную как аргумент, но не то и другое одновременно. Бывают и другие вариации описания способов вызова: значение по умолчанию, выбор из конкретных элементов, отрицание.

Значение опции указывается через пробел от самой опции. Если значение опции содержит в себе специальные или пробельные символы, то его нужно оборачивать в кавычки, двойные или одинарные - не важно.

#### params

Required parameters are written in angle brackets \<param> \
optional – in square brackets \[param]\
To indicate that a parameter can be repeated, ellipses are used \[params...]\
If only one of several parameters can be chosen, vertical bars are used: \[param 1|param 2]

#### options

_-options_ are **command line options** or **flags**, that modify the operation

### variables

```bash
TASK="project-1955"
TOKEN="bblablatoken64"
open https://main-url-$TASK.nl-k8s-stage.srv.local\?token=$TOKEN
```

## Buit in

To display all available built-in system commands, type `man builtin`\
__To quit manual press q,  f (forward),  b (backward).

```bash
# cd - change directory
cd {folder/path} 
cd ~/.ssh
cd ..
```

`pwd` - **p**rint **w**orking **d**irectory

`ls` - list directory contents

`stat` - display file or file system status

`hier` or `man hier` - layout of filesystems

`cat` - concatenate and print files

`grep` - (**g**lobal **r**egular **e**xpression **p**rint) searching

`touch` - file creating (not main function, but typical)

`env` - current shell env vars. [link](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)

#### pipe

&#x20;\| pipe - connect output first command to input next command

```bash
# copy public key to clipboard 
$ cat ~/.ssh/id_rsa.pub | pbcopy

# find keyword in ls results
$ ls ~/.ssh | grep digital
```

## Multiple commands in one line

<pre class="language-bash"><code class="lang-bash"># No matter the first command run successfully or not, run the second command cmd2:
<strong>$ cd; ls
</strong><strong># Only when the first command cmd1 run successfully, run the second command cmd2
</strong><strong>$ cd &#x26;&#x26; ls
</strong># Only when the first command cmd1 failed to run, run the second command cmd2
$ cd || ls
</code></pre>

### Renaming

```
touch file
mv file renamed-file
```

### Copy

```
cp renamed-file renamed-file-copy
```

### Deleting

`-r` recursion

`-f` all without question

```bash
rm folder/filename
rm -rf foder/foldername
```

### History

`Ctrl + r` fast history suggestions

## Permissions

Кроме имени пользователя и группы, с каждым файлом ассоциированы права доступа: **r** — чтение, **w** — запись и **x** — исполнение. Причём эти права задаются для трёх типов пользователей: владельца (Owner), пользователей, входящих в ту же группу (Group) и остальных (Other) — тех, кто не попал в предыдущие две.

![](<../.gitbook/assets/image (14).png>)

## **TLDR command**

**TLDR** stands for **T**oo **L**ong **D**idn'**t R**ead and is described as "a collection of simplified and community-driven man pages."

```
brew install tldr
tldr ls
tldr cd
```

## Aliases

```bash
# to save it in shell zsh - ~/.zshrc
nano ~/.bashrc
# add alias

# Add ssh key
alias key='ssh-add --apple-use-keychain ~/.ssh/id_rsa'

# save it

# add to current session
source ~/.bashrc
```

## Processes

```bash
```
