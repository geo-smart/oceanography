# Contributing


Contributions are welcome.


- Report bugs, request features or submit feedback as a [GitHub Issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues).
- Make fixes, add content or improvements using [GitHub Pull Requests](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests)


Ready to contribute? Here's a quick guide


## Contributing website changes


To build our website, we need specific Python packages which 
are managed with the `conda` and `mamba` tools. 
If you already do not already have those tools installed, we recommend using the 
[Mambaforge Installer](https://github.com/conda-forge/miniforge#mambaforge):


1. Fork this geosmart's website repo on GitHub.


2. Clone your fork locally:

    ```sh
    git clone https://github.com/geo-smart/use_case_template.git
    cd book
    ```

3. Create a branch to add your changes:

    ```sh
    git checkout -b name-of-your-bugfix-or-feature
    ```

4. Create and activate the "geosmart" conda environment.

   __NOTE__: If you're running linux or Windows use `conda/conda-linux-64.lock.yml`
    ```sh
    mamba env create --name geosmart --file conda/conda-osx-64.lock.yml
    mamba activate geosmart
    ```
   __NOTE__: If you want to add packages or change the environment,
    you must follow the procedure outlined in [./conda/README.md](./conda/README.md).

5. Make your desired changes and build the book locally

    ```sh
    jb build book
    ```
   __NOTE__: to preview the changes open `book/build/html/index.html`

6. Push your branch to GitHub when you're ready:

    ```sh
    git add .
    git commit -m "Your detailed description of your changes."
    git push origin name-of-your-bugfix-or-feature
    ```

7. Open a pull request through the GitHub website: https://github.com/geo-smart/use_case_template
