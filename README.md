# Oceanography Jupyter Book

Badges: <BR><BR>


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
        - To do (?): Enable github pages
    - (4) Edit `environment.yml` to establish a working environment
        - The pre-existing `environment.yml` contains what is needed to build the Jupyter Book
            - Therefore do not clobber its contents!
            - Rather: Plan to merge other content into this file...
                - ...but only after successfully building a prototype Book
                - How is this done?
                    - At the top left of the GitHub console is a sequence of tabs: Code, Issues, Pull requests, Actions, ..., Settings
                    - Up above I went to Settings > Pages > Source > enable Github Actions
                    - *Now* I go to **`Actions`** and confirm a dialog about enabling workflow
                    - When I trigger a build (for example by editing and committing the `README.md` file):
                        - It fails because the default `environment.yml` file has `=10.3` etcetera: Out-of-date version specs
                        - I edit this file and remove the version conditions for `python` and `jupyter-book`
                        - The commit of this file triggers the build workflow
                        - When this completes I can look at the published Book
        - Expanding **`environment.yml`**?
            - Read up on Python environments
            - From a blank slate wor;Install the `conda` package manager
                - I use `miniconda`
                - I then install packages / libraries as needed
            - From a working (*activated*) environment: `conda env export > environment.yml`
                - Analogous: `pip freeze` produces `requirements.txt`


### Remaining instructions / question

- Jupyter notebooks go in the books/chapters folder: One notebook per chapter; add chapter file paths to book/_toc.yml
- in the github repository, enable github pages
- push all changes

