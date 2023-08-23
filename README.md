# Jupyter
 This is a Jupyter Notebook Data Science Environment. Right now it only houses a notebook to evaluate NYC MTA OMNY transit data.

## Setup

- I set this up with Pipenv to try and make dependency management more reproducible.
- `pipenv shell` to enter into a special shell unique to this directory. Now `pip list` will show only the packages needed for this repo
- `pipenv install notebook pandas matplotlib seaborn` will install dependencies and configure the `Pipfile` and `Pipfile.lock` files
  - `notebook` is Jupyter Notebook
  - `pandas` is to manage DataFrames
  - `matplotlib` is the underlying graph/plot/figure library
  - `seaborn` is an easier to use figure library built on matplotlib
- In the future, just running `pipenv install` would look at the Pipfile and lockfile and get the environment set up automatically based on the packages defined within
- Run/open Jupyter Notebook with `jupyter notebook` and it will start on port 8888 and can be browsed http://localhost:8888/tree?
- (Optional) Pandoc and LaTeX are needed to export PDFs from Notebook, but need to be installed via homebrew or another method (not in pip): `brew install pandoc basictex`
  - Part of installing `basictex` is adding the following into the `.zshrc` file to update the PATH with `/Library/TeX/texbin`: `eval "$(/usr/libexec/path_helper)"`
  - I also had to use `tlmgr` to update and install some LaTeX extensions and plugins, otherwise I was seeing errors such as  `LaTeX Error: File 'adjustbox.sty' not found` when I tried to run the export command `jupyter nbconvert --to pdf "OMNY Analysis.ipynb"`
  - First `sudo tlmgr update --all --self` 
  - Then `sudo tlmgr install tcolorbox environ pdfcol adjustbox titling enumitem soul collection-fontsrecommended`
  - (Perhaps just installing the full 5GB MacTeX `brew install mactex` would have avoided this)
  - After these steps though, LaTeX-style PDFs of the Notebook can be exported via the Web UI or with the CLI `jupyter nbconvert --to pdf "OMNY Analysis.ipynb"`
  - Resources
    - https://stackoverflow.com/questions/59225719/latex-error-related-to-tcolorbox-sty-not-found
    - https://www.softec.lu/site/DevelopersCorner/MasteringThePathHelper
    - https://pandoc.org/installing.html
- (Optional) nbextensions setup
  - https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/install.html
  - Shut down the Jupyter Notebook server
  - Run `pipenv install jupyter_contrib_nbextensions` to add it to the Pipfile
  - Run `jupyter contrib nbextension install --user` to install the files
  - NOPE, it's not currently supported for Jupyter Notebook v7 https://stackoverflow.com/questions/76893872/modulenotfounderror-no-module-named-notebook-base-when-installing-nbextension
