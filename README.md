# Bighorn Backcountry

according to lauras thesis - 83 functional sites for detecting wildlife from oct 2019 - sept 2020, but then a different array of 39 sites used to capture range of vehicle activity. These shouldn't be used for wildlife occurrence then??

# Richardson Wildfire Project
This repository contains data, R scripts and associated outputs, and other materials necessary for the Applied Conservation and Macro Ecology (ACME) laboratory's research program with the Richardson Wildfire Project. 
The Richardson Wildfire Project was undertaken by InnoTech Alberta beginning in late 2017 as part of their CAMERA project that uses coordinated distributed camera trap arrays to research the effects of continued landscape change and multiple management interventions on mammal biodiveristy in Alberta,  across a gradient of landscape change, from relatively low human footprint to high human footprint, as well as different degrees of active human use. The Richardson study region experiences low-intensity land use and is less accessible.The project objectives were to: develop inventory tool to estimate relative density of ungulate species using CT surveys in the boreal forest of north-eastern Alberta, and validate winter density and demographic estimates against concurrent provincial survey methods. Cameras were deployed in a two-factorial design: on and off seismic lines, in and out of wildfire burns, with the first phase of cameras deployed solely outside of burns. In November 2017, 30 cameras were deployed in the Richardson/Marguerite area (WMU 530), and an additional 28 cameras were deployed in November 2018. Data were retrieved from cameras in April 2019, November 2019, and November 2020.

Note that because this was a collaborative project, data and code has changed hands multiple times. The efforts below use data previously cleaned and processed by multiple individuals, and this is an attempt to house the "final" products of these efforts. 
<hr>

### GENERAL INFORMATION

**Project Information**   
Details for the Richardson Wildfire research program [here](http://www.acmelab.ca/richardson.html).
Further details for the Richardson WILDCAM progam page [here](https://wildcams.ca/projects/richardson-project/).

Also visit the [ACME website](http://www.acmelab.ca) more information about the ACME lab.

**Author Information (project management and data):**  
 Principal Investigator Contact Information  
 Name: Jason T. Fisher, PhD   
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [fisherj@uvic.ca](mailto:fisherj@uvic.ca) 

 **Author Information (project management and data):**  
 Principal Investigator Contact Information  
 Name: Cole A. Burton, PhD   
 Institution: University of British Columbia 
 Address: Forest Sciences Centre 2038, 2424 Main Mall, Vancouver, BC V6T 1Z4
 Email: [cole.burton@ubc.ca](cole.burton@ubc.ca ) 

**Author Information (code):**  
 Data Analysis Contact Information  
 Name: Aidan Brushett  
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [aidanbrushett@uvic.ca](mailto:aidanbrushett@uvic.ca) 

 **Author Information (code):**  
 Data Analysis Contact Information  
 Name: Andrew Barnas, PhD   
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [andrew.f.barnas@gmail.com](mailto:andrew.f.barnas@gmail.com) 

 ### DATA & FILE OVERVIEW
The following steps combine efforts by Dr. Gonçalo Curveira-Santos who assembled the raw data from the Richardson array (richardson_raw_data) and additional processing steps from Aidan Brushett (cleaned_richardson_data). Some of the files in these are redundant or not needed, or need further processing to create the standard outputs for the ACME github which are detailed in 1. Data Prep.RMD

*Richardson.Rproj*: The R project which houses all this data and analysis

*1. Data Prep.Rmd*: The R markdown file that does all the work of producing outputs

**inputs**

This folder contains both summarized and raw(ish) data products (e.g. previously processed data) used to produce key products in the outputs folder. I am providing the whole folder for transparency, even though some redundant products (Wildtrax) appear in here. 
These files are partially processed data provided by Dr. Cole Burton on behalf of Dr. Gonçalo Curveira-Santos, and some made by Aidan Brushett 

*Files*
1) Richardson_daily_effort_lookup.csv: A file of daily camera operability for each camera for each year. Note I provide a slightly different format in the outputs folder. 
2) Richardson_Deployment_Data_2018_2019_2020.csv: a file of deployment data featuring start and stop dates based on camera operability or visibility for each camera in the Richardson array
3) Richardson_Deployment_Site_data.csv: A file of deployment timing and location information 
4) Richardson_Detection_Data_2018_2019_2020.csv: a large file that appears to be the amalgamated timelapse files for all cameras in the Richardson array
5) Richardson_Wildtrax_Detection_Data_2019_2020.csv: a file of detection data from the additional Richardson Wildtrax project. 
6) Richardson_Wildtrax_Detection_Data_2020_2021.csv: a file of detection data from the additional Richardson Wildtrax project.
   

