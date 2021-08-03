## changeRangeR Multispecies Functions Testing Instructions

**Instructions**
1. In RStudio, run these lines of code:
```{r}
library(wallace)
run_wallace()
```

2. Wallace will open in your browser. Go to the component "Occ Data" - and choose module "Query GBIF". Enter a Genus and species for an animal name of your choice.

3. The species' occurrences should appear on the map. Click on "Table" to view detailed information on each point, and remove erroneous points from the set. We suggest *Alouatta palliata* - which has at least one erroneous point in Argentina.

4. Search for two or more additional species that live in the same area/region as the first species. We suggest as two other species: *Alouatta seniculus*, *Ateles belzebuth*.

5. Continue through the rest of the modules to build a species distribution model for the species - remember to check the box "batch" when you see it to run each step for all of your species.  Choose the species' name from the dropdown menu to view the loaded occurrences in the table and again remove any erroneous points (for example, like the one in North America for *Ateles belzebuth* and the one in Africa for *Alouatta seniculus*). 
Follow the Component and Module Guidance in each section for more information - but please skip the "Env Space"", "User SDM", "Mask", and "ChangeRR" Components.
To save time, we suggest the following choices in each component:

- under "Env Data", you can upload user-specified 10 arc-minute data downloaded from the link on the workshop website. You don't have to select all 19 variables, you can select 1-10 or as many as you wish.
- under "Proc Occs", use spatial thinning by 10km or skip this step.
- under "Proc Env", use a bounding box with a 1 degree buffer and sample between 1000-10,000 background points (highest available for your area)
- skip "Env Space"
- under "Part Occs", use a non-spatial partition of random k-folds (2 folds)
- under "Model", select MaxEnt, and then maxnet, L and LQH, and a regularization of range 1-2, and clamping can be either true or false.
- under "Visualize", choose each species and then plot cloglog without a threshold. 

6. When you get to the component "Project", it is important that you project all three models to the exact same projection extent and to thresholded binary projections. <br>
For the extent, we suggest that you project to the extent of Colombia (this is the file "Col_adm0.shp" in the [website data downloads](Data.md), with a 1 degree buffer around the shapefile, and choose a minimum training presence threshold projection. This step cannot be done in batch, you will have to choose each species from the dropdown menu and then select the projection extent (Colombia shape file with a 1 degree buffer), and then project using the MTP threshold.
- Adding a 1 degree buffer is important to add to help simplify the polygon (because the Colombia shapefile includes a very detailed coastline). You can instead upload a simpler polygon (such as a square or rectangle shape) and project without adding a buffer.

7. Skip to the "Alpha Div" Component. Select the "Richness" module and review the component and module guidance tabs. Select all three species that you modeled and projected, and hit Run to view species richness. If you get an error message here about projecting to the same extent, try going back to the "Project" component and add a 1 degree buffer around your polygon and reproject each species' module.

8. Select the "Endemism" module. Review the module guidance tab. Select all three species you modeled and projected, and hit Run to view species endemism.


**changeRangeR vignettes**:

[Single species](https://drive.google.com/file/d/1-NbDIjI8b7sCjAvUcOTNBy4xijJi7BsC/view?usp=sharing)

[Multiple species](https://drive.google.com/file/d/1pK6huSbfjsITKDam0nFpzShhP4d7FXLX/view?usp=sharing)

[Diversity metrics using sparse matrices](pdf/Diversity_Metrics_Using_Sparse_Matrices.pdf)

**changeRangeR demonstration videos:**

[Large scale biodiversity measures in changeRangeR](https://youtu.be/Hn5fm6XO7tg)

[phylogenetic diversity in changeRangeR](https://youtu.be/yJee8TVBGEs)
