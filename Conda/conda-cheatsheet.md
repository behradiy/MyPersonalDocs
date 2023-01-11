
# CONDA CHEAT SHEET
###     
### copied from [here](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)
------
> #### **Conda** (also known as Anaconda) is a Command line *package* and *environment* manager. Using Venvs helps us to resolve and share our dependencies easier. Learn these conda commands in 30 minutes and never dought it again.


TIP: Anaconda Navigator is a graphical interface to use conda but we can't be sure if we have access to Navigator all the time. so it's better to learn conda commands.

<mark> => Conda Basics</mark>

| Description | Command |
| ----------- | ----------- |
| Verify conda is installed, check version number | 
`conda info` |
| install a pacakage **included in andaconda** | `conda install PACKAGENAME` |
| Update any installed app | `conda update PACKAGENAME` |
| Command line help | `conda install --help` |

<mark> => Using environments</mark>
| Description | Command |
| ----------- | ----------- |
| Create a new env named py35, install Python 3.5 | `conda create --name py35 python=3.5` |
| Activate the env you made | `conda activate ENVNAME` |
| Deactivate the env you're in | `conda deactivate` |
| Get a list of all environments, active one is marked with a * | `conda env list` |
| Make a exact copy of an environment | `conda create --clone py35 --name py35-2` |
| List all the packages installed on the env you're in | `conda list` |
| List the history of each change to the current env | `conda list --revisions` |
| Restore environment to a previous revision | `conda install --revision 2 conda` |
| Save environment to a text file | `conda list --explicit > py35-env.txt` |
| Delete an envinroment and everything in it | `conda env remove --name py35` |
| Create env from a text file | `conda env create --file py35.txt` |

<mark> => Conda packages</mark>

| Description | Command |
| ----------- | ----------- |
| Use conda to search for a package | `conda search PACKAGENAME` |
| Installing Package (toolz) into a different env (py29) | `conda install --name py29 toolz` |
| Installing PyPi Package into current active enviroment | `pip install PACKAGENAME` |
| Removing one or more (toolz, pandas) from a specific environment (py35) | `conda remove --name py35 toolz pandas` |
------------
