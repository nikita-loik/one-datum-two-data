---
title: "VIRTUALENV"
date: 2020-12-07T00:00:00-00:00
categories:
  - blog
toc: true
toc_label: "Table of Contents"
toc_icon: "th-list"
tags:
  - shell script
  - virtual environment
  - python
  - makefile
---

## Prerequisits
Set-up macOS and install `pyenv` as described in [PIP my Env](https://nikita-loik.github.io/one-datum-two-data/blog/pip-my-env).
Set global version of python using `pyenv`.
```sh
pyenv global #.#.#
```

## Virtualenv Installation & Use
```shell
pip install virtualenv
virtualenv --version
```
Examples of the scripts and the Makefile are provided in [dummy/virtualenv_test](https://github.com/nikita-loik/dummy/tree/main/virtualenv_test).

|file|function|
|:-:|:-:|
|[get_virtualenv.sh](https://github.com/nikita-loik/dummy/blob/main/virtualenv_test/get_virtualenv.sh)|creates python virtual environment using virtualenv|
|[remove_virtualenv.sh](https://github.com/nikita-loik/dummy/blob/main/virtualenv_test/remove_virtualenv.sh)|removes python virtual environment using virtualenv|
|[Makefile](https://github.com/nikita-loik/dummy/blob/main/virtualenv_test/Makefile)|contains make commands to run the corresponding shell scripts|
|[test.py](https://github.com/nikita-loik/dummy/blob/main/virtualenv_test/test.py)|imports installed libraries, and reports whether the imports were successful|

**NB!** To make script executable, it may be necessary to change the [mode of the file][chmod-tutorial]:

```sh
chmod +x SCRIPT_PATH
```

To install virtual environment, run:
```sh
make venv_get
```
To test the installation was successful, run:
```sh
source .venv_virtualenv_test/bin/activate
python test.py
deactivate
```
To remove virtual environment, run:
```sh
make venv_remove
```

## Manage Requirements
Manually update and clean requirements stored in `requirements.txt`.
```shell
pip freeze > requirements.txt
```

[chmod-tutorial]: https://catcode.com/teachmod/