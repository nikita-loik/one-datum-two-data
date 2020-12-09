---
title: "Create Python Virtual Environment Using Shell Script and Makefile"
date: 2020-02-07T00:00:00-00:00
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
Set-up macOS and install `pyenv` as described in [ACT ONE](https://nikita-loik.github.io/one-datum-two-data/blog/pip-my-env).
Set global version of python using `pyenv`.

## Virtualenv Installation
```shell
pip install virtualenv
virtualenv --version
```

## Shell Script

Create a shell script `SCRIPT_PATH`.

```shell
# CREATE AND ACTIVATE VIRTUAL ENVIRONMENT =============================
# 1. Get working directory name (without full path).
dir_name=${PWD##*/}

# 2. Replace '-' with '_' in a name.
venv_stem="${dir_name//-/_}"

# 3. Get virtual environment name.
venv_name="venv_${venv_stem}"
echo "===creating virtual environment ${venv_name}==="

# 4. Create virtual environment.
virtualenv -p python3 ".${venv_name}"

# 5. Activate virtual environment.
source ".${venv_name}/bin/activate"

# 6. Upgrade pip.
pip install -U pip

# JUPYTER =============================================================
pip install jupyter

# KERNELS =============================================================
# IPython
python -m ipykernel install --user --name="${venv_stem}_py"

# REQUIREMENTS ========================================================
touch requirements.txt
pip install -r requirements.txt
echo "===virtual environment .${venv_name} created==="

# GIT =================================================================
# NB! To avoid cluttering .gitignore, add ignore statement to ./.git/info/exclude.
# 8. If doesn't exist, add virtual environment path to ./.git/info/exclude.
grep -qxF ".${venv_name}/" ../.git/info/exclude || echo ".${venv_name}/" >> ./.git/info/exclude
echo "===updated ./.git/info/exclude. with ".${venv_name}/"==="
```

**NB!** To make script executable, it may be necessary to change the [mode of the file][chmod-tutorial]:

```shell
chmod +x SCRIPT_PATH
```

## Makefile

```makefile
# 1 GET NAMES =========================================================

# 1.1 Get virtual-environment name.
VENV_NAME := $(wildcard .venv_*)

# 1.2 Get virtual-environment stem.
VENV_STEM := $(subst .venv_,,$(VENV_NAME))

# 1.3 Get kernel names from virtual-environment stem.
KERNEL_NAME_PY = "$(VENV_STEM)_py"

# =====================================================================

venv_get:
	get_virtualenv.sh

venv_remove:
	@echo "===removing virtual environment==="
	rm -rf $(VENV_NAME)

	@echo "===removing virtual iPython kernel==="
	rm -rf ~/Library/Jupyter/kernels/$(KERNEL_NAME_PY)
```

## Manage Requirements
Manually update and clean requirements stored in `requirements.txt`.
```shell
pip freeze > requirements.txt
```

[chmod-tutorial]: https://catcode.com/teachmod/