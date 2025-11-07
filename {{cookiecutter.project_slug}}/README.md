TODO: Add you lecture description.

# Generate Jupyter Conda environment and Jupyter Kernel from `yml`

To re-create the environment as a Jupyter kernel for execution of the notebooks, do the following:

- Open a Terminal from the same level as this Markdown README file and the Makefile file.
- Type the following into the terminal.

```
make kernel
```

Select the kernel with the equivalent name as the `.ipynb` notebook to execute the notebook. For example, `01_lecture.ipynb` requires the kernel `01_lecture` for execution of the code blocks.

# Clean-up

To remove Jupyter checkpoints run:

```
make clean
```

In order to remove the Conda environments and Jupyter kernels runL

```
make teardown
```

# Developing

Commit notebooks without output for smaller file sizes and interactive teaching. For convenience use `nbstripout` to clean notebooks, like so:

```
pip install nbstripout
nbstripout **/*.ipynb
```

Check you code for correct syntax as we want to show off good practices. You can use flake8-nb to check your writing.

```
pip install flake8-nb
flake8-nb **/*.ipynb
```

The pre-commit hooks can be used to check whether outputs are empty. This can be achieved, like so:

```
pip install pre-commit
pre-commit install
```

# Developing

> [!TIP]
> It is recommended to use `uv` to handle the environment and the dependencies.
> To use `uv` or `uvx` the [uv] package manager needs to be installed.

## Dependencies

Use the [uv] to add dependencies to your workspace. Read the docs if you are not familiar with it. And use the following command to add dependencies to your workspace.

```bash
uv add <package>
```

## Strip Outputs

Commit notebooks without output for smaller file sizes and interactive teaching.
For convenience use `nbstripout` to clean notebooks, like so:

```bash
uvx nbstripout **/*.ipynb
```

## Code Quality

Check your code for correct syntax as we want to show off good practices. You can use [ruff] to check your writing.

```bash
# To run the ruff linter
uvx ruff check --fix

# To run the ruff formatter
uvx ruff format
```

To type check your code/notebook, and to make your code a little more static you might want to run:

```bash
uvx ty check
```

Alternatively a static type-checker like [mypy] can also be used, but that is more difficult to run on notebooks.

## Pre-Commit Hooks

The pre-commit hooks can be used to check whether outputs are empty. This can be achieved, like so:

```bash
uvx pre-commit install
```

## Taskrunner

There are two different taskrunner frameworks in place. You can use the `Makefile` or the `Justfile` to run repeated tasks.

To see what recipes are implemented there run:

```bash
make help
```

for the `Makefile` or for the `Justfile`:

```bash
just
```

These tools should make your development experience much nicer.

[ruff]: https://docs.astral.sh/ruff/
[uv]: https://docs.astral.sh/uv/
[mypy]: https://mypy.readthedocs.io/en/stable/index.html
