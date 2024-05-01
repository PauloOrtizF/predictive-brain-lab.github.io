---
layout: default
title: fMRI
rank: 5
---
This section provides useful information into conducting fMRI experiments as a member of the Predictive Brain Lab. The essential and most important information about performing fMRI experiments at the DCCN can be found on the [Intranet website](https://intranet.donders.ru.nl/index.php?id=mri-lab). Remember to always read all the information provided by the insitute, as practices may differ from your previous fMRI experiences.

This page provides a concise summary of guidelines for performing an fMRI experiment, along with tips and tricks for data analysis and references to useful resources.

- [fMRI Checklist](#fmri-checklist)
- [fMRI Analysis](#fmri-analysis)
  - [BIDS Documentation](#bids-documentation)
- [Analysis Pipeline](#analysis-pipeline)
  - [Preprocessing With Fmriprep](#preprocessing-with-fmriprep)

# fMRI Checklist

The two documents below offer a template outlining the steps necessary to set-up and complete an fMRI measurement session. You can utilize one of the template documents and adapt it to suit the requirements of your own experiment. The extensive checklist version contains information for EyeTracker usage in case you are making use of this tool in your experimental set-up.

* [Complete and Extensive Checklist](https://docs.google.com/document/d/1LSj8qO4hI7IF3ML19ZjUFMDq2pEnfQV1yOkJQaIOaWg/edit?usp=sharing)
* [Shorter Checklist](https://docs.google.com/document/d/14972YaVPQTBHaFrlEc9Bvi6kLikvxVHCsNTFxuvzzSE/edit?usp=sharing)

**_Note_**: Remember to always follow the general guidelines of data management of the Donders Institute. This is especially important for reproducibility in neuroimaging experiments and sharing your results with other lab members. 

# fMRI Analysis

This section will provide valuable insights into analyzing fMRI experiments. It includes a collection of resources compiled by various lab members over the years, which they found useful for analyzing this type of data. 

## BIDS Documentation 
[BIDS](http://bids.neuroimaging.io/) describes a format to organize neuroimaging and behavioural data (_i.e.,_ a folder structure, naming structure, etc.). It specifies the file format of the MRI files (_i.e.,_ compressed Nifti: .nii.gz files), defines rules on how to name them (making use of 'key-value' pairs, _e.g.,_ sub-01_ses-1_task-1back_run-1_bold.nii.gz), and outlines the file/folder structure of your dataset (where each subject has its own directory with separate subdirectories for different MRI modalities, including fieldmaps, functional, diffusion, and anatomical MRI). In order to be able to use **fMRIPrep** (described below), it is necessary to have all your data transformed into this format. It **is mandatory for members of the Predictive Brain Lab to use this format.** 

There are a variety of tools that can be used to convert the "raw" scanner data (_e.g.,_ in DICOM or PAR/REC format) to BIDS. At the Predictive Brain Lab, we mostly use the [bidscoin tool](https://github.com/Donders-Institute/bidscoin). But if you are curious, you can check [heudiconv](https://github.com/nipy/heudiconv) for an alternative. 

### BIDScoin
BIDScoin is a user-friendly Python application suite that converts ("coins") source-level (raw) neuroimaging data sets to standardized data sets that are organized according to the Brain Imaging Data Structure (BIDS) specification. BIDScoin is available on the DCCN cluster. For an extensive tutorial on how to use BIDScoin, see [here](https://bidscoin.readthedocs.io/en/stable/tutorial.html).

# Analysis Pipeline
Once you have converted the raw data files to NIFTI using BIDScoin, you can proceed with the data preprocessing steps.

## Preprocessing With Fmriprep
[fMRIPrep](https://fmriprep.org/en/stable/) is a functional magnetic resonance imaging (fMRI) data preprocessing pipleine designed to offer easily accessible, state-of-the-art interface that is roubst to changes in scan acquisition protocols and requires minimal user input. Additionally, it provides easily interpretable and comprehensive error and output reporting. It performs basic processing steps (coregistration, normalization, unwarping, noise component extraction, segmentation, skull-stripping, etc.) providing outputs that can be easily submitted to a variety of group level analyses, including task-based or resting-state fMRI, graph theory measures, and surface or volume-based statistics. The software makes use of the functionality from many different neuroimaging software packages (_e.g.,_ Freesurfer and FSL), in a way that ensures each step in the pipeline get executed by the software that arguably does it best. 

