+++
author = "Ding Luo"
title = "My Data Science Environment on Windows 10"
date = "2020-07-31"
description = "Guide to emoji usage in Hugo"
tags = [
    "windows 10", "data science", "development environment"
]
+++

There are tons of articles/posts on Internet about how to set up a development environment on different OS (Windows, Linux etc.). I want to make this post a place for me to dynamically record how it is on my (corporate) Windows 10.

<!--more-->

**Below is the latest setup for my own works. It for sure cannot be the state of the art, but I will keep exploring and updating.**

- [Terminal emulator - Cmder](#terminal-emulator---cmder)

- [Version control - Git](#version-control---git)

- [Environment management - Conda](#environment-management---conda)

- [Extensions for JupyterLab](#extensions-for-jupyterlab)

<!-- - [Source code editor/IDE - VS Code/PyCharm](#source-code-editor-ide---vs-code-pycharm) -->

<!-- toc -->

## Terminal emulator - Cmder    
What has bothered me a lot about working on Windows is that I did not use a good tool to handle multiple terminals.  Why? Because it is very common for me to have a couple of PowerShell terminals running at the same time for various tasks, such as running Jupyter Lab/Notebook, connecting remote machines on cloud, running a local server for editing my website, doing Git... Luckily recently I found [Cmder](https://cmder.net/), which makes my life much easier.

 But of course, Microsoft has started building their own tool [Windows terminal](https://github.com/microsoft/terminal). However, at this moment I cannot try it because my corporate laptop cannot be updated to the latest Windows 10 build version. Really look forward to trying it out!

## Version control - Git
No need to repeat why Git is necessary for any coding related works. Git as a general version control tool should be used in many other works.

## Environment management - Conda
When I started using the current computer, I installed [Anaconda](https://www.anaconda.com/). But I guess in the future I would just install Conda because that is sort of the only part that I use from Anaconda.

Another thing relating to environment management is adding python kernels to JupyterNotebook/Lab. Simply speaking, we only install jupyter in one environment, but the python kernels in the other environments can also be used in this jupyter environment. See more details [here](../../post/env/).

## Extensions for JupyterLab
Check out this [awesome-jupyterlab-extension](https://github.com/Yogayu/awesome-jupyterlab-extension#telamoniantheme-darcula).

<!-- ## Source code editor/IDE - VS Code/PyCharm -->
PyCharm is nice, but VS Code can still be useful in some cases.
