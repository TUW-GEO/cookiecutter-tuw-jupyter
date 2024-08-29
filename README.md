# Cookiecutter TU Wien Jupyter Template

This template is meant for creating Jupyter notebooks for lectures and labs from scratch.

## Template

```
my_project
├── .github
│   └── workflows
│       └── binder.yaml        <- Workflow for launching the project on mybinder.org.
│
├── .setup
│   ├── Makefile               <- Commands for setting up the project environment.
│   └── README.md              <- Instructions for setting up the development environment.
│
├── .gitignore                 <- Specifies files and directories to ignore in version control.
│
├── 01_eo-discover-eodag.ipynb <- Example Jupyter notebook
│
├── 01_eo-discover-eodag.yml   <- YAML configuration for the associated Jupyter notebook
│
├── Makefile                   <- Root-level Makefile for project-wide commands
│
└── README.md                  <- Main README with project overview and usage instructions
```

## Usage
1. Create an empty repository on Guithub where the new Jupyter Notebook project should be. Github account name of person or group and the prject name will be needed in step 4.

2. Install [`cookiecutter`](https://cookiecutter.readthedocs.io/en/stable/index.html)
   if you haven't installed it yet:

   ```
   pip install cookiecutter
   ```

3. Use `cookiecutter-tuw-jupyter` to generate the Jupyter Notebook template. Therefor run

   ```
   cookiecutter git@github.com:executablebooks/cookiecutter-jupyter-book.git
   ```

4. Now fill out the requested information (default templating values are shown in square brackets `[]` and will be used if no other information is entered):
   - Github Name: Github account name of person or group (defaults to [TUW-GEO](https://github.com/TUW-GEO))
   - Project Name: Name of project and the accompanying GitHub repository
   - Project Slug: The same as the name but without capital letters and spaces
   The names are used in the `makefile` form the `.setup` folder. This is important for sharing the notebook for easy setup.

5. Now commit the changes to the notebooks. 




## Explanation of the makefile,... the whole workflow