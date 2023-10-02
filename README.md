# About

This is material for a tutorial on the [COSIMA Cookbook](https://github.com/COSIMA/cosima-cookbook) for a 2023 Intersect course on [HPC and Data in Computational Fluid Dynamics](https://intersect.org.au/education/collaborative-graduate-courses/3rd-collaborative-course/). It borrows very heavily from Aidan Heerdegen's [training workshop](https://github.com/ACCESS-Hive/cosima-training-workshop-2023) and associated [hive post](https://forum.access-hive.org.au/t/introduction-to-cosima-cookbook-data-explorer-and-access-nri-intake-catalog/1144) (thanks Aidan!)

This tutorial is aimed at people who have some familiarity with the Python programming language but have never used the [COSIMA Recipes](https://github.com/COSIMA/cosima-recipes) for accessing and analysing COSIMA model output.

The tutorial will use the [NCI ARE](https://opus.nci.org.au/display/Help/ARE+User+Guide) (Australian Research Environment) [JupyterLab App](https://opus.nci.org.au/display/Help/3.+JupyterLab+App). This is user-friendly way to run Jupyter Notebooks at NCI, which makes it possible to access the data required for this tutorial.

# Preparation Before Tutorial Day

There are three prerequisites, two to access NCI resources, and one to get the jupyter python notebooks.

*All* perequisites need to be completed **WELL BEFORE** the day of tutorial. We only have 90 min for the tutorial, and there will not be time to do administration *and* follow the tutorial.

## NCI Account

You *must* have an NCI account linked to a project with remaining compute allocation. This tutorial will require submitting a job to the NCI batch queuing system. Without remaining compute allocation your submitted job will never run.

If you aren't sure which project to use, ask your supervisor, colleagues or relevant local IT support.

If you do not have an NCI account follow the NCI [instructions to create one](https://opus.nci.org.au/display/Help/Setting+up+your+NCI+Account).

## NCI Projects 

To access the data you need to complete the tutorial you should make sure you are also a member of the following projects at NCI:

* `hh5`
* `ik11`
* `cj50`

You can see the projects you are a member of at https://my.nci.org.au/mancini.

## Get Notebooks

The tutorial uses two notebooks in a `git` repository. You will need to download these notebooks to an NCI filesystem. The recommended location is your home directory on `gadi`, as this is always accessible to an ARE JupyterLab session.

To do this log in to `gadi` and copy and paste this command:
```
git clone https://github.com/aekiss/HPC-Data-CFD-2023.git
```
This will have created a directory called `HPC-Data-CFD-2023` in your gadi home directory. 

# Tutorial Session

## Start ARE JupyterLab Session

This will be the first thing we do in the tutorial, but feel free to test this out before the tutorial day to check it is all working correctly for you.

The [instructions from the ACCESS-NRI Intake catalogue docs](https://access-nri-intake-catalog.readthedocs.io/en/latest/usage/how.html#using-the-catalog-on-the-are) are excellent and worth reading for background, and of course the [NCI ARE Documentation](https://opus.nci.org.au/display/Help/ARE+User+Guide) is also available.

Steps:
1. Log in to ARE using your NCI username and password: https://are.nci.org.au

![ARE|690x468, 50%](upload://831Tl4SXxv1HTBDLnfHD8XtyEmP.png)

2. Select the JupyterLab app

![icon|440x440, 50%](upload://uiwvajTDrrxLVqhmAybSTwAhHdF.png)


For this tutorial there are some recommended settings for your ARE session that have been tested and will work:
|||
|--|--|
|Walltime|2 hours|
|Queue|normalbw|
|Compute Size|Medium|
|Project| *choose one*|
|Storage| *see below* |

You must *choose one* of the projects you have available to you. This must be a project with compute allocation remaining as discussed above in prerequisites.

The storage section *must* contain all the `/g/data` projects you need to access. Use the following to include all the projects specified above:
```
gdata/hh5+gdata/ik11+gdata/cj50+scratch/public
```

Click on "Advanced Settings" and set the following options

**Module directories**
```
/g/data/hh5/public/modules
```

**Modules**
```
conda/analysis3-unstable
```

Push the submit button and then you will have a window that looks something like this:

![ARE_queue|690x246](upload://1KMmWJaFqGF4TaVUjgENgOdZTli.png)

You may wait a few minutes for your queued job to start running, which is where your JupyterLab application runs.

When your JupyterLab session is ready the screen will change, an "Open JupyterLab" button. Push it and your JupyterLab session will open in a new window.

![JupyterLab_ready|690x287](upload://puxjZ11pRjXtk9SNbUjDJZbi5Hz.jpeg)


## Find Tutorial Notebooks

In the JupyterLab window use the file browser to navigate to the directory where you downloaded the jupyter notebook files in the preparation section above. Double-click on the `home` directory in the file browser:
![jupyterlab_filebrowser|540x500, 75%](upload://8ecBWfgaKuDBRJiKjlptr1SSHXg.png)

and then double-click on the `HPC-Data-CFD-2023` directory.

## Notebook 1: Finding COSIMA Data

The [first notebook](https://github.com/aekiss/HPC-Data-CFD-2023/blob/main/Finding_COSIMA_data.ipynb) covers using the explorer tools in the COSIMA Cookbook database to find data.

## Notebook 2: Comparing Sea Surface Height Data

In the [second notebook](https://github.com/aekiss/HPC-Data-CFD-2023/blob/main/Sea_level.ipynb) you'll use what you've learned from the first part to load sea surface height data, do some calculations and plot the result.

# Clean-up

When finished make sure you save your work, close the tab and then Delete your running JupyterLab app, otherwise it will continue to consume compute resources and eventually stop when it reaches the walltime limit.

You are free to keep the notebooks you've been working on for reference. If you no longer want them you can use
```bash
rm -rf HPC-Data-CFD-2023
```
but BE CAREFUL with `rm -rf`. This will happily recursively delete your entire directory tree if given the wrong arguments (or right, if that is what you want to do).

# Conclusion

Hopefully you now know how to find COSIMA data, load it and do some meaningful analysis. Also you can now use the explorer to locate data, and learn the syntax for loading data in your own notebooks.
