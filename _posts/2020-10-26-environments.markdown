---
layout: post
title:  "What are virtual environments?"
date:   2020-10-26 21:03:36 +0530
categories: pipenv, venv, conda
---

## Definition
A virtual environment is an isolated container for Python projects. Think of them as folders where you can install a version of the Python interpreter, libraries, and their dependencies that are isolated from other folders (virtual environments) including those installed as part of your core operating system.


## Why do we need virtual environments?
Virtual environments are needed to ensure reproducibility of your Python project. The main reason for this is that Python, its frameworks, libraries, and packages are constantly being updated, this means that some functions are being added while others are being deprecated.
In other words, projects built using certain versions of the Python interpreter or libraries, might not work when run on systems that have other versions installed (e.g., you send your project to a co-worker who has different versions installed).
With virtual environments you can replicate the exact environment used when the project was created. 


## How to use virtual environments
There are several tools that allow you to create virtual environments, in this post I'll will focus on venv (as of Python 3, the venv module is part of the standard Python library)

To create an environment in the current folder type:

```
# Python 3
$ python -m venv *name_of_your_environment*
```

In order to use this environment we need to "activate" it. To do this run the following:

```
$ source *name_of_your_environment*/bin/activate
(env) $
```

Now we can install the libraries needed for our project using pip:

```
(env) $ pip install numpy
```

Once we are done installing all the libraries needed for our project we can use the following command to create a "requirements" file that indicate the versions of the libraries installed.

```
(env) $ pip freeze > requirements.txt
```

This file should be shared with the project and will allow other data scientists to replicate the exact environment.  If you received a requirements.txt file you can use the run the following to install the required libraries:

```
(env) $ pip install -r requirements.txt
```

Lastly if you are using Jupyter, you need to manually add a kernel with a different python version or virtual enviroment:

```
(env) $ pip install ipykernel
(env) $ python -m ipykernel install --name=*name_of_your_environment*
```

To go back to the normal shell session run and deactivate the current environment type:

```
(env) $ deactivate
$
```

## Further reading
* [Python virtual environments: a primer](https://realpython.com/python-virtual-environments-a-primer/)
* [Installing using pip and virtual environments](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)
* [Pipenv & Virtual Environments](https://docs.python-guide.org/dev/virtualenvs/)






