# User-defined programs

## therms

`#!` - "shebang". \
Directive for the Linux program loader that specifies a program that will run the script

`#!/usr/bin/env python3` - python example

## example

`hello_world.sh`

```no-highlight
#!/usr/bin/env bash
echo 'Hello, world!'
```

## Run a shell script <a href="#run-a-shell-script" id="run-a-shell-script"></a>

* open the corresponding directory with file and type `bash hello_world.sh`
* make the file executable by typing `chmod +x hello_world.sh`\
  Then can run it `./hello_world.sh`
