## BioModelos API Subgroup Instructions

Please also check out the demo videos for [Getting data (en Espanol)](https://www.youtube.com/watch?v=7-erSCspct8&feature=youtu.be) and [Getting and posting data (in English)](https://youtu.be/E-2fgqa-Epk)<br>

**Instructions**<br>
1. In RStudio, run this line of code to load wallace:<br>
```{r}
library(wallace)
```
2. Then use this line to run the version of wallace with the special BioModelos modules:
```{r}
run_wallace(biomodelos=TRUE)
```
3.  Wallace should open in your web browser. Go to the Component "Occ Data" - and choose module "Query BioModelos".  Enter a  Genus and species for a Colombian animal name of your choice - but note it must already be in the biomodelos database (you can search [BioModelos](http://biomodelos.humboldt.org.co/).  We suggest *Alouatta palliata*.<br>
4. For "enter API key", paste the following key:<br><br>
**5NbMdjylEPEN1cBCIsX9dl:3vbVvDAXQdjf40NeYHfN1g**<br><br>
DO NOT SHARE THIS KEY WITH ANYONE OUTSIDE THE WORKSHOP<br>
5. The species' occurrences should appear on the map. Click on "Table" to view detailed information on each point.<br>
6. Continue through the rest of the modules to build a species distribution model for the species. <br>
Follow the Component and Module Guidance in each section for more information - but please skip the "Env Space"", "User SDM", "Mask", "ChangeRR", and "Alpha Div" Components.<br>
To save time, we suggest the following choices:

    - under "Env Data", choose worldclim 10 arc-minute data (if this step is not working then use the [worldclim download](Data.md) link on the workshop website and upload these layers under "User-specified"  
    - under "Proc Occs", use spatial thinning by 10km.
    - under "Proc Env", use a bounding box with a 0.5 degree buffer and sample between 1000-10,000 background points (highest available for your area)
    - skip "Env Space"
    - under "Part Occs", use a non-spatial partition of random k-folds (2 folds)
    - under "Model", select MaxEnt, and then *maxnet*, L and LQH, and a regularization of 1 value only (your choice), and clamping can be either true or false. 
    - under "Visualize", plot cloglog without a threshold. Then plot a threshold of your choice. 
    - you can skip "Project".

7. Now you're ready to send the model to BioModelos! <br> 
Skip ahead to the "Reproduce" Component, "Biomodelos payload" module.<br>
Choose your species and re-enter the API key from Step 4. Enter your email  (if you are not yet registered as a BioModelos user, you can register on their website! http://biomodelos.humboldt.org.co/; And under CC license, choose the copyright license under which you agree to share your model with BioModelos users. You can read more about different licenses here: https://creativecommons.org/licenses/ <br>
Finally, check the box beside "Atlas agreement" if you agree that BioModelos can publish your model as a part of the next Atlas of Biodiversity of Colombia. Today, our models are just tests - so don't worry, they won't be publishing the models we run today. <br>
Then, select "Push Payload"!  This will send your occurrence data, model rasters, model metadata, and .RmD file to BioModelos.<br>
8. Once you have tried it with one species, close your browser and hit the "stop sign" in R studio. You can try again by going back to step 3 in these instructions. Try running 2+ species at the same time in batch! (check the "Batch" box in each Component)! You will able able to send each species' model (one at a time) to BioModelos in the Reproduce component.
