---
description: VCS - Version Control System
---

# 📖 Git

#### links

* [https://git-scm.com](https://git-scm.com/)
* [https://github.com/github/gitignore](https://github.com/github/gitignore)  .gitignore
* [https://ohshitgit.com](https://ohshitgit.com/)
* [https://gitexplorer.com](https://gitexplorer.com/)
* [https://blog.gitbutler.com](https://blog.gitbutler.com)

commits

* [https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)
* [https://conventionalcomments.org](https://conventionalcomments.org/)
* [https://www.youtube.com/watch?v=uBhpBOX8VYg](https://www.youtube.com/watch?v=uBhpBOX8VYg)

hints and examples

* [https://wiki.nikiv.dev/programming/version-control/git](https://wiki.nikiv.dev/programming/version-control/git)

## fast start

```bash
# init and connect repo
git init
git remote add origin git@github.com:ptrpl4/GitBookWiki.git

# create commit
git commit -a -m 'init commit'
# or 
git ci -am 'init commit'

# push to repo
git push
# or
git push origin master
```

## config

```bash
# check settings
git config --list --show-origin

# set global
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com

# set local
git config --local user.name "Pyotr V."
git config --local user.email ptrpl4@example.co

# add alias
git config --global alias.staash 'stash --all'
git config --global alias.script !any-script.sh
```

## .gitignore

The following rules apply to templates in the .gitignore file:&#x20;

* Blank lines, as well as lines starting with #, are ignored.&#x20;
* Standard templates are global and are applied recursively to the entire directory tree.&#x20;
* To avoid recursion use a slash (/) at the beginning of the template.&#x20;
* To exclude a directory add a slash (/) at the end of the template.&#x20;
* You can invert the template by using an exclamation point (!) as the first character.

## Basic commands

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### Add

<pre class="language-bash"><code class="lang-bash"># add --patch (parts of changes to commit)
<strong>git add -p index.html 
</strong></code></pre>

### Commit

```bash
# add all staged files to commit
git commit -a -m 'feat: add browser check'
# or
git ci -am 'feat: add browser check'
```

#### Semantic Commit Messages

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

### Push

```bash
# sent to remote repo origin master
git push

git push --force with lease
```

### Log

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

# Reference logs
git reflog
```

### Amend last commit

```bash
# add some chaged in last commit --amend
git commit -m 'Initial commit'
git add forgotten_file.md
git commit --amend
# if commit messg still actual
git commit --amend --no-edit

# example
git commit README.md --amend -m 'update instructions' 
```

### Remote

```shell
# check remote repos with links
git remote -v

# check remote repo info
git remote show origin

# connect origin repo to git
git remote add origin git@github.com:ptrpl4/GitBookWiki.git
```

### Fetch/Pull

```shell
# get data from origin repo
git fetch origin
# get + merge data from origin repo
git pull

# if unstashed changes
git stash save "Temporary changes"
git rebase
git stash pop
```

### Tag

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

## How to Rename

```bash
$ git mv README.md README
# equal
$ mv README.md README
$ git rm README.md
$ git add README
```

## How to Undo

```bash
# Unstaging a Staged File
git reset HEAD testfile.md

# Unmodifying a Modified File
git checkout -- CONTRIBUTING.md
```

## Branch

### Basics

```bash
# list of local branches
git branch --column

# create branch
git branch test_branch

# switch to branch
git checkout test_branch
# create and switch
git checkout -b test_branch

# delete branch (-d, --delete)
git branch -d test_branch
# local branches + last commits
git branch -v
# all not merged branches
git branch --no-merged
# all merged branches
git branch --merged
```

### renaming

```bash
# rename localy
$ git branch --move bad-branch-name corrected-branch-name
# push changes
$ git push --set-upstream origin corrected-branch-name
# delete branch
$ git push origin --delete bad-branch-name
```

## Merge

```bash
# add commit from test_branch to current branch
git merge test_branch
```

## Rebase

rebasing better to use only for local branches to not mess with changes in remote repo

```bash
# will rerite commit history
git merge test_branch
```

## Branching strategy

### GitHub Flow&#x20;

<figure><img src="../../.gitbook/assets/image (1) (5).png" alt=""><figcaption></figcaption></figure>

**long-live main branch + short-live feature branches**

### GitFlow

Gitflow is a legacy Git workflow that was originally a disruptive and novel strategy for managing Git branches. Gitflow has fallen in popularity in favor of trunk-based workflows, which are now considered best practices for modern continuous software development and DevOps practices

**develop => feature => develop => release branch => master + tag version**

<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

link&#x20;

* [https://nvie.com/posts/a-successful-git-branching-model](https://nvie.com/posts/a-successful-git-branching-model/)

