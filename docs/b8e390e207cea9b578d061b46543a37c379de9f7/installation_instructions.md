# Instructions for Installation of dependencies for Wallace Version 3

### **1. Installing R and RStudio for beginner R users**
R is an open-source statistical software package that has the ability to do GIS operations among many other things. We use it in conjunction with RStudio, an easy way to manage R code.

To download R([Windows](https://cran.r-project.org/bin/windows/base/), [Mac](https://cran.rstudio.com/bin/macosx/))<br>
            
To download [RStudio](https://www.rstudio.com/products/rstudio/download/). Install RStudio Desktop (Free, Open Source) accepting the default pathways.<br>

Now, you will need to tell RStudio where R lives. Open RStudio, go to Tools -> Global Options and change the R version by navigating to where you saved R. Unless you have a reason against it, you should use the 64 bit version of R (64 and 32 bit R are both downloaded).

**If you are a Windows user, please also install RTools from here - (*even if you have already installed R*)**<br>
https://cran.r-project.org/bin/windows/Rtools/ (choose 64 bit unless you have a reason not to). And follow the steps under "Putting Rtools on the PATH".

### **2. Before loading Wallace, update R and R packages:**
**Beginner R users**: Please update or install the latest version of R (v4.x) and update all packages (in RStudio, go to tools - check for package updates) before starting with the installation steps below. 

**Advanced R users**: Update rgbif, paleobioDB, sf.

### **To install changeRangeR and maskRangeR (for new components)**
##### Wallace v2.x (beta testing of what will become v3)
  + ##### A. Install all necessary packages in their development versions. Agree to update all packages on installation.

```{r}
install.packages("devtools")
devtools::install_github("cmerow/maskRangeR/maskRangeR", dependencies=TRUE)
devtools::install_github("https://github.com/andrepazv/changeRangeR", dependencies= TRUE)
# load packages
library(maskRangeR)
library(changeRangeR)
```

** NOTE **: If you have issues installing changeRangeR because of path length, use:
```{r}
devtools::install_github("https://github.com/andrepazv/changeRangeR/tree/paths_fix2", dependencies= TRUE)
# Load packages
library(changeRangeR)
```

If you have issues with changeRangeR because of parallelsugar:
```{r}
devtools::install_github("nathanvan/parallelsugar")
devtools::install_github("https://github.com/andrepazv/changeRangeR/tree/paths_fix2", dependencies= TRUE)
# Load package
library(changeRangeR)
```

  + #### B. Install ENMeval
```{r}
install.packages("EMMeval")
```

  + #### C. Install the development version of Wallace
```{r}
devtools::install_github("https://github.com/wallaceEcoMod/wallace/tree/biomodelos", dependencies = TRUE)
# Open Wallace
library(wallace)
run_wallace()
```

##### What is new in future v3.0?
It incorporates several components for conservation analyses based on functionalities of the packages maskRangeR and changeRangeR.
- EOO and AOO estimation
- Masking of SDMs with shapefiles (e.g. protected areas)
- Adding or removing areas from SDM based on expert knowledge
- Plotting changes in distribution through time given interventions (e.g. deforestation)
- Representation of distribution in polygons (e.g protected areas)
- Mapping species richness and species endemism

#### Important note!
After testing the development versions of Wallace, if you want to go back to the older version, you need to reinstall Wallace and ENMeval from CRAN. You can use the following code:
```{r}
install.packages(c("wallace", "ENMeval"))
```

### Report bugs
If you find a bug, let us know!
If you have a Github account, you can report issues [here](https://github.com/wallaceEcoMod/wallace/issues) <br>
You can email the [Wallace Google Group](https://groups.google.com/g/wallaceEcoMod) using the subject [installation]. <br>
If you have another suggestion, please write to the Wallace email (wallaceEcoMod@gmail.com), specifying that you have been testing the development version.

### Do you want to know more about Wallace?
Please visit our [website](https://wallaceecomod.github.io/).