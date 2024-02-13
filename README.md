# Example Package

This is a simple example package. You can use
[GitHub-flavored Markdown](https://guides.github.com/features/mastering-markdown/)
to write your content.


## Install

Install these first:

```
python3 -m pip install --upgrade pip
pip install --upgrade setuptools build twine
```

## Create (Test) PyPI Account Token

```
$HOME/.pypirc

[testpypi]
  username = __token__
  password = pypi-xxxxx

```

## Generate distribution archive

From the same directory as the `pyproject.toml` file run:

```
python3 -m build
```

The tar.gz file is a source distribution whereas the .whl file is a built distribution.

```
pycowsay_tutorial/dist/
├── pycowsay_tutorial-0.0.1-py3-none-any.whl
└── pycowsay_tutorial-0.0.1.tar.gz
```
## Upload the distribution archive

```
python3 -m twine upload --repository testpypi dist/*
```

## Create Entry Points

Now, suppose that we would like to provide some way of executing the function hello_world() from the command-line. 

One way to do this is to create a file `src/pycowsay/__main__.py` providing a hook as follows:

```
from . import hello_world

if __name__ == '__main__':
    hello_world()
```
Better though is:

```
pyproject.toml

[project.scripts]
cowsay = "pycowsay.main:main"
```

```
$ cowsay Hi

  --
< Hi >
  --
   \   ^__^
    \  (oo)\_______
       (__)\       )\/\
           ||----w |
           ||     ||

```

## pip install -e

When you're still developing your project, you can install a local version using the `-e` flag.




## The 5 links:

Official Python Tutorial :: Packaging Python projects
This tutorial walks you through how to package a simple Python project
Uses SETUPTOOLS under the hood
https://packaging.python.org/en/latest/tutorials/packaging-projects/

SETUPTOOLS :: Packaging Python projects
This tutorial walks you through how to package a simple Python project, the SETUPTOOLS way
https://setuptools.pypa.io/en/latest/userguide/index.html

Pipx :: Install and Run Python Applications in virtual environments without needing to first activate the virtual environment.
Apparantely the world's been using pipx this whole time and I just didn't notice.
https://pypi.org/project/pipx/

Cookiecutter :: Probably the best python package for creating python packages
Created by the author of Two Scoops of Django 
https://github.com/cookiecutter/cookiecutter
```
> cookiecutter $cookiecutter_template
> cookiecutter https://github.com/audreyfeldroy/cookiecutter-pypackage # Thorough. The doc-u-men-tation! Schews to an older SETUPTOOLS layout.
> cookiecutter https://github.com/cookiecutter/cookiecutter-django     # Wow
```

PPW :: Cookiecutter fork, endorsed by Cookiecutter.
https://zillionare.github.io/python-project-wizard/

----------------------------------------------------------



