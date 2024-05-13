# Oceanography Jupyter Book

Badges: <BR><BR>


[![Deploy](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml/badge.svg)](https://github.com/geo-smart/use_case_template/actions/workflows/deploy.yaml)
[![Jupyter Book Badge](https://jupyterbook.org/badge.svg)](https://geo-smart.github.io/simple-template)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geo-smart/simple-template/HEAD?labpath=book%2Fchapters)
[![GeoSMART Use Case](./book/img/use_case_badge.svg)](https://geo-smart.github.io/usecases)


My name is Rob Fatland and among other things I advocate for extensively documenting one's process. 
So... this writeup is how this Oceanography Book was assembled. The starting point is a template repo
provided by the Geo-Smart organization. <br>


- I knew there were two templates available: The simple one (in use here) and a more comprehensive version
    - The website to view these (plus existing books) is [here](https://geo-smart.github.io/usecases).
- From the simple template I followed the directions (4 steps) in the README
    - (1) Clicked "Use This Template"; named the new repository (appearing in my personal organization) **`oceanography`**
        - Forked main branch only (the default checked option)
        - I have an existing repository **`ocean`**: Will be the basis of this Jupyter book
            - I am starting with a blank slate here
    - Started editing this `README.md` to trace my steps
    - (2) Edited `book/_config.yml` file to reflect this fork to `my-org/oceanography`
        - Presumably this will get bounced back over to the geo-smart org: For a later day
    - (3) Settings --> Pages --> Source = GitHub Actions
        - To do (?): Enable github pages
    - (4) Edit `environment.yml` to establish a working environment
        - How to create a proper **`environment.yml`**?
            - Read up on Python and environments
            - Install the `conda` package manager
                - I use `miniconda`
                - I then install packages / libraries as needed
            - From a working (*activated*) environment: `conda env export > environment.yml`
                - Analogous: `pip freeze` produces `requirements.txt`


### Open questions

- Jupyter notebooks go in the books/chapters folder
    - One notebook per chapter
    - Add chapter file paths to book/_toc.yml
- Instructions are to enable github pages in the github repository, enable github pages
- push all changes

