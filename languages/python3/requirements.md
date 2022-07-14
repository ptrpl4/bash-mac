# requirements

## Using pip

```
# collect
pip freeze > requirements.txt
# install
pip install -r requirements.txt
# check outdated
pip list --outdated
# check missing
python -m pip check
# upgrade choosen
pip install -U PackageName
# upgrade all
pip install -U -r requirements.txt
```

example of requirements.txt

```
tensorflow==2.3.1
uvicorn==0.12.2
fastapi==0.63.0
```
