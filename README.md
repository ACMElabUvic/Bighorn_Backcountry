# Bighorn Backcountry
This repository contains data, R scripts and associated outputs, and other materials necessary for the Applied Conservation and Macro Ecology (ACME) laboratory's research program with the Bighorn Backcountry Project. 
The Bighorn Project seeks to understand how anthropogenic footprint and human activity affects mammal communities in this amazing wilderness in Alberta’s Rocky Mountains. This multi-use landscape houses a nearly intact large mammal community and is also home to important resource extraction and a key recreation area for areas of Edmonton and Calgary. Conserving its mammal biodiversity require informed management decisions. 

Of **key** importance here. The Bighorn project was comprised of two camera arrays. The first, was a deployment of 93 cameras designed to sample wildlife, which resulted in 83 cameras of useable data. The second array was designed explicitly for examining recreational vehicle use and was deployed under a different design. I (Barnas) have decided to only include the first array of data in this repository, as this more strongly aligns with our goals of sampling wildlife. The second array could be used for wildlife sampling but would require special considerations depending on the project. For further details and access to this data, contact myself or any other individuals listed here. The array here ran from October 2019 to September 2020.

The data provided here were previously cleaned and processed by Laura Eliuk. All the heavy lifting was done by her, my only role really was to format this for github.
<hr>

### GENERAL INFORMATION

**Project Information**   
Details for the Bighorn Backcountry research program [here](http://www.acmelab.ca/bighorn.html).
Further details for the Bighorn WILDCAM progam page [here](https://wildcams.ca/projects/bighorn-backcountry-project/).

Also visit the [ACME website](http://www.acmelab.ca) more information about the ACME lab.

**Author Information (project management and data):**  
 Principal Investigator Contact Information  
 Name: Jason T. Fisher, PhD   
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [fisherj@uvic.ca](mailto:fisherj@uvic.ca) 

 **Author Information (project and data management):**  
 Data Analysis Contact Information  
 Name: Laura Eliuk, MSc   
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [lauraeliuk@gmail.com](mailto:lauraeliuk@gmail.com) 

 **Author Information (code):**  
 Data Analysis Contact Information  
 Name: Andrew Barnas, PhD   
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [andrewbarnas@uvic.ca](mailto:andrewbarnas@uvic.ca) 

 ### DATA & FILE OVERVIEW
The following steps use previously cleaned data by Laura Eliuk that have been quality controlled and checked. These files were used to create the standardized outputs listed below. 

*Bighorn_Backcountry.Rproj*: The R project which houses all this data and analysis

*1. Data Prep.Rmd*: The R markdown file that does all the work of producing outputs

**inputs**

This folder contains cleaned and summarised data products by Laura Eliuk (seriously, she is a beacon of hope for how students should leave their project datafiles in order) containing the raw detection files, camera operability, and the camera deployment data. 

*Files*
1) BH.detections.raw.csv: a file of timelapse files featuring detection data from 83 cameras.
2) bh.landcover.all.csv: a file of landscape covariates for each camera site extracted at various buffer sizes for each site.
3) BH_deployment_clean.csv: a file of deployment data for each camera detailing when and where the camera was operating. 
   

**outputs**

This folder contains four key data products needed to move forward with additional analyses; 1) a summary of independent detections of wildlife species at each camera site to the standard 30 minute threshold, 2) the GPS locations of individual camera sites along wiht their own operability, 3) covariates associated with each camera site extracted across multiple radius buffers (details below), 4) the raw detection file containing all the image information, should anyone want to calculate their own threshold or produce a different type of response variable.
*See details on files below*

**relevant literature**  

This folder provides pdf copies of previously published papers using the Bighorn Backcountry remote camera dataset. The purpose of this folder is to provide background/information on previously published work using this dataset. Note that sample numbers may vary between individual manuscripts due to specifics of individual projects. E.g. the use of all cameras vs the subsetted 93/83 cameras
 * Barnas et al. 2024 How landscape traits affect boreal mammal responses to anthropogenic disturbance.
 * Laura Eliuk MSc Thesis 2023 - The relative impact of recreational activity and landscape protection on a Rocky Mountain Mammal community
 * Khan et al 2023 Shifts in diel activity of Rocky Mountain mammal communiities in response to anthropogenic disturbance and sympatric invasive white-tailed deer
<hr>

### **DETAILS ON OUTPUTS** 
### Data specific information for : [outputs/bighorn_camop.csv]  

* **Number of variables/columns:** 5
* **Number of observations/rows:** 83 (one per camera) 

**Variable List:**
* **site** : camera site ID
* **latitude** : camera site latitidue 
* **longitude** : camera site longitutde
* **start_date** : first day of camera operation as recorded by notes on camera start dates for that check
* **end_date** : last day of camera operation as recorded by camera visability and camera checks

### Data specific information for : [outputs/bighorn_detections_raw.csv]  
Note this is slimmed down, I have removed much of the default timelapse columns as they are generally not useful. If you want the extra details on group counts and whatnot, track them down from the inputs folder
* **Number of variables/columns:** 3
* **Number of observations/rows:** 634778 (one row for each image at each site) 

**Variable List:**
* **site** : camera site ID
* **datetime** : the datetime (year-month-day hour:minute:second) of the image 
* **species** : the species in the image. Note this still contains "Unknowns" and will need to be filtered/cleaned before any analysis.



### Data specific information for : [outputs/bighorn_30min_independent_detections.csv]  

* **Number of variables/columns:** 5
* **Number of observations/rows:** 5940 (one row for each independent detection of a species at each site) 

**Variable List:**
* **site** : camera site ID
* **datetime** : the datetime (year-month-day hour:minute:second) of the image 
* **species** : the species in the independent detection. Note this still contains "Unknowns" and will need to be filtered/cleaned before any analysis.
* **timediff** : the time difference between subsequent detections for the same species at the same site 
* **Event.ID** : individual identifier for each detection

### Data specific information for: [outputs/bighorn_covariates.csv]

* **Number of variables:** 49
* **Number of cases/rows:** 1680

**Variable List:**

So at the risk of sounding lazy, there are a lot of variables here listed. Here is the relevant section from Laura's thesis on page 21: "To determine which landscape factors best supported the occurrence of wildlife species, I used three competing models with three corresponding sets of landscape covariates: an activity model, a linear disturbance model, and a natural landcover model (Tabled 2.3 and 2.4). Covariates were measured by building buffers (250m-2500m, in 250m increments) (Fisher et al., 2011) around wildlife cameras and extracting landcover variables within each buffer. For the activity model, I used the predicted peak activity on roads, cutlines, and ATV trails (Figure 2.4). For the linear disturbance features model, I obtained data on cutlines from ABMI’s 2017 Human Footprint Inventory (ABMI, 2017), and I obtained road and ATV trail data from Government of Alberta staff (Table 2.3). For the natural landscape features model, I used a Landsat dataset classified into habitat types (Nijland et al., 2015) (Table 2.3)."

I would recommend users either:
1) Read the relevant literature folder and the sources cited for these variables or
2) Depending on the specificity needed, re-extract variables on your own. 

***


Fin. 


