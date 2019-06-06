draftcheck
==========

Travis:[![Build Status](https://travis-ci.org/dvolgyes/draftcheck.svg?branch=master)](https://travis-ci.org/dvolgyes/draftcheck)

`draftcheck` is an LaTeX linter that is specifically designed for academic writing.

Installation
------------

`draftcheck` can be installed using pip:

```bash
pip install draftcheck
```

You can also install it from source:

```bash
mkdir draftcheck && cd draftcheck
git clone https://github.com/ebnn/draftcheck.git
python setup.py install
```

Usage
-----

The supplied files contains several example LaTeX files that can be used to test it.

```
$ draftcheck examples/simple.tex
examples/simple.tex:26:1: (http://www.comp.leeds.ac.uk/andyr/misc/latex/\-latextut...
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
	[030] Wrap URLs with the \url command.

examples/simple.tex:31:37: ...thin \LaTeX\cite{lamport94}...
                                        ^^^^^^^
	[004] Place a single, non-breaking space '~' before citations.

examples/simple.tex:49:10: ...%Set up an 'itemize' environmen...
                                        ^^^^^^^^^^^
	[014] Use left and right quotation marks ` and ' rather than '.

examples/simple.tex:93:0: \begin{center}
                          ^^^^^^^^^^^^^^
	[015] Use \centering instead of \begin{center}.

examples/simple.tex:123:29: ...the number '9'. This is b...
                                         ^^^^^
	[014] Use left and right quotation marks ` and ' rather than '.


Total of 5 mistakes found.
```

Pre-commit hooks
----------------

[Pre-commit](https://pre-commit.com/) hooks is a framework for managing and maintaining multi-language pre-commit hooks.

You can check your LaTeX files automatically before committing them to git.
Three steps are required:
- install pre-commit package from pip, e.g. ```pip install pre-commit --user```
- go to your latex directory, and install the hooks:
  ```pre-commit install```
- add the following lines to your `.pre-commit-config.yaml` file:
```
repos:
-   repo: https://github.com/ebnn/draftcheck
    rev: master
    hooks:
    - id: draftcheck
```

