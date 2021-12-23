# Configs

CLI usage

```
# detailed output (-v)
$ python -m pytest --verbose
# only imortant data (-q)
$ python -m pytest --quiet
# stop after fail (--maxfail=1)
$ python -m pytest --exitfirts
# create report
$ python -m pytest --junit-xml report.xml
```

Config files

link [https://docs.pytest.org/en/stable/customize.html](https://docs.pytest.org/en/stable/customize.html)

Example - pytest.ini&#x20;

```
[pytest]
minversion = 6.0
addopts = -ra -q
testpaths =
    tests
    integration
```
