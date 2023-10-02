# About

These are notebooks for a training session on the [COSIMA Cookbook](https://cosima-recipes.readthedocs.io/en/latest/index.html) for a 2023 course on [HPC and Data in Computational Fluid Dynamics](https://intersect.org.au/education/collaborative-graduate-courses/3rd-collaborative-course/).

https://forum.access-hive.org.au/t/introduction-to-cosima-cookbook-data-explorer-and-access-nri-intake-catalog/1144

<div data-theme-toc="true"> </div>

# About

This is material to support a training session on the [COSIMA Cookbook](https://github.com/COSIMA/cosima-cookbook) using its Data Explorer component. The [ACCESS-NRI Intake catalog](https://forum.access-hive.org.au/c/access-workshop-2023/61) will also be introduced to show similar and complementary functionality.

This training is aimed at people who have never used (or have forgotten how to use) the [COSIMA Recipes](https://github.com/COSIMA/cosima-recipes) for accessing and analysing COSIMA model output.

The training will utilise the [NCI ARE](https://opus.nci.org.au/display/Help/ARE+User+Guide) (Australian Research Environment) [JupyterLab App](https://opus.nci.org.au/display/Help/3.+JupyterLab+App). This is user-friendly way to run Jupyter Notebooks at NCI, which makes it possible to access the data required for this training session.

# Who is this for?

Attendees of the COSIMA Workshop, a satellite meeting of the [ACCESS 2023 Community Workshop](https://forum.access-hive.org.au/c/access-workshop-2023/61). Attendees will need some familiarity with the python programming language. 

# Preparation Before Training Day

There are three prerequisites, two to access NCI resources, and one to get the jupyter python notebooks.

*All* perequisites need to be completed **WELL BEFORE** the day of training. We only have an hour for the training, and there will not be time to do administration *and* follow the training.

## NCI Account

You *must* have an NCI account linked to a project with remaining compute allocation. This training will require submitting a job to the NCI batch queuing system. Without remaining compute allocation your submitted job will never run.

If you aren't sure which project to use, ask your supervisor, colleagues or relevant local IT support.

If you do not have an NCI account follow the NCI [instructions to create one](https://opus.nci.org.au/display/Help/Setting+up+your+NCI+Account).

## NCI Projects 

To access the data you need to complete the tutorial you should make sure you are also a member of the following projects at NCI:

* `hh5`
* `ik11`
* `cj50`
* `xp65`
* `p73`
* `oi10`
* `jk72`
* `fs38`

<!-- The following are optional, but will allow you to access more datasets
* `al33`
* `rr3`
* `dk92`
-->

You can see the projects you are a member of at https://my.nci.org.au/mancini.

Or run this command on `gadi`
```
/scratch/public/COSIMA_tutorial/check_projects
```

## Get Notebooks

The training uses two notebooks in a `git` repository. You will need to download these notebooks to an NCI filesystem that is accessible to the ARE session you just started. The recommended location is your home directory on `gadi`, as this is always accessible to an ARE JupyterLab session.

To do this log in to `gadi` and copy and paste this command:
```
git clone git@github.com:ACCESS-Hive/cosima-training-workshop-2023.git
```
This will have created a directory called `cosima_training` in your gadi home directory. 

# Training Session

## Start ARE JupyterLab Session

This will be the first thing we do at the training session, but feel free to test this out before the training day to check it is all working correctly for you.

The [instructions from the ACCESS-NRI Intake catalogue docs](https://access-nri-intake-catalog.readthedocs.io/en/latest/usage/how.html#using-the-catalog-on-the-are) are excellent and worth reading for background, and of course the [NCI ARE Documentation](https://opus.nci.org.au/display/Help/ARE+User+Guide) is also available.

Steps:
1. Log in to ARE using your NCI username and password: https://are.nci.org.au

![ARE|690x468, 50%](upload://831Tl4SXxv1HTBDLnfHD8XtyEmP.png)

2. Select the JupyterLab app

![icon|440x440, 50%](upload://uiwvajTDrrxLVqhmAybSTwAhHdF.png)


For this training here are some recommended settings for your ARE session that have been tested and will work:
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
gdata/hh5+gdata/ik11+gdata/cj50+gdata/xp65+gdata/p73+gdata/oi10+gdata/dk92+gdata/fs38+scratch/public
```
Note: you can hover over the box above, and click on the icon in the top right corner to copy it into your buffer and then paste it into the ARE window.

Click on "Advanced Settings" and set the following options

**Module directories**
```
/g/data/hh5/public/modules
```

**Modules**
```
conda/analysis3-unstable
```
Note: can cut and paste these using the shortcut mentioned above.

Push the submit button and then you will have a window that looks something like this:

![ARE_queue|690x246](upload://1KMmWJaFqGF4TaVUjgENgOdZTli.png)

You may wait a few minutes for your queued job to start running, which is where your JupyterLab application runs.

When your JupyterLab session is ready the screen will change, an "Open JupyterLab" button. Push it and your JupyterLab session will open in a new window.

![JupyterLab_ready|690x287](upload://puxjZ11pRjXtk9SNbUjDJZbi5Hz.jpeg)


## Find Tutorial Notebooks

In the JupyterLab window use the file browser to navigate to the directory where you downloaded the jupyter notebook files in the preparation section above. Double-click on the `home` directory in the file browser:
![jupyterlab_filebrowser|540x500, 75%](upload://8ecBWfgaKuDBRJiKjlptr1SSHXg.png)

and then double-click on the `cosima-training-workshop-2023` directory.

## Notebook 1: Finding COSIMA Data

The [first notebook](https://github.com/ACCESS-Hive/cosima-training-workshop-2023/blob/main/Finding_COSIMA_data.ipynb) covers using the explorer tools in the COSIMA Cookbook database to find data.

## Notebook 2: Comparing Sea Surface Height Data

In the [second notebook](https://github.com/ACCESS-Hive/cosima-training-workshop-2023/blob/main/Sea_level.ipynb) you'll use what you've learned from the first part to load sea surface height data, do some calculations and plot the result.

## Notebook 3: Introducing the ACCESS-NRI Intake Catalog

If there is time, or for those who are particularly interested, the [third notebook](https://github.com/ACCESS-Hive/cosima-training-workshop-2023/blob/main/Intake.ipynb)  is a very short introduction to the [ACCESS-NRI Intake Catalogue](https://access-nri-intake-catalog.readthedocs.io/en/latest/). The catalog was developed by @dougiesquire. 

The aim is to show similarities and how the cookbook and intake catalog can be complementary: how the same load operation is done with the ACCESS-NRI Intake catalog, and what other datasets are available via the Intake catalog.

# Clean-up

When finished make sure you save your work, close the tab and then Delete your running JupyterLab app, otherwise it will continue to consume compute resources and eventually stop when it reaches the walltime limit.

You are free to keep the notebooks you've been working on for reference. If you no longer want them you can use
```bash
rm -rf cosima-training-workshop-2023
```
but BE CAREFUL with `rm -rf`. This will happily recursively delete your entire directory tree if given the wrong arguments (or right, if that is what you want to do).

# Conclusion

Hopefully you now know how to find COSIMA data, load it and do some meaningful analysis. Also you can now use the explorer to locate data, and learn the syntax for loading data in your own notebooks.

If there was time maybe you've learnt a bit how the intake catalogue works, how it is different to the COSIMA Cookbook, and complimentary.
