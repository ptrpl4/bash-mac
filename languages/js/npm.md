---
description: Node package manager
---

# NPM

### Links

* Official - [https://www.npmjs.com](https://www.npmjs.com/)

### Installation

**npm** is installed with **Node.js**

```
# install latest
npm install -g npm
# check version
npm -v
```

### Package.JSON

The content of package.json must be written in **JSON**.

At least two fields must be present in the definition file: **name** and **version**.

```
{
"name" : "foo",
"version" : "1.2.3",
"description" : "A package for fooing things",
"main" : "foo.js",
"keywords" : ["foo", "fool", "foolish"],
"author" : "John Doe",
"licence" : "ISC"
} 
```

### packages <a href="#about-packages" id="about-packages"></a>

A **package** is a file or directory that is described by a `package.json` file. A package must contain a `package.json` file in order to be published to the npm registry.

**Scoped** public packages belong to a user or organization and must be preceded by the user or organization name when included as a dependency in a `package.json` file:

* `@username/package-name`
* `@org-name/package-name`

### modules <a href="#about-modules" id="about-modules"></a>

A **module** is any file or directory in the `node_modules` directory that can be loaded by the Node.js `require()` function.

Since modules are not required to have a `package.json` file, not all modules are packages. Only modules that have a `package.json` file are also packages.
