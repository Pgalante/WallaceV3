## Mask in Wallace  

#### Overview
The *Mask* tab allows users to post-process the SDM you made in Wallace, or imported in the UserSDM tab. Modules include the possibility of masking using remote sensing data, shapefiles or expert opinions and time matching between observations and remote sensing data.


Before you begin, please follow the [Wallace v3 installastion instructions](installation_instructions.md) and [Download the prepared datasets](Data.md)

For more information about this component, please see our [video: maskRangeR demonstration in Wallace](https://youtu.be/uBbYqQLRirU)

**Instructions**<br>

1. In R studio, run these lines of code: 
```{r}
library(wallace) 
run_wallace(biomodelos=TRUE) 
```
2. Wallace will open in your browser. Upload occurrence data in **Occ Data** tab. 

* Select the "**User-specified**" module, and upload Occurrence CSV: *All_new_records_by_year.csv* 

**Note**: if you want to use the maskRangeR temporal extract module, this .csv file must include a column "year" with the years for occurrence data. Years should match MODIS data that you will upload in that module.  

3. Upload an SDM. 

* You can either work through *Wallace* to build a model, or choose the **User SDM** tab. 

Find the *Bassaricyon_neblina.tif* file that you downloaded - it is inside the olinguito.zip zipfile.  

Upload distribution map (**): "Bassaricyon_neblina.tif" 

**Note**: This is a continuous model prediction for the olinguito. All of the *Mask* modules can be done with a continuous model prediction, but note that some changeranger functions (area calculations) will require a thresholded model, so you may want to mask a thresholded  model here instead, to use later with changeranger. Make sure any model you upload in User SDM is projected and has the same name as the scientific name of your species occurrence csv file . 

4. In **Mask** component, select "Mask by Shapefile".  

Upload polygon in shapefile (.shp, .shx, .dbf): Load the "SA_Ecoregions_WWF" shapefile. 

This is WWF's Terrestrial Ecoregions of the World 

**NOTE**: You must upload *all three* files (.shp, .shx, .dbf) 

Click "Load".  

You may see an error message- don't worry. Wallace is giving you a warning: 

```{r}
! WARNING:Bassaricyon neblina cloglog | Projection not found for shapefile. It is assume that shapefile datum is WGS84 (**) 
```

Select Field: "ECO_NAME" 

First, deselect all. We will select the 5 options for "montane forest". 

**NOTE**: Blue sections will be removed, yellow will be kept. 

Select Attribute:

  - Cauca Valley montane forest 
  - Magdalena Valley montane forest
  - Eastern Cordilla real montane forests
  - Cordilla Oriental montane forest
  - Northwestern Andean montane forests 

Click "Mask". It may take a few minutes. 

You can then download your masked projection, continue masking, or move on to changeRangeR. 

Lets try another *Mask* module 

5. In the *Mask* tab, select "Expert Polygon".  

Draw polygon using the polygon drawing tool. 

Click "Create". 

Select "remove polygon" and then "Mask". 

Note: You can only remove a polygon from a continuous model prediction. You can add or remove a polygon to a thresholded model prediction.  

Lets try the last Mask module 

6. In the *Mask* tab, select "Temporal Extract".  

Upload environmental rasters for masking distribution: Select the 5 MODIS files: 

   - 2005_olinguito_Modis.tif
   - 2006_olinguito_Modis.tif
   - 2008_olinguito_Modis.tif
   - 2009_olinguito_Modis.tif
   - 2010_olinguito_Modis.tif 

Click "load". 

Select bounds by choosing **2005, 2006, 2008, 2009, 2010**, and deselecting the rest of the  

years. Select only the years for which you have MODIS data and occurrence record data. 

Click "Get Bounds". 

Select raster for masking. 

Select upper and lower bounds. 

Click "mask". 

You can download the masked sdm or move on to changeRangeR. 