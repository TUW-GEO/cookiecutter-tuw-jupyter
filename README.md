# Cookiecutter TUWien Jupyter template

This template is mean for creating Jupyter notebooks for lectures and labs.

# Requirements

This template depends on the frameworks:

- `cookiecutter` for generating templated projects (https://cookiecutter.readthedocs.io/en/stable/index.html)
- `poetry` for dependency management (https://python-poetry.org/)

# Dependency management

Make sure to add python packages to the manifest file for managing the environment and creation of reproducible workflows in the 
JupyterHub. The preferred way to add dependencies is as follows:

```
poetry add <package>
```

Followed by:

```
poetry lock
```

The latter writes all the packages and their exact versions that it downloaded to a poetry.lock file, locking the project to those specific versions. This gives the most robust results for reproducing the Jupyter workflows.

