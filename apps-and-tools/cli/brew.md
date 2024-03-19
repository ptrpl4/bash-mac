---
description: The Missing Package Manager for macOS (or Linux)
---

# 🍻 HomeBrew

### links

* man [https://docs.brew.sh/Manpage](https://docs.brew.sh/Manpage)

### Install Brew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

or [https://github.com/Homebrew/brew/releases/latest](https://github.com/Homebrew/brew/releases/latest)

### Add to shell

<pre class="language-bash"><code class="lang-bash"><strong>(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> ~/.zshrc
</strong></code></pre>

### Where to find

Homebrew installs packages to their own directory and then symlinks their files

* /opt/homebrew on Apple Silicon
* /usr/local/bin/brew and /usr/local/Homebrew on Intel

```bash
# mac Apps
brew --caskroom
/opt/homebrew/Caskroom

# installed packages (symlinks to /bin)
brew --cellar
/opt/homebrew/Cellar
```

### Commands

```sh
# help
brew commands

# install
brew install wget
brew install --cask firefox

brew rm wget
brew rm --cask firefox

# manage
brew update
brew outdated
brew upgrade --formula
brew upgrade --cask

brew list
brew list --formula
brew list --cask

# check deps
brew uses --installed node

# a diagram of packages and dependencies
brew deps --tree --installed

# cleanup
# get list dependencys of another formulano longer needed
brew autoremove -n
brew cleanup
```

### Completion

* [https://docs.brew.sh/Shell-Completion#configuring-completions-in-zsh](https://docs.brew.sh/Shell-Completion#configuring-completions-in-zsh)

```bash
if type brew &>/dev/null
then
  FPATH="$(brew --prefix)/share/zsh/site-functions:${FPATH}"

  autoload -Uz compinit
  compinit
fi
```

### Helpers

```bash
# List packages sorted by creation date (installation date)
find "$(brew --cellar)" -type d -maxdepth 0 | xargs ls -ltU
```
