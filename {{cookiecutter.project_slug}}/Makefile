.ONESHELL:
SHELL = /bin/bash
.PHONY: help clean environment kernel teardown

YML = {{cookiecutter.project_slug}}.yml
CONDA_ACTIVATE = source $$(conda info --base)/etc/profile.d/conda.sh ; conda activate ; conda activate {{cookiecutter.project_slug}}
PREFIX = $(CURDIR)/.conda_envs
CONDA_ENV_DIR := $(PREFIX)/{{cookiecutter.project_slug}}
KERNEL_DIR = $(shell jupyter --data-dir)/kernels/{{cookiecutter.project_slug}}

help:
	@echo "Makefile for setting up environment, kernel, and pulling notebooks"
	@echo ""
	@echo "Usage:"
	@echo "  make environment  - Create Conda environments"
	@echo "  make kernel       - Create Conda environments and Jupyter kernels"
	@echo "  "
	@echo "  make teardown     - Remove Conda environments and Jupyter kernels"
	@echo "  make clean        - Removes ipynb_checkpoints"
	@echo "  make help         - Display this help message"

clean:
	rm --force --recursive .ipynb_checkpoints/

teardown:
	$(CONDA_ACTIVATE)
	jupyter kernelspec uninstall -y {{cookiecutter.project_slug}}
	conda deactivate
	conda remove -n {{cookiecutter.project_slug}} --all -y

$(CONDA_ENV_DIR): $(YML)
	conda env create --file $^ --prefix $@

environment: $(CONDA_ENV_DIR)
	@echo -e "conda environments are ready."

$(KERNEL_DIR): $(CONDA_ENV_DIR)
	$(CONDA_ACTIVATE)
	python -m ipykernel install --user --name {{cookiecutter.project_slug}} --display-name {{cookiecutter.project_slug}}
	conda deactivate

kernel: $(KERNEL_DIR)
	@echo -e "conda jupyter kernel is ready."
