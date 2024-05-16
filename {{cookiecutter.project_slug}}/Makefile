.ONESHELL:
SHELL = /bin/bash
.PHONY: help clean install environment test version dist
CONDA_ENV_DIR = $(shell conda info --base)/envs/<pkg-name>
CONDA_ACTIVATE = source $$(conda info --base)/etc/profile.d/conda.sh ; conda activate ; conda activate
EODAG_PATH = $$(python -m pip show eodag | grep Location: | sed 's/^Location: //')

help:
	@echo "make clean"
	@echo " clean all jupyter checkpoints"
	@echo "make manifest"
	@echo " lock dependencies of conda environment"
	@echo "make develop"
	@echo " create a development conda environment"
	@echo "make kernel"
	@echo " make ipykernel based on conda lock file"
	@echo "make jupyter"
	@echo " launch JupyterLab server"

clean:
	rm --force --recursive .ipynb_checkpoints/

develop:
	@echo "creating new base {{cookiecutter.project_slug}} conda environment..."
	conda create -y -c conda-forge -n {{cookiecutter.project_slug}} python=3.10 pip mamba
	$(CONDA_ACTIVATE) {{cookiecutter.project_slug}} 
	mamba install -y -c conda-forge nbgitpuller jupyterlab eodag ipykernel 

publish:
	$(CONDA_ACTIVATE) {{cookiecutter.project_slug}} 
	mamba env export | grep -v "^prefix: " > environment.yml

kernel:
	mamba env create -n {{cookiecutter.project_slug}}--file {{cookiecutter.project_slug}} .yml
	$(CONDA_ACTIVATE) {{cookiecutter.project_slug}} 
	cp -f /tmp/eodag.yml ${HOME}/.config/eodag/eodag.yml
	cp -f /tmp/providers.yml $(EODAG_PATH)/eodag/resources/providers.yml
	python -m ipykernel install --user --name {{cookiecutter.project_slug}}
	@echo -e "conda jupyter kernel is ready."

jupyter: kernel develop
	jupyter lab .
