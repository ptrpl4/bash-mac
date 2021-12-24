# macOS Hints

## python2=>python3 transition

Until we have preinstalled python2 in macOS...

Just add two new lines to zsh configuration file

```
$ echo "alias pip=/usr/bin/pip3" >> ~/.zshrc  
$ echo "alias python=/usr/bin/python3" >> ~/.zshrc
# and check results
$ python --version && pip --version  
```

! check path before changing

How to use an old one?

pip - no way!

python2 - $ \python
