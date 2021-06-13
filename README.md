<div align="left">
  <img src="https://github.com/pyscf/pyscf-doc/blob/master/logo/pyscf-logo.png" height="80px"/>
</div>

PySCF website and documentation
===============================

## Overview

The PySCF website and documentation are written in a combination of Markdown and
reStructuredText, using `sphinx-doc` and several associated extensions to
generate static `html` files that are served from the `gh-pages` branch.  Pushes
to this repository trigger a Github Action that builds and serves the updated
website.

## Building the docs locally

### Requirements

Pip install the following packages, which are also listed in `requirements.txt`:

- pyscf
- sphinx
- sphinx-material
- sphinxcontrib-bibtex
- nbsphinx

If you have multiple versions of PySCF on your machine and you would like so use
a specific version, set `PYTHONPATH` to include the specific PySCF source
directory you want; otherwise, uncomment
`sys.path.append(os.path.abspath('path_to_pyscf'))` in
[source/conf.py](source/conf.py).

### Building
All sphinx related sources files (i.e. `.rst` and `.md`) are contained in `source` and all webpage files (once they're generated) live in the `build`.

To generate the website (without the API docs) run the following from the main project directory.
If you are running on Linux, and you want to build faster you can use `make html_parallel`.

```bash
make html
```

To generate the complete website (including the API docs) run the following from the main project directory.
Since the API docs are large, this build is noticeably slower than just generating the website with `make html`.
:warning: PySCF must be accessible in your current Python environment when you run `make api_docs` or `make html_full`.

```bash
make html_full
```

To see more of the options you can use with `make`, just use `make help`.


### Serving
Finally to serve the website, you can run:

```bash
 python -m http.server --directory build/html
```


### Adding Content to GitHub Pages

If you want to show the latest version of the docs on GitHub pages, build using then instructions above. Then from `pyscf-doc/source` run the following:

```bash
make gh_pages_setup
```

## How to Contribute

1.  Add a rst file \"your\_method.rst\" in the [source/user](source/user/) directory in which one describes the basic theory and usage of the method. Reference \"user/your\_method.rst\" in the \"toctree\" section in [source/user.rst](source/user.rst).
2.  Add a rst file \"your\_module.rst\" in the [source/modules](source/modules/) directory in which one lists the examples and the member classes and functions of the module (the API doc is then generated by autodoc). (In the \"\_\_init\_\_.py\" file of each module, one should include a simple usage section. See [pyscf.dft.\_\_init\_\_.py](https://github.com/pyscf/pyscf/blob/master/pyscf/dft/__init__.py) as an example.) Reference \"your\_module.rst\" in the \"toctree\" section in [source/modules.rst](source/modules.rst).
3.  Optionally, one could also add a rst file \"your\_method\_develop.rst\" in the  [source/develop](source/develop/) directory where one provides more detailed descriptions of the implementation and advanced guidelines for using and further development of the module. Reference \"your\_method\_develop.rst\" in [source/develop.rst](source/develop.rst). 


<!-- ## Adding Blog Posts

Create a new `.md` file in `pyscf-doc/source/posts` and add the following header (modified for your post):

```
---
blogpost: true
date: February 1, 2021
author: James Smith
location: World
category: Tutorial
tags: HF, DFT, MCSCF
language: English
---
```

If you want to write a post in `.rst` that's fine too! Just use the following in your header:

```
:blogpost: true
:date: Oct 10, 2020
:author: Nabil Freij
:location: World
:category: Manual
:language: English
``` -->
