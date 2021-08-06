### Range Change Through Time Testing instructions.

#### Overview 
The Change RR component calculates several indicators relevant for conservation assessments. One indicator is an estimate of range size, AOO, and EOO based on occurrence localities and/or SDMs. Additionally, the percentage of overlap between species distributions with different spatial categories (e.g, protected areas, mining) and estimates of how range size may change over time given various spatial categories (e.g. deforestation, ecological footprint).


Before you begin, please follow the [Wallace v3 installastion instructions](installation_instructions.md) and [Download the prepared datasets](Data.md)

For more information about this component, please see our [demonstration video for single species analyses](https://youtu.be/mfBwqnate88)<br>


## Single species testing

Instructions:<br>
1. In RStudio, run these lines of code:
```{r}
library(wallace)
run_wallace()
```
2. Wallace will open in your browser. Go to the component "*Occ Data*" - and choose **User-specified**. Upload the occurrence data file *All_new_records_by_year.csv* from the **olinguito.zip** found on the [data page](Data.md).

3. Go to the "*User SDM*" tab. <br>
(for **ChangeRR** modules, you can either upload an SDM or if you want to you can go through and make your own model in *Wallace* and even mask it in the **Mask** component and then continue to **ChangeRR**)

Upload the file *Bassaricyon_neblina.tif* in **Upload User SDM**.<br>
Note: This is a binary - thresholded model. We need a thresholded model for the Areas calculations, but we can use a continuous model for the overlap and time modules.

4. Go to the "*ChangeRR*" tab and choose the "**Areas**" Module. Set the options to "Range size" and for the source choose "User SDM". In this module you can also calculate areas from a *Wallace* model, a *Wallace* projected model, or a masked model (made in the "*Mask*" tab). <br>
View the results tab for the calculation of area.

5. Now choose "EOO" and choose "User SDM" - View the results tab for the calculation of EOO area

6. Now choose "AOO" and choose "User SDM" - View the results tab for the calculation of AOO area.

7. you can also calculate these via standard IUCN methods: Go to "EOO" and choose occurrences - and you will see a map plot and in the Results tab with the area calculation for EOO based on a minimum convex polygon around the occurrences (the standard IUCN method). <br> 
Lets move on to the Overlap module

8. Select the "Overlap" module. Under **Step 1**, choose user SDM and for **Step 2**, choose the *SA_Ecoregions_WWF* shapefile you downloaded - remember to select all three files (.shp, shx, .dbf) - and for fields of interest (**Step 3**), choose "ECO_NAME" as well as all of the "montane forests".

9. Click the "Results" tab to view the percentage of range within montane forests. <br>
**tip**: Try it again for protected areas. This is the shapefile "WDPA_COL_olinguito.shp" that you downloaded in the "parks.zip" file from the data page. <br>
Now let's try calculating change through time.

10. In the "Time" module, under **Step 1**, choose user SDM.

11. Choose environmental variables (**Step 2**), upload the 5 MODIS rasters that are in the *olinguito.zip* zipfile from the download page. Set the threshold value for the species - in this case, we'll try a threshold forest cover for the olinguito of 0.25

12. In **Step 3**, enter all the years you want to view in the plot - in this case we only have available 5 years from the MODIS rasters: 2005,2006,2008,2009,2010

13. Press "calculate". You can see in the "Results" tab a plot of how the range of the species has changed through time for the environmental layers you have available - in this case, forest cover.

