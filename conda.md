# Installing and using conda

## Contents
---

- [Introduction](#intro)
- [Installation](#install)
- [Info](#info)
- [Environments](#enviro)
- [Maintenance](#maint)





<a id="intro"></a>

### Introduction

------------------------------------------------

Conda is a cross platform tool for managing Python environments and packages.
Instead of using the system Python, it allows you to install and run both Python 2.7 and Python 3.5.
You can create an environment for each Python project and install different packages or versions of
packages in each environment. This eliminates cross project dependency issues.
Conda is also useful for exporting an environment from one system and importing it on another system.
Full documentation is available at the [official conda documentation](http://conda.pydata.org/docs/index.html) page.
A [conda pdf cheatsheet](http://conda.pydata.org/docs/_downloads/conda-cheatsheet.pdf) is also available.
The commands and options below are the ones I've found to be most useful.



<a id="install"></a>

### Installation

-------------------------------

Download and run the conda [installer](http://conda.pydata.org/miniconda.html) (Windows, Mac, or Linux).



<a id="info"></a>

### Info and help

-------------------------------

```
Note: Packages or the Python distribution installed in the current environment are marked with an asterisk.
```

| Command                                          | Description          |
| :------------------------------------------------- | :------------------- |
| __conda help__                 		     | show available conda commands |
| __conda help [command]__                 	     | more detailed help and options for that command or package |
| __conda info -a__                 		     | displays all info about the current conda install |
| __conda info -e__                 		     | displays conda environments. The current environment is marked with an asterisk |
| __conda search searchString__                     | Search for packages with "searchString" in the name. <br> Or search online at: [https://docs.continuum.io/anaconda/pkg-docs](https://docs.continuum.io/anaconda/pkg-docs) |
| __conda search -f Python__			    | list available Python distributions. |


<a id="enviro"></a>

### Environments

-------------------------------


| Command                                          | Description          |
| :------------------------------------------------- | :------------------- |
| __conda list__                 		     | list installed packages for the current environment |
| __conda list -n environmentA__                     | list installed packages for "environmentA" |
| __conda list -e > packagesA.txt__                   | export package list to a file for the current environment |
| __conda install -n environmentA package1 package2__      | Install package1 and package2 in environmentA. <br> conda will try to install the latest version of the packages. It may update existing packages and install additional required packages. <br> a useful option is __-- dry-run__ |
| __conda create -n myEnviro python=2.7 numpy notebook__	| create a new environment called myEnviro with python 2.7 and install numpy and jupyter notebook packages at the same time |
| __conda create -n environmentB --file packagesA.txt --file pack2.txt__  | create a new environment with packages from multiple export files <br> note __--file__ is "- - file" |
| __conda env export -n environmentA__               | list installed packages for environmentA, including pip installed packages <br> requires conda-env package |
| __conda env export -n environmentA > enviroA.yml__ | export environmentA to YAML file |
| __conda env create -f path/to/enviroA.yml -n newEnviroName__               | create an environment from YAML file with optional new name |
| __source activate myEnviro__				| switch to the myEnviro environment |
| __source deactivate__					| end the current environment and return to the root environment |


<br>

If a conda package is not available, try using pip to install a package to your conda environment.

  1. source activate myEnviro
  2. ```pip install packageName```
  or
  ```python setup.py install```



	# verify path of python executable installed in a conda environment
	import sys
	sys.executable

	# verify installed packages in your environment
	import pip
	sorted(["%s==%s" % (i.key, i.version) for i in pip.get_installed_distributions()])










<a id="maint"></a>

### Maintenance

-------------------------------


| Command                                          | Description          |
| :------------------------------------------------- | :------------------- |
| __conda update -n myEnviro --all --dry-run__ 		| update conda all packages for the myEnviro environment |
| __conda update numpy --dry-run__			| update the numpy package for the current environment |
| __conda update python__				| update python for the current environment |
| __conda update conda__				| update conda itself |
| __conda clean -a --dry-run__				| remove all unused packages and caches |
| __conda remove --dry-run mayavi__			| remove a list of packages from the current environment |
| __conda remove -n envName -all__			| remove an environment |
