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

While very effective as a tool, it can be fairly laborious to create [python virtual environment][hitchhikers-guide-virtual-environments] for every project on every computer.

To simplify this tedious task a simple shell script combined with [makefile][exhaustive-make-reference] can be used.

## Shell Script

```shell
#!/bin/zsh
# 1. Get virtual environment name.
# 1.1. Get working directory name (without full path).
dir_name=${PWD##*/}
# 1.2. Replace '-' with '_' in a name.
venv_stem="${dir_name//-/_}"
# 1.3. Get virtual environment name.
venv_name="venv_${venv_stem}"
echo "===creating virtual environment ${venv_name}==="

# 2. Create virtual environment.
virtualenv -p python3 ".${venv_name}"

# 3. Activate virtual environment.
source ".${venv_name}/bin/activate"

# 4. Install jupyter.
pip install jupyter

# 5. Install IPython kernel.
python -m ipykernel install --user --name="${venv_name}"

# 6. Install requirements.
# 6.1. Make an empty file requirements.txt if doesn't exist.
touch requirements.txt
# 6.2. Install requirements.
pip install -r requirements.txt
echo "===virtual environment .${venv_name} created==="

# 7. If doesn't exist, add virtual environment path to .gitignore.
grep -qxF ".${venv_name}/" .gitignore || echo ".${venv_name}/" >> .gitignore
echo "===updated .gitignore with ".${venv_name}/"==="

# 8. Add and commit .gitignore to git.
# NB Will report 'no changes added to commit' if .gitignore stayed the same.
git add .gitignore
git commit -m "Update .gitignore with '.${venv_name}/'"
echo "===added & committed .gitignore to git==="
```

**NB!** To make script executable it may be necessary to change the [mode of the file][chmod-tutorial]:

```bash
chmod 777 FILE_PATH
```

## Makefile

```makefile
# Virtual environment.
# 1. Get virtual environment name.
VENV_NAME := $(wildcard .venv_*)
# 2. Get kernel name from virtual-environment name (substitute '.' for '').
KERNEL_NAME := $(subst .,,$(VENV_NAME))
venv_get:
    scripts_shell/get_venv.sh

venv_remove:
    @echo "===removing virtual environment==="
    rm -rf $(VENV_NAME)
    @echo "===removing virtual iPython kernel==="
    rm -rf ~/Library/Jupyter/kernels/$(KERNEL_NAME)
```

[hitchhikers-guide-virtual-environments]: https://docs.python-guide.org/dev/virtualenvs/
[exhaustive-make-reference]: https://www.gnu.org/software/make/manual/make.html
[chmod-tutorial]: https://catcode.com/teachmod/