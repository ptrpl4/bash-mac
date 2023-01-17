---
description: Asynchronous event-driven JavaScript runtime
---

# Node

### Links

* Docs - [https://nodejs.org/en/](https://nodejs.org/en/)
* n - [https://github.com/tj/n](https://github.com/tj/n)
* how to update node - [https://guillermo.at/update-node-proper-way](https://guillermo.at/update-node-proper-way)

### Manage Node versions

#### with n

```
# install with n (Node.js version management)
npm install -g n
# install node with n
n lts # note! on macOS you probably should change app directory to avoid r/w restrictions
```

#### with nvm

```bash
# install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
# check
nvm --version
# instal node stable/latest/16/18/lts
nvm install stable
# check installed
nvm ls
# choose installed
nvm use 16
```

\
\
