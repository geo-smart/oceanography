[Jupyter Book](https://geo-smart.github.io/oceanography/intro.html), [GitHub repo](https://github.com/geo-smart/oceanography).



# Oceanography Jupyter Book


## Preamble


- This is the main branch README markdown file for a book on oceanography
    - This book is developed within the Geo-Smart geosciences organization
    - Built from the [simple template](https://github.com/geo-smart/simple-template) (not the [more expansive template](https://github.com/geo-smart/use_case_template))
- This repository (automatically) publishes to [this Jupyter Book website](https://geo-smart.github.io/oceanography).
- A Jupyter Book is an extension of the Jupyter notebook concept and [the documentation on this is at JupyterBook.org](https://jupyterbook.org).
- Here are related badges: <BR><BR>


[![Deploy](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml/badge.svg)](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml)
[![Jupyter Book Badge](https://jupyterbook.org/badge.svg)](https://geo-smart.github.io/simple-template)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geo-smart/simple-template/HEAD?labpath=book%2Fchapters)
[![GeoSMART Use Case](./book/img/use_case_badge.svg)](https://geo-smart.github.io/usecases)


## Build a working Jupyter Book: Get Started

> Before diving in a couple notes:
> - [Jupyter Book documentation here](https://jupyterbook.org)
> - Be sure to `pip install -U jupyter-book` in a local computer conda environment
> - If a commit fails to produce a new version of the Book: Go to the GitHub Actions tab to read the fail diagnostic


I advocate for documenting process... so here is how I began with the Geo-Smart organization 'simple skeleton' 
repository and built out an Oceanography JupyterBook. The important idea is that in addition to a repo there
is a website *compiled* from that repo.


- There are two templates hosted by Geo-Smart on GitHub: A simple one and a more comprehensive version
    - [Links: See 'use cases' here](https://geo-smart.github.io/usecases).
- **Simple** template gives directions on building a new Jupyter Book: Template `README.md` file
    - Click "Use This Template"
        - Name a new repo; choose the Geo-Smart organization
        - Fork the main branch (default)
        - Breadcrumbs: This `README.md`
    - Edit `book/_config.yml` to reflect the topic, again *oceanography*
    - Settings > Pages > Source = GitHub Actions
        - Every commit triggers a recompile of the website
    - (4) Edit `environment.yml` to establish a working environment
        - Template includes `environment.yml`: essential libraries for the Jupyter Book
            - ***Do not clobber this file!***
                - Test the build now (see below), verify the Book
                - Add other libraries as needed
                - Open question: Myst-nb? See below on image embed
        - My test build failed
            - Top left of the GitHub console tabs: Code, Issues, Pull requests, Actions, ..., Settings
            - Earlier: **> Settings > Pages > Source > enable Github Actions**: Done
            - Fixing the website compile fail: **> `Actions`** tab
                - GitHub may require workflow approval: Approve
                - Trigger a build (compile): Commit a change or start it manually
                - Build fail error message: `environment.yml` outdated versions
                    - Example: `python=3.10`
                    - Solution: Edit `environment.yml` to remove `=xx.yy` versions
                    - Example `python=3.10` > `python`, and so for jupyter-book
                    - Commit `environment.yml`: Book build ok
        - The section below expands **`environment.yml`** modifications
            - Read about Python environments
            - clone the repo locally
                - Sketch of setting up a local working Python environment:
                    - Blank slate workstation: install **`miniconda`**
                        - miniconda is lightweight and includes the `conda` package manager
                    - **`git clone https://github.com/geo-smart/newbookreponame`
                    - Create an environment and activate it
                    - In case we forget: We include the `activate` command as a `.bashrc` echo
                        - Activate this environment on each work session
                        - Install libraries, develop content
                            - This will introduce errors in the JupyterBook
                            - ...because the environment is built from `environment.yml` which...
                            - ...has not been updated yet. Continued below...
                        - `environment.yml` is a derived record of installed libraries
                            - From a working (*activated*) environment: `conda env export > environment.yml`
                                - `pip freeze` is an analogous approach
                            - Plan: Do not wholesale copy-paste `env.yml` into the GitHub repo.
                            - Rather: Take a more minimalist approach; again see below


## Building the JupyterBook: Content development


### So far

- The Book builds / compiles with every commit
- **`_config.yml`** has been modified
- The subfolder **`/books/chapters`** is where notebooks go
- The subfolder **`/books/img`** is where static visual content (`png` files) reside


### Questions, procedures, issues


- Each **`.ipynb`** notebook maps to a book chapter: **`~/book/chapters/newchapter.ipynb`**.
    - Create a new chapter entry in **`/book/_toc.yml`**
        - This will look like **`    - file: chapters/newchapter`**
        - Corresponding to **`chapters/newchapter.ipynb`**
- How does the Book environment develop along with increasing content?
    - First example error: `No module named 'matplotlib'`
        - Notice the JupyterBook builds despite errors of this sort
        - Added a `matplotlib` entry and an `xarray` entry to `environment.yml` fixed this error
- How much Python functionality is present in the Book?
- LaTeX?
- How much data can be bundled with the Book?


### Inline images

Per the JupyterBook documentation: HTML is not recommended so I will revert to markdown inlining of
images. This does not seem to work for jpegs so convert `jpg` to `png` using Python:


```
from PIL import Image
Image.open('revelle.jpg').save('revelle.png')
```


***Issue*** The corresponding basic markdown `![text](path_to_image.png)` works. A more sophisticated version
seems to require Myst-nb (?) and does not seem to work natively. 


To organize static content: **`~/book/img/`** += subfolders **`/rca/images/<category>`** and 
**`/rca/animations/<category>`**.






