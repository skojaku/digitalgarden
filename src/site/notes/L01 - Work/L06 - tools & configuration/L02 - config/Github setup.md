---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-configuration/l02-config/github-setup/","dgPassFrontmatter":true}
---


# Github shortcut
Create `~/.gitconfig` file and set up `[alias]` section:

```
[alias]
    s = status
    ch = checkout
    co = commit -m
    pu = push
```

# Setup Github Action

Make a PyPI project using twine 
```
python setup.py sdist
twine upload --repository pypi dist/\*
```

Make PyPI and get TOKEN API :
- Login
- Go to the project
- Get API TOKEN

Make a workflow file `.github/workflows/main.yml` 

```
name: Unit Test & Deploy
on: push
jobs:
  build_test_publish:
    name: "Build & Test"
    runs-on: ubuntu-latest
    strategy:
      max-parallel: 1
      matrix:
        python-version: [3.7, 3.8]
    steps:
      - uses: actions/checkout@v2
      - name: Set up Python ${{ matrix.python-version }}
        uses: actions/setup-python@v2
        with:
          python-version: ${{ matrix.python-version }}
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip wheel setuptools
          pip install -r requirements.txt
      - name: Unit Test
        run: |
          python -m unittest tests/simple_test.py
      - name: Build python package
        run: |
            python setup.py bdist_wheel
      - name: Deploy to PyPI
        if: success() && startsWith(github.ref, 'refs/tags') && matrix.python-version == 3.8
        uses: pypa/gh-action-pypi-publish@master
        with:
          user: __token__
          password: ${{ secrets.PYPI_API_TOKEN }}
```

Add the pypy api token as the secretes to the github, with key name "PYPI_API_TOKEN"

## Auto-linting by pre-commit

Install pre-commit by 
```bash
conda install -c conda-forge pre-commit
```

Make a file under the root of the repo:
```.pre-commit-config.yaml 
# See https://pre-commit.com for more information
# See https://pre-commit.com/hooks.html for more hooks
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v3.2.0
    hooks:
    -   id: trailing-whitespace
    -   id: end-of-file-fixer
    -   id: check-yaml
    -   id: check-added-large-files

-   repo: https://github.com/pycqa/isort
    rev: 5.5.2
    hooks:
    -   id: isort
        args: ["--profile", "black"]

-   repo: https://github.com/psf/black
    rev: 19.10b0
    hooks:
    -   id: black
        language_version: python3

-   repo: https://github.com/pre-commit/mirrors-mypy
    rev: v0.790
    hooks:
    -   id: mypy
        args: [--ignore-missing-imports]

-   repo: https://github.com/myint/docformatter
    rev: v1.3.1
    hooks:
    -   id: docformatter
        args: [--in-place]

-   repo: https://github.com/PyCQA/flake8
    rev: 3.8.3
    hooks:
    -   id: flake8
        args: [--max-line-length, "88"]
        additional_dependencies: [flake8-bugbear, flake8-builtins, flake8-eradicate, pep8-naming]
```

And install by 
```bash
pre-commit
```

## Deploy

Please make sure your setup.py is correctly set up. [[checklist before deploy\|checklist before deploy]]

Push with a tag

```bash
git tag -a v<version> -m 'version <version>'
git push origin v<version>
```

