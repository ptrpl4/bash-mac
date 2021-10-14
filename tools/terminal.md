# Command line

Shortcuts - [https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac](https://support.apple.com/guide/terminal/keyboard-shortcuts-trmlshtcts/mac)

Explain Shell - [https://explainshell.com/explain?cmd=curl+-fsSL+example.org](https://explainshell.com/explain?cmd=curl+-fsSL+example.org)

More shortcuts - [http://macmy.ru/pages/terminal-commands-macosx#](http://macmy.ru/pages/terminal-commands-macosx#)

Filesystem Hierarchy Standard - [https://ru.wikipedia.org/wiki/FHS](https://ru.wikipedia.org/wiki/FHS)

Database and OS scripting - [https://ss64.com/](https://ss64.com)

Terminal - приложение для macOS, позволяющее взаимодействовать со средой выполнения команд (bash по умолчанию для macOS).

Через Terminal можно решать задачи для которых обычно требуются программы с графическим интерфейсом.

## Commands syntax

### model

У команд бывают _аргументы_ и _опции_ (их также называют флагами). Например, в команде `ls Music`, `Music` — это аргумент, а вот в команде `ls -a`, `-a` — это опция. Опции всегда начинаются с одного или двух дефисов.

Опции можно комбинировать. Чтобы вывести все файлы, включая скрытые, с подробным описанием, нужно набрать `ls -a -l`. Bash позволяет объединять опции и писать так `ls -al` или даже так `ls -la`.

```bash
$command [params.z..] [-options…]
```

_params_ are **command parameters**\
****_-options_ are **command line options** or **flags**,  that modify the operation

Options may also start with a double hyphen(--). \
Usually, options starting with single hyphen have abbreviated names, like _-a_ or _-R_, while options starting with double hyphen have full names, like _--version_ or _--help_. \
Command line syntax is **case-sensitive**.

In command manuals, required parameters are written in angle brackets _\<param>_, and optional ones – in square brackets _\[param]_. To indicate that a parameter can be repeated, ellipses are used _\[params...]_. \
If only one of several parameters can be chosen, vertical bars are used: _\[param 1|param 2]_.

To display all available built-in system commands, type _man builtin_ 

**To quit manual, press **_**q**_**.**

`man command`\
Для выхода из режима просмотра нажмите q, для просмотра вперёд f (forward), назад — b (backward).

```bash
cd {folder/path} 
cd ..
```

`pwd` - **p**rint **w**orking **d**irectory

`cd`  - **c**hange **d**irectory

`ls` - list directory contents

`stat `- display file or file system status

`hier` or `man hier `- layout of filesystems

`cat` -- concatenate and print files

`grep` - (**g**lobal **r**egular **e**xpression **p**rint) searching 

`touch `- file creating (not main function, but typical)

## Manual

```bash
$say [-v voice] [-r rate] [-o outfile [audio format options] | -n name:port | -a device] [-f file | string ...]
```

Квадратные скобки `[]` обозначают необязательность. Например, опция `-v` необязательна, то же самое касается и любых других опций этой программы. Вертикальная черта `|` обозначает операцию "или", причём именно **исключающее или**. Посмотрите на последний блок `[-f file | string ...]`. Он означает, что `say` может либо произносить текст из файла, либо произносить строчку, переданную как аргумент, но не то и другое одновременно. Бывают и другие вариации описания способов вызова: значение по умолчанию, выбор из конкретных элементов, отрицание.

Значение опции указывается через пробел от самой опции. Если значение опции содержит в себе специальные или пробельные символы, то его нужно оборачивать в кавычки, двойные или одинарные - не важно.

Когда мы запускали `man`, то перед нами открывался `less` с загруженным туда контентом.

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

```
rm -rf one
```

### History

`Ctrl + r` fast history suggestions

Permissions

Кроме имени пользователя и группы, с каждым файлом ассоциированы права доступа: **r** — чтение, **w** — запись и **x** — исполнение. Причём эти права задаются для трёх типов пользователей: владельца (Owner), пользователей, входящих в ту же группу (Group) и остальных (Other) — тех, кто не попал в предыдущие две. 

![](<../.gitbook/assets/image (14).png>)

