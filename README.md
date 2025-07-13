# Project Overview
This is a Jupyter kernel implementation that provides on-demand IPython kernels with dependencies pulled from PEP723 metadata. Each kernel instance is an on-demand virtual environment managed by `uv`. This kernel is compatible with notebooks modified by `juv`.

# Installation and use
Either:
```bash
uv tool run --with uvvkernel --from jupyterlab jupyter-lab 
``` 
or just `pip install uvkernel` to your existing jupyter server environment.

# Known limitations
- Can't install Jupyter extensions
- There is no UI (you can use the juv comand line tool, though!)
- There's no graceful handling of invalid/unsolvable dependency metadata (the kernel just doesn't start)

# Why use this instead of...
### Juv?
Use Juv if you want to spin up a dedicated Jupyter server for a specific notebook. Use uvkernel if you prefer to have a single (maybe even shared) jupyter server, and many notebooks with individual dependencies. Use Juv for a nice command-line tool to add dependencies and do locking (in fact, you should use the command line tool to manage your notebooks for uvkernel!)

### pyproject-local-kernel?
Use pyproject-local-kernel if you want to manage dependencies with pyproject.toml files, separate from your notebooks. Use uvkernel if you want the dependencies embedded in the notebook. Use pyproject-local-kernel if you want the freedom to use uv/hatch/poetry/etc. uvkernel only uses uv!

# Development Commands
1. Install uv manually.
2. Git checkout this repository.
3. Run the local version like this:
```bash
# Test package with jupyter-lab
uv tool run --with . --refresh-package uvkernel --from jupyterlab jupyter-lab
```
