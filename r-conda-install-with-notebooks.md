# R installation with Jupyter Notebooks

Below we go through the steps (the main section below as tested on a mac) to install an R notebook infrastructure using the jupyter notebook approach.

There are some slightly modified instructions for windows further below.

Once you worked through the steps below you should be able to make new R notebooks from the Jupyter `New Notebook` menu which should allow you to select `R`, i.e. to open a new R notebook.

## Creating the environment and basic conda installs

```
conda create -n r-stats
conda activate r-stats

conda install -c conda-forge r-recommended
conda install -c conda-forge r-ggplot2
```

## Install some packages using R

Below we install a few extra packages that are useful for plotting and a few other tasks. Rather than using `conda` which seems to be hit-and-miss in working properly for some of the packages, we use use R's builtin `install.packages` command. Below this shown as carried out from the (mac) command line, but one can also do this from an R command line directly (e.g. in an RStudio session) and then type at the R command line `install.packages("xxxx")` where `xxxx` is a placeholder for the actual package name, see examples bow.

### [Optional] Startup setting to avoid having to choose CRAN mirror location each time

As explained in [this post](https://stackoverflow.com/questions/11488174/how-to-select-a-cran-mirror-in-r), it can be useful to set the default repo to autoselect from a close mirror. Otherwise, one always has to manually select a local Swiss mirror from a long list, before the command would execute, in every new R session. To avoid this one can add the following code to `$HOME/.Rprofile`:

```R
## Default repo
local({r <- getOption("repos")
       r["CRAN"] <- "https://cloud.r-project.org" 
       options(repos=r)
})
```

Presumably this should work on windows as well, provided one creates the file in the directory specified in the `$HOME` environment variable. See also this [stackoverflow post](https://stackoverflow.com/questions/46819684/how-to-access-and-edit-rprofile).

### Packages for quasirandom point plotting

```
R -e 'install.packages("beeswarm")'
R -e 'install.packages("ggbeeswarm")'
```

### Packages for plotting several panels

```
R -e 'install.packages("patchwork")'
```

### Package lawstat: Tools for Biostatistics, Public Policy, and Law

```
R -e 'install.packages("lawstat")'
```

### Package plyr: Tools for Splitting, Applying and Combining Data

```
R -e 'install.packages("plyr")'
```

## Conda install of jupyter support and register R kernel

For this last part we are switching back to using `conda`. It seems pretty hassle-free and has always worked when we tried it.

```
conda activate r-stats # activate r-stats env if not already done
conda install -c conda-forge jupyter
conda install -c conda-forge r-irkernel
R -e 'IRkernel::installspec()'
```

# Tweaks for Windows

On windows we need a slightly tweaked set of instructions, listed compactly below.

	conda create -n r-stats
	conda activate r-stats
	conda install -c conda-forge r-recommended
	conda install -c conda-forge r-ggplot2

### Set the default CRAN mirror

Now we briefly follow [these instructions](https://stackoverflow.com/questions/46819684/how-to-access-and-edit-rprofile) to edit .Rprofile. In particular, open an R command line, and then issue this command:

	file.edit(file.path("~", ".Rprofile")) # edit .Rprofile in HOME

This brings up notepad and you can paste the recommended text into .Rprofile:

	## Set Default CRAN mirror
	local({r <- getOption("repos")
       	r["CRAN"] <- "https://cloud.r-project.org" 
       	options(repos=r)
	})

Now carry on with the rest of install.

### Remainder of Windows install

Note windows specific quotes which need to be as shown below, the mac style quotations do not work!


	R -e "install.packages('beeswarm')"
	R -e "install.packages('ggbeeswarm')"
	R -e "install.packages('patchwork')"
	R -e "install.packages('lawstat')"
	R -e "install.packages('plyr')"
	conda install -c conda-forge jupyter
	conda install -c conda-forge r-irkernel
	R -e IRkernel::installspec()


Now you can change directory to your top level notebook directory

	cd top_dir_where_notebooks_reside
	jupyter notebook # open notebook server for R notebooks

The file interface that comes up allows you to open existing `R` notebooks and create new ones.
