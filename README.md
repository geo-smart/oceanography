# Oceanography Jupyter Book

- This is the main branch README markdown file for the geo-smart oceanography repository.
    - Built from the [simple template](https://github.com/geo-smart/simple-template) (not the [more expansive template](https://github.com/geo-smart/use_case_template))
- This repository (automatically) publishes to [this Jupyter Book website](https://geo-smart.github.io/oceanography).
- Here are related badges: <BR><BR>


[![Deploy](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml/badge.svg)](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml)
[![Jupyter Book Badge](https://jupyterbook.org/badge.svg)](https://geo-smart.github.io/simple-template)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geo-smart/simple-template/HEAD?labpath=book%2Fchapters)
[![GeoSMART Use Case](./book/img/use_case_badge.svg)](https://geo-smart.github.io/usecases)


I advocate for documenting process. Here is how the Geo-Smart organization 'simple skeleton' source 
repository was used to create a Jupyter Book version of my oceanography work.<br>


- I knew there were two templates available: The simple one (in use here) and a more comprehensive version
    - [Find links to these two templates here](https://geo-smart.github.io/usecases).
- The 'simple' template gives directions on forking a new Jupyter Book in the `README.md` file.
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
            - Earlier: Settings > Pages > Source > enable Github Actions: Good
            - *Now*: **`Actions`** and if necessary sign off (click) the dialog enabling workflow
                - On the Actions page: I can trigger a build manually or via a commit
                    - ...for example: Editing and commit this `README.md` file
                - Build fails: `environment.yml` file has outdated version specs: `python=3.10` etcetera
                    - Edit `environment.yml`: Remove version conditions for `python` and `jupyter-book`
                    - The commit of this file triggers the build workflow
                    - When completed: A link to the Book is given.
        - Expanding **`environment.yml`**
            - Read up on Python environments
            - From a blank slate workstation: Install the `conda` package manager
                - I use `miniconda`
                - I then install packages / libraries as needed
            - From a working (*activated*) environment: `conda env export > environment.yml`
                - Analogous: `pip freeze` produces `requirements.txt`
                - At this point one could wholesale copy-paste a very long library list
                - Instead I am going to try and just add key libraries


### Remaining instructions / question

- Jupyter notebooks go in the books/chapters folder
    - One notebook per chapter
    - Add chapter file paths to book/_toc.yml

