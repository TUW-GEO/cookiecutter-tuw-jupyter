# Cookiecutter TU Wien Jupyter Template

This template is meant for creating Jupyter notebooks for lectures and labs from scratch. It streamlines the setup process, making it easier to start new projects and maintain consistency across notebooks.

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
├── 01_eo-discover-eodag.yml   <- Configuration file for the associated Jupyter notebook
│
├── Makefile                   <- Root-level Makefile for project-wide commands
│
└── README.md                  <- Main README with project overview and usage instructions
```

### .github/workflows/binder.yaml

This YAML file contains a GitHub Action for launching the project on mybinder.org. Binder allows users to create interactive Jupyter environments from a Git repository. This file automates the process, making it easy to share and run notebooks in a cloud environment.

### .setup/Makefile

The Makefile from the `.setup` folder provides commands for setting up the project or deleting the notebooks and all dependencies again. With the command `make notebooks`the file handles the task of cloning the repository from GitHub, installing dependencies, and setting up virtual environments and kernels. The command `make delete`removes notebooks, environments and kernels again.

### .setup/README.md

This README file contains instructions on how to use the makefile to share the project both for TU Wien lecturers and for TU Wien students.

### .gitignore

The .gitignore file specifies which files and directories should be ignored by Git when committing changes to the repository. This helps keep the repository clean by excluding files that are not necessary for version control, such as temporary files, build artifacts, or sensitive information.

### 01_eo-discover-eodag.ipynb

This is an example Jupyter notebook provided as a template or starting point.

### 01_eo-discover-eodag.yml

This YAML file contains configuration settings specific to the Jupyter notebook `01_eo-discover-eodag.ipynb`. Here dependencies, environment variables, or other settings required to run the notebook successfully should be defined.

### Makefile

The root-level Makefile is designed to manage the setup and maintenance of Conda environments and Jupyter kernels for the entire project. It includes commands to create and remove Conda environments, configure Jupyter kernels, clean up unnecessary files, and more.

### README.md

The main README file provides an overview of the project, including its purpose, how to get started, and usage instructions. It serves as the entry point for understanding the project and typically includes links to further documentation or resources.

## Usage

1. Install [`cookiecutter`](https://cookiecutter.readthedocs.io/en/stable/index.html)
   if you haven't installed it yet:

   ```
   pip install cookiecutter
   ```

2. Use `cookiecutter-tuw-jupyter` to generate the Jupyter Notebook template. Therefore run

   ```
   cookiecutter https://github.com/TUW-GEO/cookiecutter-tuw-jupyter
   ```

3. Now fill out the requested information (default templating values are shown in square brackets `[]` and will be used if no other information is entered):
   - Github Name: Github account name of person or group (defaults to [TUW-GEO](https://github.com/TUW-GEO))
   - Project Name: Name of project and the accompanying GitHub repository
   - Project Slug: The same as the name but without capital letters and spaces
   
   These names are used in the `makefile` form the `.setup` folder. This is important when sharing the notebook for easy setup.

4. Now you can work on the Project. A example Jupyter notebook called `01_eo-discover-eodag.ipynb`has been created. Dont forget to push your changes to GitHub (Use the same names as in 3). 

5. Make sure that the GitHub repository is public and that it has a branch called `main`. This can be changed in GitHub in your project under the `Settings` on the top right.

6. To share your Project provide the `Makefile` together with the `README` file from the `.setup`folder.