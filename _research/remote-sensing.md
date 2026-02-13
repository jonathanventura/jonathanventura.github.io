---
title: "Automated ecological and environmental monitoring from remote sensing data"
excerpt: "Developing neural network models to catalog forests and evaluate post-wildfire damage"
collection: research
---


Sponsors: California Department of Forestry and Fire Protection, U.S. Forest Service

## Urban forest inventory

### An end-to-end deep learning solution for automated LiDAR tree detection in the urban environment

Cataloging and classifying trees in the urban environment is a crucial step in urban and environmental planning; however, manual collection and maintenance of this data is expensive and time-consuming. Although algorithmic approaches that rely on remote sensing data have been developed for tree detection in forests, they generally struggle in the more varied urban environment. This work proposes a novel end-to-end deep learning method for the detection of trees in the urban environment from remote sensing data. Specifically, we develop and train a novel PointNet-based neural network architecture to predict tree locations directly from LiDAR data augmented with multi-spectral imagery. We compare this model to a number of high-performing baselines on a large and varied dataset in the Southern California region, and find that our method outperforms all baselines in terms of tree detection ability (75.5% F-score) and positional accuracy (2.28 meter root mean squared error), while being highly efficient. We then analyze and compare the sources of errors, and how these reveal the strengths and weaknesses of each approach. Our results highlight the importance of fusing spectral and structural information for remote sensing tasks in complex urban environments.

📕 [Paper](https://www.sciencedirect.com/science/article/pii/S2667393225000110)
 
### Harnessing Neural Networks for Broad-Scale Urban Canopy Cover Mapping: A Remote Sensing Approach in California

The California Urban Forestry Act was passed to plan a 10% increase in tree canopy cover by 2035, prioritizing disadvantaged and low-canopy areas. To support this goal, we developed a model to predict urban canopy cover in California using National Agricultural Image Program (NAIP) aerial imagery from 2016-2022.
Using open-source datasets available across the United States, our methods show how canopy cover can be quickly and accurately assessed. The canopy cover dataset we develop can be used to inform urban forest management by identifying places where canopy cover is low, and future tree planting should be prioritized. 

📕 [Abstract](https://ui.adsabs.harvard.edu/abs/2024AGUFMGC54A..06P/abstract)

### Individual tree detection in large-scale urban environments using high-resolution multispectral imagery

Systematic maps of urban forests are useful for regional planners and ecologists to understand the spatial distribution of trees in cities. However, manually-created urban forest inventories are expensive and time-consuming to create and typically do not provide coverage of private land. Toward the goal of automating urban forest inventory through machine learning techniques, we performed a comparative study of methods for automatically detecting and localizing trees in multispectral aerial imagery of urban environments, and introduce a novel method based on convolutional neural network regression. Our evaluation is supported by a new dataset of over 1,500 images and almost 100,000 tree annotations, covering eight cities, six climate zones, and three image capture years. To demonstrate the scalability of the technique, we produced the first map of trees across the entire urban forest of California.

📕 [Paper](https://www.sciencedirect.com/science/article/pii/S1569843224002024)
🗺️ [Interactive Map](https://jventu09.users.earthengine.app/view/urban-tree-detector)
💻 [Code](https://github.com/jonathanventura/urban-tree-detection)
🌳 [Dataset](https://github.com/jonathanventura/urban-tree-detection-data)

### Diversity and structure in California’s urban forest: What over six million data points tell us about one of the world's largest urban forests

Urban street trees provide many benefits to surrounding communities, but our ability to assess such benefits relies on the availability of high-quality urban tree data. While these data are numerous, they are not available in an easily accessible, centralized place. To fill this gap, we aggregated public and private data into a single, comprehensive inventory of urban trees in California called the California Urban Forest (CUF) Inventory. This aggregated inventory of one of the world's largest urban forests provides the data necessary to assess the structure, diversity, and value of California’s urban forests at multiple spatial scales.

📕 [Paper](https://www.sciencedirect.com/science/article/pii/S1618866722002229)
🌳 [Data dashboard](https://lookerstudio.google.com/u/0/reporting/880d448d-de26-48d3-b563-0c6317e456e4/page/jWHKB)

## Ecological monitoring

### A Convolutional Neural Network Classifier Identifies Tree Species in Mixed-Conifer Forest from Hyperspectral Imagery

In this study, we automate tree species classification and mapping using field-based training data, high spatial resolution airborne hyperspectral imagery, and a convolutional neural network classifier (CNN). We tested our methods by identifying seven dominant trees species as well as dead standing trees in a mixed-conifer forest in the Southern Sierra Nevada Mountains, CA (USA) using training, validation, and testing datasets composed of spatially-explicit transects and plots sampled across a single strip of imaging spectroscopy. By training a CNN classifier using field data and hyperspectral imagery, we were able to accurately identify tree species and predict their distribution, as well as the distribution of tree mortality, across the landscape. The hyperspectral CNN model captures the species composition changes across ~700 meters (1935 to 2630 m) of elevation from a lower-elevation mixed oak conifer forest to a higher-elevation fir-dominated coniferous forest. High resolution tree species maps can support forest ecosystem monitoring and management, and identifying dead trees aids landscape assessment of forest mortality resulting from drought, insects and pathogens. We publicly provide our code to apply deep learning classifiers to tree species identification from geospatial imagery and field training data.

📕 [Paper](https://www.mdpi.com/2072-4292/11/19/2326)
💻 [Code](https://github.com/jonathanventura/canopy)

### Application of Deep Learning for Classification of Intertidal Eelgrass from Drone-Acquired Imagery

Shallow estuarine habitats are globally undergoing rapid changes due to climate change and anthropogenic influences, resulting in spatiotemporal shifts in distribution and habitat extent. Yet, scientists and managers do not always have rapidly available data to track habitat changes in real-time. In this study, we applied image segmentation techniques to two years of high-resolution drone-based imagery of eelgrass (Zostera marina) meadows in the Morro Bay estuary, which has undergone large eelgrass declines and the subsequent recovery of seagrass meadows in the last decade. The model accurately classified eelgrass across a range of conditions and sizes from meadow-scale to small-scale patches that are less than a meter in size. This study demonstrates the potential for machine learning methods to accurately support the active monitoring and analysis of seagrass dynamics.

📕 [Paper](https://www.mdpi.com/2072-4292/15/9/2321)

## Wildfire preparedness and response

### DamageMap: A post-wildfire damaged buildings classifier

The increasing frequency and severity of wildfire events in the last few decades has created an urgent need for new technologies that allow rapid surveying and assessment of post-wildfire building damage. However, existing technologies lack in accuracy and ability to scale to effectively aid disaster relief and recovery. Even today, most wildfire event inspectors need to physically visit the areas impacted by wildfires and manually classify building damage, which requires considerable time and resources. Here, we present DamageMap, an artificial intelligence-powered post-wildfire building damage classifier.  DamageMap may help governmental and non-governmental agencies rapidly survey building damage using post-wildfire aerial or satellite imagery in wildfire-impacted areas.

📕 [Paper](https://www.sciencedirect.com/science/article/pii/S221242092100501X)
🗺️ [Interactive Map](https://kkraoj.users.earthengine.app/view/damagemap)
💻 [Code](https://github.com/MariosGalanis/DamageMap)