**outputs**
This folder contains three key data products needed to move forward with additional analyses; 1) a summary of independent detections of wildlife species at each camera site to the standard 30 minute threshold, 2) the GPS locations of individual camera sites, 3) covariates associated with each camera site extracted across multiple radius buffers (details below), 4) the raw detection file containing all the image information, should anyone want to calculate their own threshold or produce a different type of response variable.
*See details on files below*

**relevant literature**  
This folder provides pdf copies of previously published papers using the Willmore Wilderness remote camera dataset. The purpose of this folder is to provide background/information on previously published work using this dataset. Note that sample numbers may vary between individual manuscripts due to specifics of individual projects, as well as the multiple deployment designs within the Willmore dataset.
 * Barnas et al. 2024 How landscape traits affect boreal mammal responses to anthropogenic disturbance.
 * Burton et al. 2022 Behavioural bycatch from camera trap surveys yields insights on prey responses to human-mediated predation risk
 * Curveria-Santos 2024. Disturbance-mediated changes to boreal mammal spatial networks in industrializing landscapes
 * Sun et al. 2022 A cautionary tal comparing spatial count and partial identity models for estimating densities of threatened and unmarked populations
<hr>

### **DETAILS ON OUTPUTS** 
### Data specific information for : [outputs/richardson_camop.csv]  
One thing to note for the camera operability file, whoever made this and was quite diligent with removing periods of obscurity (e.g. snow cover). I have removed the comments column from this because its large and unweildly, but should someone want to go in and see the specific reason for gaps in camera operation, see the original file Richardson_Deployment_Data_2018_2019_2020.csv
* **Number of variables/columns:** 7
* **Number of observations/rows:** 273 (multiple rows per camera sites due to multiple checks and periods of camera obscurity) 

**Variable List:**
* **site** : camera site ID
* **lat** : camera site latitidue 
* **long** : camera site longitutde
* **easting_12n** : camera site Easting location
* **northing_12n** : camera site Northing location
* **start_date** : first day of camera operation as recorded by notes on camera start dates for that check
* **end_date** : last day of camera operation as recorded by camera visability and camera checks

### Data specific information for : [outputs/richardson_detections_raw.csv]  

* **Number of variables/columns:** 11
* **Number of observations/rows:** 634778 (one row for each image at each site) 

**Variable List:**
* **array**: the array this took place in (obviously richardson)
* **camera**: I don't know maybe a camera unit number? We have a seperate column for site ID
* **site** : camera site ID
* **species** : the species in the independent detection. Note this still contains "Unknowns" and will need to be filtered/cleaned before any analysis.
* **datetime** : the datetime (year-month-day hour:minute:second) of the image 
* **image_total** : Looks to be a total of how many "things" (wildlife)? Were in the image, E.g. 2 for two bears in the same image, 0 for an empty image
* **group_total** : Guessing this is a summary of how many individuals were in the same sequence of images. E.g. one bear passess by but then another bear walks by, but clearly a different bear. This is a group of 2?
* **age_class** : looks like a categorization for adult, young of the year, juvenile etc. Not sure how accurate, recommend tracking down project leads for how this was done and which species it would be good for
* **sex** : male or female, also not sure how reliable and for which species. Contact PIs
* **image_comments**: Any comments from the taggers on the image itself
* **tag_comments**: Any comments from the taggers on the tag? Not sure how this differs from above. 


