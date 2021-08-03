# Instructions for Installation of dependencies for our Wallace-BioModelos 3 Workshop
Thank you for joining!

**Beginner R users**: Please update to the latest version of R (v4) and update all packages (in R Studio go to tools - check for package updates) before starting with the installation steps below. For more information on installing R and R studio - see more instructions below, and please reach out to the workshop organizers for help during our zoom office hours and on our Slack channel (links in the installation instructions email) - Tambien hablamos espanol!.

**Advanced R users**: Update rgbif, paleobioDB, sf, and skip ahead to "Run the following lines in R" below

**More details on installing R and RStudio for beginner R users:**<br>
R is an open-source statistical software package that has the ability to do GIS operations among many other things. We use it in conjunction with RStudio, an easy way to manage R code.

To download R([Windows](https://cran.r-project.org/bin/windows/base/), [Mac](https://cran.rstudio.com/bin/macosx/))<br>
            
To download [RStudio](https://www.rstudio.com/products/rstudio/download/). Install RStudio Desktop (Free, Open Source) accepting the default pathways.<br>

Now, you will need to tell RStudio where R lives. Open RStudio, go to Tools -> Global Options and change the R version by navigating to where you saved R. Unless you have a reason against it, you should use the 64 bit version of R (64 and 32 bit R are both downloaded).

**If you are a Windows user, please also install RTools from here - (*even if you have already installed R*)**<br>
https://cran.r-project.org/bin/windows/Rtools/ (choose 64 bit unless you have a reason not to). And follow the steps under "Putting Rtools on the PATH".

Now continue to "Run the following lines", below.

**Another note for beginners**: Also, if you previously installed and used Wallace or ENMEval last year and regularly save your workspace environment, please clear your R Studio workspace environment (using the broom icon on the right side). Then, exit RStudio and when prompted save the (now cleaned) workspace, and open RStudio again before proceeding with the steps below (in the future. don't save your workspace environment).


#### Run the following lines in R:
```{r}
#install the devtools package to help you install other things
install.packages("devtools")
library(devtools)
#install the dev version of ENMeval
install_github("https://github.com/bobmuscarella/ENMeval/tree/dev", dependencies = TRUE, force = TRUE)
# if you are asked about whether or not to update or install new packages, say yes install all (1), and after that, if you are asked if you want to install new packages that need to be compiled from binaries, say no, which means you choose to install the older version (like systemfonts)
# if installation failed, check the error message; it is probably because of other dependencies (like gbm, randomForest) that need to be installed, please install them and then try to install enmeval again now, install the dev version of occCite
install_github("https://github.com/hannahlowens/occCite", dependencies = TRUE, force = TRUE)
#install maskRangeR
devtools::install_github("cmerow/maskRangeR/maskRangeR")
# install changeRangeR
devtools::install_github("cmerow/changeRangeR")
#if this doesn't work - especially if you are on windows - try this:
devtools::install_github("cmerow/changeRangeR", build = FALSE, force = T)
#check that both of these installations worked
library(maskRangeR)
library(changeRangeR)
# now install the Wallace v 2 dev version
install_github("https://github.com/wallaceEcoMod/wallace/tree/multiSp", dependencies = TRUE, force = TRUE)
# if you are asked about whether or not to install a package that needs to be compiled from binaries, say no, which means you choose to >install the older version (like systemfonts)
#now, load Wallace to test that it works
library(wallace)
run_wallace()
#This should open Wallace - **please let us know via the Slack channel or email as soon as you have successfully gotten to this point. Remember if you are having trouble, please come to our installation office hours or reach us on the Slack channel.**
#Stop here - We will run one more line of code at the beginning of the workshop for you to install the "BioModelos" version of Wallace. Thank you for installing all of these first, to make the installation of the BioModelos version much faster. Please remember to also download all of the workshop datasets from the link on the workshop homepage.
#Note: if you want to use the more stable version of wallace for teaching or for your work after our workshop, you will need to reinstall the stable version from CRAN.
```

Before the workshop, please reinstall the newest Wallace- BioModelos version to get the latest updates!
```{r}
devtools::install_github("https://github.com/wallaceEcoMod/wallace/tree/biomodelos", dependencies = TRUE, force = TRUE)
library(wallace)
run_wallace(biomodelos=TRUE)
```


