# Make

## Links

[https://www.gnu.org/software/make/manual/make.html](https://www.gnu.org/software/make/manual/make.html) \
[https://opensource.com/article/18/8/what-how-makefile](https://opensource.com/article/18/8/what-how-makefile)

## Make

Utility Make is a build automation tool that automatically builds executable programs and libraries from source code by reading files called _makefiles_

## makefile

structure

```makefile
target … : prerequisites …
        recipe
        …
        …
```

example

```makefile
say_hello:
        @echo "Hello World"

generate:
        @echo "Creating empty text files..."
        touch file-{1..10}.txt

clean:
        @echo "Cleaning up..."
        rm *.txt
```

```makefile
install:
	pip3 install -r ./requirements.txt
run-locally:
	python3 ./webserver.py
```

run

```bash
# run target
$ make say_hello
$ make install
$ make run-locally
```
