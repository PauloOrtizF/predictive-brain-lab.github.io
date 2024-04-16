---
layout: default
title: BIDS Coin
---

# BIDS Coin
These are the steps to convert the raw DICOM data into the BIDS format:

```
cd /project/31XXXXX.19 # this directory contains the 'raw' folder with all DICOMs (31XXXXX.19 is your project ID)

# load bidscoin on the DCCN mentat cluster
module add bidscoin
source activate /opt/bidscoin

# optional: if your data does not follow the default raw structure (e.g. if you run a pilot without a dedicated project ID)
# dicomsort.py # arrange DICOMs into the default raw structure (see here for details)

# create sample folder structure
bidstrainer.py bids

# IMPORTANT: manually copy example DICOMs (1 per series/run from the raw folder of 1 participant) into the corresponding BIDS folder (e.g. put BOLD data into ~/labwiki/projID/bids/code/samples/func/bold #TODO @DAVID). Do the same for the event files.

# create a ``bidsmap_sample.yaml`` file from DICOMs
bidstrainer.py bids

# Maps yaml file to raw folder structure. Also finds unknown series (i.e. without sample DICOM); check bids/code/bidsmap.yaml "extra_data" for unknown series, add to sample folder and rerun bidstrainer.py bids
bidsmapper.py raw bids

# In the bids/code/bidsmap.yaml file, you may want to rename the "task_label" field of the functional scans into something more readable, e.g. the task name of that run.

# Converts dicom 2 bids for each subject in raw, outputs to bids folder
bidscoiner.py raw bids

# NOTE: You should update the content of the dataset_description.json and README files in your bids folder and you may need to provide e.g. additional *_scans.tsv,*_sessions.tsv or participants.json files (see the BIDS specification for more information). Similarly BIDScoin does currently not support log or event files, thus you also need to manually add these.
```