### Data specific information for : [outputs/richardson_30min_independent_detections.csv]  

* **Number of variables/columns:** 8
* **Number of observations/rows:** 5940 (one row for each independent detection of a species at each site) 

**Variable List:**
* **array**: the array this took place in (obviously richardson)
* **camera**: I don't know maybe a camera unit number? We have a seperate column for site ID
* **Site** : camera site ID
* **species** : the species in the independent detection. Note this still contains "Unknowns" and will need to be filtered/cleaned before any analysis.
* **event_start** : the datetime (year-month-day hour:minute:second) of the first camera image of each independent detection. 
* **event_end** : the datetime (year-month-day hour:minute:second) of the last camera image of each independent detection. 
* **year** : the year the independent detection took place
* **month** : the month the independent detection took place. 

### Data specific information for: [outputs/richardson_covariates_formatted_grouped.csv]

-   **Number of variables:** 42
-   **Number of cases/rows:** 1276

**Variable List:**

-   **array;** a factor with 10 levels describing the landscape unit (eg., LU01)
-   **site;** a factor with 430 levels where the first element abbreviation describes the landscape unit and the second element describes the camera site.
-   **array_year;** a factor with 3 levels that describes the year the camera was deployed
-   **lat;** latitude of the camera location in decimal degrees (WGS84)
-   **long;** longitude of the camera location in decimal degrees (WGS84)
-   **easting_12N;** easting coordinate of the camera site(NAD 83 UTM Zone 12N)
-   **northing_12N;** northing coordinate of the camera site(NAD 83 UTM Zone 12N)
-   **buffer_dist;** a numeric measurement in meters ranging from 50 - 5000, of the buffer radius around the camera for which the proportion of all variables were calculated.
-   **harvest_0\_15;** a numeric variable indicating the proportion of the buffer area comprised of
-   of harvest areas harvested within the past 15 years.
-   **harvest_gt_15;** a numeric variable indicating the proportion of the buffer area comprised of of harvest areas harvested over 15 years ago.
-   **harvest_total;** a numeric variable indicating the proportion of all harvest areas within the buffer area.
-   **osm_industrial;** a numeric measurement representing the proportion of various industrial features and clearings within the buffer. This includes, borrowpits (i.e., Borrowpit-dry, Borrowpit-wet, Borrowpits, Ris-borrowpits, Dugout, Lagoon, and Sump), clearings (i.e., Clearing-unknown, Clearing-wellpad-unconfirmed, Ris-clearing, Ris-clearing-unknown, and Runway), facilities (i.e., Camp-industrial, Facility-other, Facility-unknown, Mill, Misc-oil-gas-facility, Oil-gas-plant, Ris-camp-industrial, Ris-facility-operations, Ris-facility-unknown, Ris-plant, Ris-tank-farm, Ris-utilities, and Urban-industrial), and mines (i.e., Grvl-sand-pit, Mines-oilsands, Mines-pitlake, Open-pit-mine, Peat, Ris-drainage, Ris-mines-oilsands, Ris-oilsands-rms, Ris-overburden-dump, Ris-reclaim-ready, Ris-soil-salvaged, Ris-tailing-pond, Ris-waste, and Tailing-pond).
-   **pipe_trans;** a numeric measurement representing the proportion of pipelines and transmission lines within the buffer.
-   **railways;** a numeric variable indicating the proportion of single track railways within the buffer area. Single track railways are defined as, hard, steel rail lines designed for train use. Specifically, a road or track for trains, consisting of parallel steel rails, supported on wooden crossbeams. The single track consists of one parallel sets of tracks.
-   **roads**; a numeric measurement representing the proportion of roads within the buffer. Roads are defined as, non-vegetated, impermeable surfaces used for motorized vehicle or aircraft transportation or access and includes, Airp-runway, Interchange-ramp, Ris-airp-runway, Ris-road, Road-gravel-1L, Road-gravel-2L, Road-paved-1L, Road-paved-2L, Road-paved-3L, Road-paved-4L, Road-paved-5L, Road-paved-6L, Road-paved-7L, Road-paved-div, Road-paved-undiv-1L, Road-paved-undiv-2L, Road-unclassified, Road-unimproved, Road-unpaved-1L, Road-unpaved-2L, Road-winter, and Transfer station.
-   **seismic;** a numeric measurement representing the proportion of seismic lines and 3D seismic lines within the buffer.
-   **seismic_lines;** a numeric measurement representing the proportion of seismic lines within the buffer. Seismic lines are defined as, cleared corridors created during hydrocarbon exploration with a 3-meter buffer (6-meter total width), and were not grouped with any other variables.
-   **seismic_lines_3D;** a numeric measurement representing the proportion of 3D seismic lines (also called low-impact seismic lines) within the buffer. 3D seismic lines are defined as, cleared corridors created during hydrocarbon exploration with a 1.5-meter buffer (3-meter total width), and were not grouped with any other variables.
-   **trails;** a numeric measurement representing the proportion of trails within the buffer. Trails are defined as, cleared corridors surfaced with dirt or low vegetation for human/vehicle access, and include Trail, and Truck-trail.
-   **veg_edges;** a numeric measurement representing the proportion of vegetated edges within the buffer. Vegetated edges are defined as, disturbed vegetation alongside road edges, railway edges including ditches, and other industrial features, and include Vegetated-edge-railways, Vegetated-edge-roads, and Surrounding-veg.
-   **wells_active;** a numeric measurement representing the proportion of active wells within the buffer. Active wells are defined as, ground cleared for an oil/gas well pad where at least one well is currently active include, Well-bitumen, Well-cased, Well-cleared-not-confirmed, Well-cleared-not-drilled, Well-gas, Well-oil, Well-other, and Well-unknown.
-   **well_inactive;** a numeric measurement representing the proportion of inactive wells within the buffer. Inactive ells are defined as, ground cleared for an oil/gas well pad, where the well is currently abandoned.
-   **wells_total;** a numeric measurement representing the proportion of wells within the buffer. Wells are defined as, ground cleared for an oil/gas well pad, and include Well-abandoned, Well-bitumen, Well-cased, Well-cleared-not-confirmed, Well-cleared-not-drilled, Well-gas, Well-oil, Well-other, and Well-unknown.
-   **pct_betu_pap;** a numeric variable indicating the proportion of Betula papyrifera (White birch) within the buffer area.
-   **fire_0\_15;** a numeric variable indicating the proportion of burned area up to 15 years old within the buffer area.
-   **fire_gt_15;** a numeric variable indicating the proportion of burned area over 15 years ago within the buffer area.
-   **pct_lari_lar;** a numeric variable indicating the proportion of Larix laricina (Tamarack) within the buffer area.
-   **lc_broadleaf;** a numeric variable indicating the proportion of broadleaf forest within the buffer area.
-   **lc_conifer;** a numeric variable indicating the proportion of conifer forest within the buffer area.
-   l**c_herbs;** a numeric variable indicating the proportion of herb within the buffer area.
-   **lc_mixedwood;** a numeric variable indicating the proportion of mixedwood forest within the buffer area.
-   **lc_shrubs;** a numeric variable indicating the proportion of shrubs within the buffer area.
-   **lc_water;** a numeric variable indicating the proportion of water within the buffer area.
-   **lc_wetland;** a numeric variable indicating the proportion of wetland within the buffer area.
-   **lc_wetland_treed;** a numeric variable indicating the proportion of treed wetland within the buffer area.
-   **pct_pice_gla;** a numeric variable indicating the proportion of Larix laricina (White spruce) within the buffer area.
-   **pct_pice_mar;** a numeric variable indicating the proportion of Picea mariana (Black spruce) within the buffer area.
-   **pct_pinu_ban;** a numeric variable indicating the proportion of Pinus banksaina (Jack pine) within the buffer area.
-   **pct_popu_tre;** a numeric variable indicating the proportion of Populus tremuloides (Trembling aspen) within the buffer area.

***


Fin. 


