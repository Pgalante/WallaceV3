## Wallace Version 3 beta-testing instructions

If you are a twitter user, **please use our hashtag #WallaceEcoMod** to tweet about your work.


* ### **Wallace v3**
  + ##### [Wallace installation instructions](installation_instructions.md)
  + ##### Resources
    + [**Wallace Version 1 Tutorial**](https://wallaceecomod.github.io/vignettes/wallace_vignette.html)


* ### Data
  + [**Download prepared Datasets**](Data.md)<br><br>


* #### **"Mask" component (new)**
  *Mask* allows users to post-process the SDM you made in *Wallace* or imported with *UserSDM*.  Users are given the option to mask SDMs using remotely sensed data, user-specified shapefiles, or expert opinions. Additionally, *Mask* allows users to temporally match species occurrence records with remote sensing data (e.g., forest cover).
  
  + #### Testing Instructions
    ##### [Mask component testing instructions](mrw.md)
  + ##### Resources
    [**maskRangeR R package vignette**](https://cmerow.github.io/maskRangeR/maskRangeR_Tutorial.html)


* #### **"Change RR" component (new)**
  *Change RR* allows users to calculate several indicators relevant for conservation assessments based on occurrence localities and/or SDMs. Such indicators include range size estimates and IUCN Area of Occupancy (AOO) and Extent of Occurrence (EOO). Additionally, *Change RR* allows users to calculate the percentage of overlap between species' distributions and different spatial features (e.g, protected areas, mining) and estimate how range size may change over time given various spatial processes (e.g. deforestation, ecological footprint).
  
  + ##### Testing Instructions
    ##### [Change RR testing instructions](crt.md)
  + ##### Resources
    [**changeRangeR**](pdf/singleSpeciesMetrics.pdf)


* #### **"Alpha Div" component (new)**
  *Alpha Div* allows users to calculate diversity indices based on multiple species' SDMs (either created in *Wallace* or user-uploaded via *UserSDM*). Currently, users can calculate species richness and species endemism. However, we plan to include tools to calculate metrics reflecting other dimensions of diversity; in particular phylogenetic diversity and phylogenetic endemism calculations.
  
  + ##### Testing Instructions
    ##### [Alpha diversity testing instructions](crr.md)
  + ##### Resources
    [**changeRangeR multiple species tutorial**](pdf/BiodivMetrics.pdf)<br>
    [**changeRangeR diversity metrics using sparse matrices tutorial**](pdf/Diversity_Metrics_Using_Sparse_Matrices.pdf)
    


* ### **Help *Wallace* improve**
  + **Bug reporting**<br>
  **Github:** If you find a bug, let us know! If you have a Github account, you can report issues [here](https://github.com/wallaceEcoMod/wallace/issues) <br>
  **Google group:** You can email the [Wallace Google Group](https://groups.google.com/g/wallaceEcoMod) using the subject [installation]. <br>
  
* ### **Suggestions**
If you have another suggestion, please write to the Wallace email (wallaceEcoMod@gmail.com), specifying that you have been testing the development version.<br>

* ### Do you want to know more about Wallace?
  + Please visit our [website](https://wallaceecomod.github.io/).


