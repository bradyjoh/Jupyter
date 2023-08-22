# Jupyter
 This is a Jupyter Notebook Data Science Environment.







## Setup

- I set this up with Pipenv to try and make dependency management more reproducible.
- `pipenv shell` to enter into a special shell unique to this directory. Now `pip list` will show only the packages needed for this repo
- `pipenv install notebook pandas matplotlib seaborn` will install dependencies and configure the `Pipfile` and `Pipfile.lock` files
- In the future, just running `pipenv install` would look at the Pipfile and lockfile and get the environment set up automatically based on the packages defined within
- Run/open Jupyter Notebook with `jupyter notebook` and it will start on port 8888 and can be browsed
