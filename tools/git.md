---
description: version control system
---

# 📖 Git

## links

[https://git-scm.com/](https://git-scm.com/)&#x20;

[https://github.com/github/gitignore](https://github.com/github/gitignore)  .gitignore

[https://ohshitgit.com/](https://ohshitgit.com/)

[https://gitexplorer.com/](https://gitexplorer.com/) &#x20;

commits:

[https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)

[https://conventionalcomments.org/](https://conventionalcomments.org/)

[https://www.youtube.com/watch?v=uBhpBOX8VYg](https://www.youtube.com/watch?v=uBhpBOX8VYg) \


### fast start

```bash
git commit -a -m "init commit"
git push
```

## config

```bash
# check settings
git config --list --show-origin

# set global
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com

# set local
git config --local user.name "Petr V."
git config --local user.email ptrpl4@ya.ru
```

## Add

<pre class="language-bash"><code class="lang-bash"># add --patch (parts of changes to commit)
<strong>git add -p index.html 
</strong></code></pre>

## Commit

```bash
# add all staged files to commit
git commit -a -m "text"
```

### Semantic Commit Messages

Format: `<type>(<scope>): <subject>`

`<scope>` is optional

```
feat: add hat wobble
^--^  ^------------^
|     |
|     +-> Summary in present tense.
|
+-------> Type: chore, docs, feat, fix, refactor, style, or test.
```

More Examples:

* `feat`: (new feature for the user, not a new feature for build script)
* `fix`: (bug fix for the user, not a fix to a build script)
* `docs`: (changes to the documentation)
* `style`: (formatting, missing semi colons, etc; no production code change)
* `refactor`: (refactoring production code, eg. renaming a variable)
* `test`: (adding missing tests, refactoring tests; no production code change)
* `chore`: (updating grunt tasks etc; no production code change)

## Push

```bash
# sent to remote repo origin master
git push
```

## .gitignore

К шаблонам в файле .gitignore применяются следующие правила:

* Пустые строки, а также строки, начинающиеся с #, игнорируются.
* Стандартные шаблоны являются глобальными и применяются рекурсивно для всего дерева каталогов.
* Чтобы избежать рекурсии используйте символ слеш (/) в начале шаблона.
* Чтобы исключить каталог добавьте слеш (/) в конец шаблона.
* Можно инвертировать шаблон, использовав восклицательный знак (!) в качестве первого символа.

## Переименование

```bash
$ git mv README.md README
# equal
$ mv README.md README
$ git rm README.md
$ git add README
```

## Лог

```shell
# all commits order by desc
git log
# show patch -p or --patch
git log -p -2
# short changed info --stat
git log --stat
# change view for data --pretty
git log --pretty
# additional options for --pretty
git log --pretty=oneline
# another addotional opt. - =short, =full, =fuller
# time options
git log --since=2.weeks
# serach for string -S
git log -S function_name
# commits related to specific file -- path/to/file
git log -- path/to/file
# exclude merges --no-merges
git log --no-merges
# branches and changes
git log --oneline --decorate
```

## Добавление в последний коммит

```bash
# add some chaged in last commit --amend
git commit --amend
# example
git commit README.md --amend -m 'update instructions'             
```

## Отмена индексации

```
git reset HEAD filename
```

## Отмена изменений

```
git checkout -- filename
```

## Remote

```shell
# check remote repos with links
$ git remote -v
# check remote repo info
git remote show origin
```

## Fetch/Pull

```shell
# get data from origin repo
git fetch origin
# get + merge data from origin repo
git pull 
```

## Tag

```shell
# create Annotated Tags (full author info) and message
$ git tag -a v1.4 -m "my version 1.4"
$ git show v1.4
# Lightweight Tags (only tag info)
$ git tag v1.4-lw
# add tag to already created commit
$ git tag -a v1.2 9fceb02dfs22f332d
# push choosen tag to remote
$ git push origin <tagname>
# push all tags
$ git push --tags
# delete tag
$ git tag -d v1.4
# delete from remote
$ git push origin --delete <tagname>
# check tag file (not recommended)
$ git checkout v2.0.0
# create branch with tag (recommend)
$ git checkout -b version2 v2.0.0
```

## Branch

### basic

```bash
# current branches
git branch
# create branch
git branch test_branch
# switch to branch
git checkout test_branch
# create and switch
git checkout -b test_branch
# delete branch (-d, --delete)
git branch -d test_branch
# all branches + all last commits
git branch -v
# all not merged branches
git branch --no-merged
# all merged branches
git branch --merged
```

### renaming

```
# rename localy
$ git branch --move bad-branch-name corrected-branch-name
# push changes
$ git push --set-upstream origin corrected-branch-name
# delete branch
$ git push origin --delete bad-branch-name
```

## Merge

```
# add test_branch to current branch
git merge test_branch
```

### Branching strategy

### GitHub Flow&#x20;

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

long-live main branch + short-live feature branches

### GitFlow

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

develop => feature => develop => release branch => master + tag version

link - [https://nvie.com/posts/a-successful-git-branching-model](https://nvie.com/posts/a-successful-git-branching-model/)

