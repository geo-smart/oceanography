# Oceanography Jupyter Book


## Preamble


- This is the main branch README markdown file for the geo-smart oceanography repository.
    - Built from the [simple template](https://github.com/geo-smart/simple-template) (not the [more expansive template](https://github.com/geo-smart/use_case_template))
- This repository (automatically) publishes to [this Jupyter Book website](https://geo-smart.github.io/oceanography).
- A Jupyter Book is an extension of the Jupyter notebook concept and [the documentation on this is at JupyterBook.org](https://jupyterbook.org).
- Here are related badges: <BR><BR>


[![Deploy](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml/badge.svg)](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml)
[![Jupyter Book Badge](https://jupyterbook.org/badge.svg)](https://geo-smart.github.io/simple-template)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geo-smart/simple-template/HEAD?labpath=book%2Fchapters)
[![GeoSMART Use Case](./book/img/use_case_badge.svg)](https://geo-smart.github.io/usecases)


## Building a working Jupyter Book


I advocate for documenting process. Here is how the Geo-Smart organization 'simple skeleton' source 
repository was used to create a Jupyter Book version of my oceanography work.<br>


- I knew there were two templates available: The simple one (in use here) and a more comprehensive version
    - [Links are provided by the 'use cases' website here](https://geo-smart.github.io/usecases).
- The 'simple' template gives directions on forking a new Jupyter Book (in the template `README.md` file).
    - These are reiterated here with some elaboration.
    - (1) Clicked "Use This Template"; name the new repo; choose the Geo-Smart organization; behold **`oceanography`**
        - Forked the main branch only (the default checked option)
            - I can see the value in doing something more complicated but I decline at this point to do so.
        - My existing repository **`ocean`** will be the basis of this Book once the basics are sorted.
        - I began editing this this `README.md` to trace my steps.
    - (2) Edited `book/_config.yml` to reflect `oceanography`
    - (3) Settings --> Pages --> Source = GitHub Actions
        - This turns on automatic regeneration of the book every time there is a repo commit
    - (4) Edit `environment.yml` to establish a working environment
        - The template includes an `environment.yml` file needed to build the Jupyter Book
            - Do not clobber this file!
            - Rather these two steps:
                - Test the build now (see note below) to verify the Book is created properly
                - As content is added: Add in other modules / libraries as needed
        - Did the test build work??? No! And here is why and how to fix it:
            - Top left of the GitHub console tabs: Code, Issues, Pull requests, Actions, ..., Settings
            - Earlier: **> Settings > Pages > Source > enable Github Actions**: Necessary, done.
            - *Now*: **> `Actions`**
                - The GitHub portal may request that you sign off on enabling workflow: ok.
                - Trigger a Book build: Commit a change or start the build manually
                - My issue when this Build failed: `environment.yml` outdated versions
                    - Example: `python=3.10`
                    - Solution: Edit `environment.yml` to remove versions
                    - Example `python=3.10` becomes just `python`
                    - Likewise for `jupyter-book`
                    - Commit `environment.yml` and the Book now builds properly
                    - Verify from the provided link
        - In the next section I document expanding `environment.yml` as content is added
            - In preparation for this phase I suggest
                - Read about Python environments
                - Work from a local clone of the repo
                    - Outline of setup:
                        - On a blank slate workstation install the `conda` package manager
                            - I use `miniconda` rather than full `anaconda`
                        - Clone the GitHub repository (*this*) using `git clone <URL>`
                        - Create an environment and activate it
                            - Include the activate command in an echo statement inside `.bashrc`
                            - Remember to activate this environment every time logging in
                        - Working locally: Install packages / libraries, develop content
                            - This *expands* what the environment supports
                        - Commit changes, check the resulting Book is correct
            - Specific to `environment.yml`
                - This file acts as a derived record of installed libraries for a given environment
                    - From a working (*activated*) environment: `conda env export > environment.yml`
                    - Analogous: `pip freeze` produces `requirements.txt`
                    - At this point one could wholesale copy-paste a very long library list
                    - Instead I am going to try a more minimalist approach; see notes below


## Building out and testing the Book

At this point the Book site is automatically compiling with every commit. The **`_config.yml`** file 
has been modified and we have the subfolder **`/books/chapters`** where the notebooks will go.


**Questions, procedures, issues:**


- Each **`.ipynb`** notebook maps to a book chapter: **`~/book/chapters/newchapter.ipynb`**.
    - Create a new chapter entry in **`/book/_toc.yml`**
        - This will look like **`    - file: chapters/newchapter`**
- How does the Book environment develop along with increasing content?
    - There is some crossover here with **binder** it seems
- How much Python functionality is present in the Book?
- LaTeX?
- How much data can be bundled with the Book?

### Inline images


The following Python code will convert a `jpg` to `png` format:


```
from PIL import Image
Image.open('revelle.jpg').save('revelle.png')
```

Per the JupyterBook documentation: HTML is not recommended so I will revert to markdown inlining of
images. This does not seem to work for jpegs so the above Python is a means of converting jpg to png.

The template has a folder **`~/book/img`** so I added subfolders **`/rca/images/category`** and 
**`/rca/animations/category`**.



