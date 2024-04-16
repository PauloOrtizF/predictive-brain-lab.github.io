---
layout: default
title: fMRI
rank: 4
---
This section provides useful information into conducting fMRI experiments as a member of the Predictive Brain Lab. The essential and most important information about performing fMRI experiments at the DCCN can be found on the [Intranet website](https://intranet.donders.ru.nl/index.php?id=mri-lab). Remember to always read all the information provided by the insitute, as practices may differ from your previous fMRI experiences.

This page provides a concise summary of guidelines for performing an fMRI experiment, along with tips and tricks for data analysis and references to useful resources.

- [fMRI Checklist](#fmri-checklist)
- [fMRI Analysis](#fmri-analysis)
  - [BIDS Documentation}(#bids-documentation)
  -  

# fMRI Checklist

The two documents below offer a template outlining the steps necessary to set-up and complete an fMRI measurement session. You can utilize one of the template documents and adapt it to suit the requirements of your own experiment. The extensive checklist version contains information for EyeTracker usage in case you are making use of this tool in your experimental set-up.

* [Complete and Extensive Checklist](https://docs.google.com/document/d/1LSj8qO4hI7IF3ML19ZjUFMDq2pEnfQV1yOkJQaIOaWg/edit?usp=sharing)
* [Shorter Checklist](https://docs.google.com/document/d/14972YaVPQTBHaFrlEc9Bvi6kLikvxVHCsNTFxuvzzSE/edit?usp=sharing)

**_Note_**: Remember to always follow the general guidelines of data management of the Donders Institute. This is especially important for reproducibility in neuroimaging experiments and sharing your results with other lab members. 

# fMRI Analysis

This section will provide valuable insights into analyzing fMRI experiments. It includes a collection of resources compiled by various lab members over the years, which they found useful for analyzing this type of data. 

## BIDS Documentation 
[BIDS](http://bids.neuroimaging.io/) describes a format to organize neuroimaging and behavioural data (_i.e.,_ a folder structure, naming structure, etc.) It is mandatory for members of the Predictive Brain Lab to use this format. The raw DICOM data can be automaticallt converted into the BIDS format using the [bidscoin tool](https://github.com/Donders-Institute/bidscoin). 

### BIDScoin
This is employed to convert the raw (DICOM) data to the BIDS format. BIDScoin is available on the DCCN cluster. For an extensive tutorial on how to use BIDScoin, see [here](https://github.com/Donders-Institute/bidscoin#bidscoin-tutorial).

This [document](./fmri/bids-coin.md) highlights the steps to conver the raw (DICOM) data into the BIDS format.


