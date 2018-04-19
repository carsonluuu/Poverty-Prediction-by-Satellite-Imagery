# Poverty Prediction by Combination of Satellite Imagery and Machine Learning
*Is it feasible for you to estimate the standard of living or energy consumption of a site based night-time satellite imagery?This means whether we can do the satellite imagery processing for socioeconomic analysis?*

*Let's find it out in this project.*

Key Steps
-------
1. Download satellite night lights images from NOAA
2. Download DHS data for Rwanda
3. Test whether night lights data can predict wealth, as observed in DHS
4. Download daytime satellite imagery from Google Maps
5. Test whether basic features of daytime imagery can predict wealth
6. Extract features from daytime imagery using deep learning libraries
7. Replicate final model and results of Jean et al (2016)
8. Construct maps showing the predicted distribution of wealth in Rwanda

A night time satellite imagery:
-----

![alt text][logo]

[logo]: https://eoimages.gsfc.nasa.gov/images/imagerecords/55000/55167/earth_lights_lrg.jpg "night time satellite imagery"


# Download nightlights images

- **RESULT**: 
 - `F182010.v4d_web.stable_lights.avg_vis.tif`: Single image file giving nightlights intensity around the world

Go to the [DMSP-OLS website](https://ngdc.noaa.gov/eog/dmsp/downloadV4composites.html) and download the satellite nighttime luminosity data (roughly 400MB). Here we are using the file F182010.v4d_web.stable_lights.avg_vis.tif.

# Download Rwandan DHS and construct cluster-level aggregates

- **FILE INPUT**: 
  - `rwanda_clusters_location.csv`: Coordinates of the centroid of each cluster
- **RESULT**: 
  - `rwanda_cluster_avg_asset_2010.csv`: Comma-delimited file indicated average wealth of each cluster 

[Demographic and Health Surveys (DHS)](http://dhsprogram.com/What-We-Do/Survey-Types/DHS.cfm) are nationally-representative household surveys that provide data for a wide range of monitoring and impact evaluation indicators in the areas of population, health, and nutrition. For this assignment, you will need to download the [2010 Rwandan DHS data](http://dhsprogram.com/what-we-do/survey/survey-display-364.cfm). **This requires registration** Do not forget to request for the GPS dataset. 

The immediate goal is to take the raw survey data, covering 12,540 households, and compute the average household wealth for each survey cluster (think of a cluster as a village). Refer to the file `Recode6_DHS_22March2013_DHSG4.pdf` for information on these data.

Saved output is `rwanda_cluster_avg_asset_2010.csv`.

NOTES:
- `Household Recode` contains all the attributes of each household. It provides datasets with different formats. We use `RWHR61FL.DAT` file in Flat ASCII data (.dat) format.
- `RWHR61FL.DCF` describes the attributes and the location of each attribute.
- Geographic Datasets: `rwge61fl.zip` contains the location of each cluster in Rwanda. It is in the format of shapefile, which needs QGIS or other GIS softwares to open. For those who are not familiar with GIS tools or who want a shortcut, you can also sue the file `rwanda_clusters_location.csv` provided.

the cluster locations, overlaid on the nightlights data, are shown in the figure below.
<img src="figure/map1.png" alt="Map" style="width: 400px;"/>
