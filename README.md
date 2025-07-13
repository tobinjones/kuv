# Project Overview
This is a Jupyter kernel implementation that provides on-demand IPython kernels with dependencies pulled from PEP723 metadata. Each kernel instance is an on-demand virtual environment managed by `uv`. This kernel is compatible with notebooks created by `juv`, EXCEPT that lockfile metadata is not respected (yet). 

# Installation and use
Either:
```bash
uv tool run --with uvvkernel --from jupyterlab jupyter-lab 
```
or just `pip install uvkernel` to your existing jupyter server environment.

# Known limitations
- The kernel must be manually restarted when the metadata changes.
- Doesn't respect juv lockfile metadata
- Unlike juv, can't install jupyter extensions
- There is no UI (you can use the juv comand line tool, though!)
- There's no graceful handling of invalid/unsolvable dependency metadata

# Why use this instead of juv
This allows you to have a single jupyter server, with unique virtualenvs for each notebook. For my use, this was a better level of abstraction than running a whole jupyter server for each notebook.

# Development Commands
Install uv manually and then run using:
```bash
# Test package with jupyter-lab
uv tool run --with . --refresh-package uvkernel --from jupyterlab jupyter-lab
```
