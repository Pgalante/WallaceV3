### Range Change Through Time Testing instructions.

#### OVerview 
The Change RR component will help the user to...



Before you begin, please follow the [Wallace v3 installastion instructions](installation_instructions.md) and [Download the prepared datasets](Data.md)

For more information about this component, please see our [demonstration video for single species analyses](https://youtu.be/mfBwqnate88)<br>


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

