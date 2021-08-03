### changeRangeR in Wallace Testing instructions.
Please also check out the [demonstration video for single species analyses](https://youtu.be/mfBwqnate88)<br>
and the [demonstration video for multiple species analyses](https://youtu.be/eXqyctCFJ0U)


## Single species testing
[Video](https://youtu.be/mfBwqnate88)

Instructions:<br>
1. In RStudio, run these lines of code:
```{r}
library(wallace)
run_wallace()
```
2. Wallace will open in your browser. Go to the component "Occ Data" - and choose module 
user-specified. Upload the occurrence data file *All_new_records_by_year.csv* from the **olinguito.zip** data download on the workshop website.

3. Skip to "User SDM"" component. <br>
(for ChangeRR modules, you can either upload an SDM or if you want to you can go through and make your own model in Wallace and even mask it in the Mask component and then continue to ChangeRR)

4. Go to your data downloads and rename the file *Bassaricyon_neblina_binary.tif* to be *Bassaricyon_neblina.tif* - make sure its exactly the same as the scientific name in the csv table for the species. This is required for any calculation in "Mask" or ChangeRangeR that also uses occurrence data (here, the occurrence-based area calculations for EOO and AOO - if you don't plan to use these functions, then you don't have to change the name).

Upload this file in User SDM.<br>
Note: This is a binary - thresholded model. We need a thresholded model for the Areas calculations, but we can use a continuous model for the overlap and time modules.

5. Go to the "Change RR" component and choose the "Areas" Module.  Calculate "range size" and for the source choose "User SDM". In this module you can also calculate areas from a Wallace model, a Wallace projected model, or a masked model (made in the "Mask" component). <br>
View the results tab for the calculation of area.

6. now choose "EOO" and choose "User SDM" - View the results tab for the calculation of EOO area

7. now choose "AOO" and choose "User SDM" - View the results tab for the calculation of AOO area.

8. you can also calculate these via standard IUCN methods: Go to "EOO" and choose occurrences - and you will see a map plot and in the Results tab with the area calculation for EOO based on a minimum convex polygon around the occurrences (the standard IUCN method). <br> 
Lets move on to the Overlap module

9. In "Overlap", choose input raster - choose user SDM and for choose input polygon - choose the *SA_Ecoregions_WWF* shapefile you downloaded - remember to select all three files (.shp, shx, .dbf) - and for fields of interest, choose ECO_NAME and check all the montane forests.

10. click the "Results" tab to view the percentage of range within montane forests. <br>
**tip**: Try it again for protected areas! This is the shapefile "WDPA_COL_olinguito.shp" that you downloaded in the "parks.zip" file from the workshop website. <br>
Now let's try calculating change through time.

11. In "Time", choose input raster - choose user SDM

12. choose environmental variables - upload the 5 MODIS rasters that are in the *olinguito.zip* zipfile from workshop website data downloads. Set the threshold value for the species - in this case, we'll try a threshold forest cover for the olinguito of 0.25

13. choose "years" - enter all the years you want to view in the plot - in this case we only have available 5 years from the MODIS rasters: 2005,2006,2008,2009,2010

14. then "calculate". You can see in the "Results" tab a plot of how the range of the species has changed through time for the environmental layers you have available - in this case, forest cover.

15. Remember to close your browser window and click the red stop sign in RStudio to close out Wallace before restarting your session for the changeRangeR multispecies functions below!


## Multiple species testing
[Video](https://youtu.be/eXqyctCFJ0U)
Instructions:<br>
1. In R studio, run these lines of code:
```{r}
library(wallace)
run_wallace(biomodelos=TRUE)
```
2. Wallace will open in your browser. Go to the component "Occ Data" - and choose module "Query BioModelos". 
  - Enter a Genus and species for a Colombian animal name of your choice - but note it must already be in the BioModelos database (you can search the BioModelos website: http://biomodelos.humboldt.org.co/). We suggest *Alouatta palliata*.

3. For "enter API key", paste the following key: **5NbMdjylEPEN1cBCIsX9dl:3vbVvDAXQdjf40NeYHfN1g**<br> DO NOT SHARE THIS KEY WITH ANYONE OUTSIDE THE WORKSHOP.

4. The species' occurrences should appear on the map. Click on "Table" to view detailed information on each point.

5. Search for two or more additional species and choose the species name from the dropdown menu to view the loaded occurrences. We suggest as two other species: *Alouatta seniculus*, *Ateles belzebuth*

6. Continue through the rest of the modules to build a species distribution model for the species - remember to check the box "batch" when you see it to run each step for all of your species.<br>
Follow the Component and Module Guidance in each section for more information - but please skip the "Env Space"", "User SDM", "Mask", and "ChangeRR" Components.
To save time, we suggest the following choices in each component:

  - under "Env Data", you can upload user-specified 10 arc-minute data downloaded from the link on the workshop website. You don't have to select all 19 variables, you can select 1-10 or as many as you wish.
  - under "Proc Occs", use spatial thinning by 10km or skip this step.
  - under "Proc Env", use a bounding box with a 1 degree buffer and sample between 1000-10,000 background points (highest available for your area)
  - skip "Env Space"
  - under "Part Occs", use a non-spatial partition of random k-folds (2 folds)
  - under "Model", select MaxEnt, and then maxnet, L and LQH, and a regularization of range 1-2, and clamping can be either true or false.
  - under "Visualize", choose each species and then plot cloglog without a threshold. 

7. When you get to the component "Project", it is important that you project all three models to the exact same projection extent and to thresholded binary projections. For the extent, we suggest that you project to the extent of Colombia (this is the file "Col_adm0.shp" in the workshop website data downloads), with a 1 degree buffer around the shapefile, and choose a minimum training presence threshold projection. This step cannot be done in batch, you will have to choose each species from the dropdown menu and then select the projection extent (Colombia shape file with a 1 degree buffer), and then project using the MTP threshold. As you can see from the demo video, the 1 degree buffer is important to add to help simplify the polygon (because the Colombia shapefile includes a very detailed coastline).

8. Skip to the "Alpha Div" Component. Select the "Richness" module and review the component and module guidance tabs. Select all three species that you modeled and projected, and click *Run* to view species richness for Colombia! If you get an error message here about projecting to the same extent, try going back to the "Project" component and add a 1 degree buffer around your polygon and reproject each species' module (like we had to do in the demo video).

9. Select the "Endemism" module. Review the module guidance tab. Select all three species you modeled and projected, and hit Run to view species endemism for Colombia!

10. If you wish, you can send your completed models to BioModelos. go to the "Reproduce" component, "BioModelos payload" module, and follow the module guidance text - you should select each species one by one to send to BioModelos.