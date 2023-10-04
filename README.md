# About

This is material for a tutorial on the [COSIMA Cookbook](https://github.com/COSIMA/cosima-cookbook) for a 2023 Intersect course on [HPC and Data in Computational Fluid Dynamics](https://intersect.org.au/education/collaborative-graduate-courses/3rd-collaborative-course/). It borrows very heavily from Aidan Heerdegen's [training workshop](https://github.com/ACCESS-Hive/cosima-training-workshop-2023) and associated [hive post](https://forum.access-hive.org.au/t/introduction-to-cosima-cookbook-data-explorer-and-access-nri-intake-catalog/1144) (thanks Aidan!)

This tutorial is aimed at people who have some [familiarity with the Python programming language](https://docs.python.org/3/tutorial/index.html) but have never used the [COSIMA Recipes](https://github.com/COSIMA/cosima-recipes) for accessing and analysing COSIMA model output.

The tutorial will use the [NCI ARE](https://opus.nci.org.au/display/Help/ARE+User+Guide) (Australian Research Environment) [JupyterLab App](https://opus.nci.org.au/display/Help/3.+JupyterLab+App). This is user-friendly way to run Jupyter Notebooks at NCI, which makes it possible to access the data required for this tutorial.

The tutorial will provide hands-on experience in
* using [Python](https://docs.python.org/3/tutorial/index.html) in the [JupyterLab App](https://opus.nci.org.au/display/Help/3.+JupyterLab+App) environment on [NCI ARE](https://opus.nci.org.au/display/Help/ARE+User+Guide)
* accessing and manipulating data with the [Xarray](https://docs.xarray.dev/en/stable/index.html) package
* using [Dask](https://www.dask.org/) to accelerate your analysis and handle larger datasets
* using the [COSIMA Cookbook](https://github.com/COSIMA/cosima-cookbook), [Data Explorer](https://cosima-recipes.readthedocs.io/en/latest/Tutorials/Using_Explorer_tools.html#Exploring-a-Cookbook-Database) and [COSIMA Recipes](https://github.com/COSIMA/cosima-recipes)

# Preparation Before Tutorial Day

There are three prerequisites, two to access NCI resources, and one to get the jupyter python notebooks.

*All* perequisites need to be completed **BEFORE** the tutorial. We only have 90 min for the tutorial, and there will not be time to do administration *and* follow the tutorial.

## NCI Account

You *must* have an NCI account. If you do not have an NCI account, follow the NCI [instructions to create one](https://opus.nci.org.au/display/Help/Setting+up+your+NCI+Account).

## NCI Projects 

This tutorial will require membership of particular projects at NCI. To participate you will need to follow the instructions sent by Meiyun. 
_Please **don't** request membership of these projects directly through Mancini._ You will be sent 3 project membership invitations which you need to accept **WELL BEFORE** the tutorial.

<!--
This tutorial will require submitting a job to the NCI batch queuing system, so you need to be a member of a project that has a compute allocation. Without remaining compute allocation your submitted job will never run. Project `nf47` has been set up for this purpose - please check that you are a member at https://my.nci.org.au/mancini.
To access the data and COSIMA Cookbook you will need to **fill in the form emailed by Meiyun, before 5pm AEDT 4th Nov**. This will give you membership of projects `hh5`, `ik11` and `cj50`. Please _don't_ request membership of these projects directly through Mancini.
-->

## Get Notebooks

The tutorial uses some notebooks in a `git` repository. You will need to download these notebooks to an NCI filesystem. The recommended location is your home directory on `gadi`, as this is always accessible to an ARE JupyterLab session.

To do this, log in to `gadi` and copy and paste this command:
```
git clone https://github.com/aekiss/HPC-Data-CFD-2023.git
```
This will have created a directory called `HPC-Data-CFD-2023` in your gadi home directory. 

Note: this repository is being updated, so you may need to clone a fresh version of this repository (or do a `git pull`, if you know about git) just prior to the tutorial.

# Tutorial Session

## Start ARE JupyterLab Session

This will be the first thing we do in the tutorial, but feel free to test this out before the tutorial day to check it is all working correctly for you.

The [instructions from the ACCESS-NRI Intake catalogue docs](https://access-nri-intake-catalog.readthedocs.io/en/latest/usage/how.html#using-the-catalog-on-the-are) are excellent and worth reading for background, and of course the [NCI ARE Documentation](https://opus.nci.org.au/display/Help/ARE+User+Guide) is also available.

Steps:
1. Log in to ARE using your NCI username and password: https://are.nci.org.au

![ARE|690x468, 50%](https://global.discourse-cdn.com/business7/uploads/access1/optimized/1X/38691708aadd177bc3929710588bc1ed23907107_2_345x234.png)

2. Select the JupyterLab app

![icon|440x440, 50%](https://global.discourse-cdn.com/business7/uploads/access1/original/1X/d459475f86a3914789ea7eed0e3595786604b373.png)


For this tutorial there are some recommended settings for your ARE session that have been tested and will work:
|||
|--|--|
|Walltime|2 hours|
|Queue|normalbw|
|Compute Size|Medium|
|Project| *choose one, e.g. `nf47`*|
|Storage| *see below* |

You must *choose one* of the projects you have available to you. This must be a project with compute allocation remaining as discussed above in prerequisites.

The storage section *must* contain all the `/g/data` projects you need to access. Use the following for this tutorial:
```
gdata/hh5+gdata/ik11+gdata/cj50
```

Click on "Advanced Settings" and set the following options:

**Module directories**
```
/g/data/hh5/public/modules
```

**Modules**
```
conda/analysis3
```

Push the Launch button and then you will have a window that looks something like this:

![ARE_queue|690x246](https://global.discourse-cdn.com/business7/uploads/access1/optimized/1X/0c4be97188937a9867b9917ea4ea143f212d0e2c_2_690x246.png)

You may need to wait a few minutes for your queued job to start running, which is where your JupyterLab application runs.

When your JupyterLab session is ready the screen will change, with an "Open JupyterLab" button. Push it and your JupyterLab session will open in a new window.

![JupyterLab_ready|690x287](https://global.discourse-cdn.com/business7/uploads/access1/optimized/1X/b2aa0d0e4390936681865bcb3930dd693c564ee1_2_690x287.jpeg)


## Find Tutorial Notebooks

In the JupyterLab window use the file browser to navigate to the directory where you downloaded the jupyter notebook files in the preparation section above. Double-click on the `home` directory in the file browser:

![jupyterlab_filebrowser|540x500, 75%](https://global.discourse-cdn.com/business7/uploads/access1/optimized/1X/39ac6a14fa5b588a322e7f327839fa2dcf193ed6_2_405x375.png)

and then double-click on the `HPC-Data-CFD-2023` directory.

## Familiarisation with the JupyterLab interface

If you've never used Jupyter or JupyterLab before, you might like to look at [this overview of the interface](https://jupyterlab.readthedocs.io/en/stable/user/interface.html) and [how to use notebooks](https://jupyterlab.readthedocs.io/en/stable/user/notebook.html).

### Creating a new notebook
* Click the big blue + button at the top of the file browser (see image above).
* Click `Python [conda env:analysis3-23.04] *` in the Notebook category. This opens a new untitled Python notebook (running with a specific package environment). You can change the notebook name by right-clicking the notebook tab or in the file browser.
* There will be a code cell at the top. Type `1+1` in it, hold down shift and press return. **Shift-return will evaluate a cell** (rather than creating a new line in the cell), print the result, and give you a new code cell in which you can try out other Python commands. You can go back and change cells and re-evaluate them with shift-click. Cells can also be rearranged, duplicated and deleted.
* You can change a cell type from Code to Markdown using the dropdown menu. Markdown cells can be used to create comments and explanations of your code and analysis, including URLs, images and tables, and also mathematical markup in Latex. Try out some of the examples [here](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html).
  
## Notebook 1: Finding COSIMA Data

The [first notebook](https://github.com/aekiss/HPC-Data-CFD-2023/blob/main/Finding_COSIMA_data.ipynb) covers using the explorer tools in the COSIMA Cookbook database to find data.

## Notebook 2: Comparing Sea Surface Height Data

In the [second notebook](https://github.com/aekiss/HPC-Data-CFD-2023/blob/main/Sea_level.ipynb) you'll use what you've learned from the first part to load sea surface height data, do some calculations and plot the result.

# Clean-up

When finished make sure you save your work, close the tab and then Delete your running JupyterLab app, otherwise it will continue to consume compute resources and eventually stop when it reaches the walltime limit.

# Conclusion

Hopefully you now know how to find COSIMA data, load it and do some meaningful analysis. Also you can now use the explorer to locate data, and learn the syntax for loading data in your own notebooks.
