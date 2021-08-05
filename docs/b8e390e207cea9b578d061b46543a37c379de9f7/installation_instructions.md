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

**Advanced R users**: Update rgbif, paleobioDB, sf, and skip ahead to "Run the following lines in R" below

### Wallace v1.9 (bets testing of what will become v2!)
#### Run the following lines in R:
```{r}
#install the devtools package to help you install other things
install.packages("devtools")
library(devtools)
#install ENMeval pakcage
installpackages("ENMeval")
# Install Wallace from github
devtools::install_github("https://github.com/wallaceEcoMod/wallace/tree/multiSp")
# Open Wallace
library(wallace)
run_wallace()
```

### Wallace v2.x (beta testing of what will become v3!)
#### Install all necessary packages in their development versions. Agree to update all packages on installation.
**To install changeRangeR and maskRangeR (for new components)**
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

#### Install ENMeval
```{r}
install.packages("EMMeval")
```

### Install the development version of Wallace
```{r}
devtools::install_github("https://github.com/wallaceEcoMod/wallace/tree/biomodelos", dependencies = TRUE)
# Open Wallace
library(wallace)
run_wallace()
```

##### What is new in this version (v1.9)? 
[See this video for more information](https://www.youtube.com/watch?v=NRtKwtCansw)

**1. Stop and start your work whenever you want**: This version allows you to save a session partway through the workflow and then restart it. Try this out via the "Save Session" tab if you think this feature is of interest (intermediate-to-advanced users).

**2. Greater reproducibility regarding occurrence records**: As a step towards greater documentation and reproducibility in biodiversity informatics, this version of Wallace provides an option of querying GBIF and receiving a DOI for the data provided. If you are already a registered GBIF user, check the "Include Data Source Citations" option under the "Query Database (Present)" module of the **OccsData** component.

**3. Cross-time projections**: If you will later be interested in projecting your models to estimates of future (or past) climate, try out the updated **Project** component. This version now has data from WorldClim and EcoClimate (which also has reconstructed data for the past). Make your original model with the same climatic data source that you would like to use for projecting across time periods.

**4. Make models for multiple species in the same Wallace session**: This advancement supports two important other functionalities: comparisons of species in environmental space (See below) and the calculations of richness and endemism that we will see in the new R package changeRangeR. If you are interested in either of these, try making models for more than one species. To get the data to do this, in the **OccData** component, either run the query multiple times or do it once iwth scientific names separated by commas. Then, in later components use the pull-down menu in the top center of the interface to indicate the species with which you want to work.

**5. Environmental space comparisons**: It may not be as directly linked to conservation as many of the other advances, but this version now has several modules in the **EnvSpace** component, which allows users to examine characteristics of environmental space across species, such as niche overlap. If this matches your research interests (for academic purposes, or to study invasive species, for example), try them out.

**6. Redesigned R-markdown functionalities**: Because of the way this version of Wallace is redesigned, it now makes the documentation files in a new way (**Reproduce** component). In addition to making sure that you can download the documentation in ways readable to humans (like pdf), it would be helpful to the development team to have users download the executable RMD code and confirm that it runs successfully in R (intermediate-to-advanced users).

##### **Summary of new features**
- General - Several species in the same session
- General - New download sub-tab at each component
- General - Save and reload session
- Occs - PaleobioDB - Fossil occs (New module!)
- Occs - BIEN (New option!)
- Occs - GBIF OccCite (New option!)
- Occs - Delimitator and Separator (New option!)
- Envs - EcoClimate (New module, including paleo reconstructions!)
- General - Select variables with pickerInput
- General - Batch option (to repeat decisions for other species)
- Process Env - Draw polygon (New module!)
- Environmental Space - NEW COMPONENT with various new modules
- Model - maxnet and maxent.jar - Categorical variables (New option!)
- Model - maxnet and maxent.jar - Parallel (New option!)
- Vis - New bioclim plot
- Vis - New maxent plots
- Vis - mapPred - New threshold option
- Proj - userProj - User specified rasters
- Proj - user background extent (New Option!)
- Proj - user-specified projection extent (New option!)
- Proj - New Time - Ecolimate (New Option!)
- RMD - New Structure 
- Metadata - based on rangeModelMetadata package.


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