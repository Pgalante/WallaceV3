## Wallace Version 3 beta-testing instructions

If you are a twitter user, **please use our hashtag #WallaceEcoMod** to tweet about your work.


* ### **Wallace v3**
  + ##### [Wallace installation instructions](installation_instructions.md)
  + ##### Resources
    + **Wallace Version 1**<br>
      + [Tutorial](https://wallaceecomod.github.io/vignettes/wallace_vignette.html)


* ### Data
  + Please use the links below for prepared demonstration data <br>
**Prepared datasets**<br>
[Download prepared Datasets](Data.md)<br><br>


* #### **"Mask" component (new)**
  + ##### **About:**
  + The *Mask* tab allows users to post-process the SDM you made in Wallace, or imported in the UserSDM tab. Modules include the possibility of masking using remote sensing data, shapefiles or expert opinions and time matching between observations and remote sensing data.
  + ##### [Mask component testing instructions](mrw.md)
  + ##### Resources
    + [**maskRangeR R package vignette**](https://cmerow.github.io/maskRangeR/maskRangeR_Tutorial.html)


* #### **"Change RR" component (new)**
  + ##### **About:**
  + The Change RR component calculates several indicators relevant for conservation assessments. One indicator is an estimate of range size, AOO, and EOO based on occurrence localities and/or SDMs. Additionally, the percentage of overlap between species distributions with different spatial categories (e.g, protected areas, mining) and estimates of how range size may change over time given various spatial categories (e.g. deforestation, ecological footprint).
  + ##### [Change RR testing instructions](crt.md)
  + ##### Resources
    + [**changeRangeR**](pdf/singleSpeciesMetrics.pdf)


* #### **"Alpha Div" component (new)**
  + ##### **About:**
  + The Alpha Div component allows users to calculate diversity indices based on multiple species SDMs (either created in Wallace or user-uploaded). In this version, those indices are species richness and species endemism. This module will be expanded to include other dimensions of diversity; in particular phylogenetic diversity and phylogenetic endemism calculations.
  + ##### [Alpha diversity testing instructions](crr.md)
  + ##### Resources
    + [**changeRangeR multiple species tutorial**](pdf/BiodivMetrics.pdf)
    + [**changeRangeR diversity metrics using sparse matrices tutorial**](pdf/Diversity_Metrics_Using_Sparse_Matrices.pdf)
    

* ### **Report bugs**
  + **Bug reporting**<br>
If you find a bug, let us know!
If you have a Github account, you can report issues [here](https://github.com/wallaceEcoMod/wallace/issues) <br>
You can email the [Wallace Google Group](https://groups.google.com/g/wallaceEcoMod) using the subject [installation]. <br>
If you have another suggestion, please write to the Wallace email (wallaceEcoMod@gmail.com), specifying that you have been testing the development version.

* ### Do you want to know more about Wallace?
  + Please visit our [website](https://wallaceecomod.github.io/).


