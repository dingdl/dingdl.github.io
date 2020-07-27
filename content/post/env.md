+++
author = "Ding Luo"
title = "Virtual Environments"
date = "2020-07-27"
description = "Guide to emoji usage in Hugo"
tags = [
    "conda", "python", "environment management"
]
+++

Manage Python virtual environments with Conda.
<!--more-->

#### Check existing Conda environments
```
conda info -e
conda env list
```
#### Create a new Conda environment
```
# env_name = my_env, python = 3.8
conda create -n my_env python=3.8
```
#### Activate an environment
```
# env_name = my_env
conda activate my_env
```
#### Add it as a new kernel in jupyter notebook/lab
**First enter the target environment using the command above**. Then install IPython kernel in the environment.
```
pip install ipykernel
```
Add it to Jupyter.
```
python -m ipykernel install --user --name my_env --display-name "whatever_name"
```
#### Check all the installed kernels
```
jupyter kernelspec list
```
#### Remove a kernel
```
jupyter kernelspec uninstall unwanted-kernel
```
