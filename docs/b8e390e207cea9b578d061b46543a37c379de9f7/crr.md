## Alpha diversity in Wallace Testing Instructions

#### Overview
The *Alpha Div* tab allows users to calculate diversity indices based on multiple species SDMs (either created in Wallace or user-uploaded). In this version, those indices are species richness and species endemism. This module will be expanded to include other dimensions of diversity; in particular phylogenetic diversity and phylogenetic endemism calculations. 


Before you begin, please follow the [Wallace v3 installastion instructions](installation_instructions.md) and [Download the prepared datasets](Data.md)

For more information about this component, please see our [demonstration video for multiple species analyses](https://youtu.be/eXqyctCFJ0U)


**Instructions**

1. In RStudio, run these lines of code:
```{r}
library(wallace)
run_wallace()
```

2. Wallace will open in your browser. Go to the tab "*Occ Data*" - and choose module "Query Database (Present)". Select the GBIF database, then enter a genus and species for an animal name of your choice - we suggest *Alouatta palliata*. Set the maximum number of occurrences to 100, and click "*Query Database*".

![](img/crrStep2.png)

3. The species' occurrences should appear on the map. Click on "Table" to view detailed information on each point, and remove erroneous points from the set. We suggest *Alouatta palliata* - which has at least one erroneous point in the ocean on the West coast of Costa Rica.

4. Search for two or more additional species that live in the same area/region as the first species. We suggest as two other species: *Alouatta seniculus*, *Ateles belzebuth*. You can view the other species by changing the drop-down menu at the top of the screen. Note that there may be unlikely occurrences for each of these species. Be sure to curate the dataset to remove unlikely records.

![](img/crrStep4.png)

5. Continue through the rest of the tabs to build a species distribution model (i.e., through *Visualize*) for each species - remember to check the box "batch" when you see it to run each step for all of your species.  Choose the species' name from the dropdown menu to view the loaded occurrences in the table and again remove any erroneous points (for example, like the one in North America for *Ateles belzebuth*. 
Follow the Component and Module Guidance (which are similar to help files) in each section for more information - but please skip the "*Env Space*", "*User SDM*", "*Mask*", and "*ChangeRR*" tabs.
To save time, we suggest the following choices in each tab:

- under the "*Env Data*" tab, you can upload user-specified environmental variables, or we suggest using *Wallace* to download the 10 arc-minute data from the *Worldclim Bioclims* Module. You don't have to select all 19 variables, you can select 1-10 or as many as you wish.
- under "*Proc Occs*", use spatial thinning by 10km or skip this step.
- under "*Proc Env*", use a bounding box with a 1 degree buffer and sample between 1000-10,000 background points (highest available for your area)
- skip "*Env Space*"
- under "*Part Occs*", use a non-spatial partition of random k-folds (2 folds)
- under "*Model*", select MaxEnt, and then maxnet, L and LQH, and a regularization of range 1-2, and clamping can be either true or false.
- under "*Visualize*", choose each species and then plot cloglog without a threshold. 

6. When you get to the "Project" tab, it is important that you project all three models to the exact same projection extent and to thresholded binary projections. <br>
* Select the *Project to NEw Extent* option
* Under *Select method*, choose "User-specified polygon" and upload the file "Col_adm0.shp" in the [website data downloads](Data.md)
* Add a *Study region buffer distance (degree)* of 1 degree around the shapefile.
* In **Step 2**, choose a minimum training presence (MTP) threshold projection. This step cannot be done in batch, you will have to choose each species from the dropdown menu and then select the projection extent (Colombia shape file with a 1 degree buffer), and then project using the MTP threshold.

- Adding a 1 degree buffer is important to add to help simplify the polygon (because the Colombia shapefile includes a very detailed coastline). You can instead upload a simpler polygon (such as a square or rectangle shape) and project without adding a buffer.

7. Go to the "Alpha Div" tab. Select the "Richness" module and review the component and module guidance tabs. Select all three species that you modeled and projected, and press **Run** to view species richness. If you get an error message here about projecting to the same extent, try going back to the "Project" tab and add a 1 degree buffer around your polygon and reproject each species' module.

8. Select the "Endemism" module. Review the module guidance tab. Select all three species you modeled and projected, and press **Run** to view species endemism.


**For more information on how the changeRangeR package works outside of Wallace**:

[Single species](pdf/singleSpeciesMetrics.pdf)

[Multiple species](pdf/BiodivMetrics.pdf)

[Diversity metrics using sparse matrices](pdf/Diversity_Metrics_Using_Sparse_Matrices.pdf)

**changeRangeR demonstration videos:**

[Large scale biodiversity measures in changeRangeR](https://youtu.be/Hn5fm6XO7tg)

[phylogenetic diversity in changeRangeR](https://youtu.be/yJee8TVBGEs)
