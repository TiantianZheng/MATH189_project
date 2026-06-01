# MATH 189 DUI Crash Analysis

This project analyzes DUI-related crash patterns using NHTSA FARS and CRSS data from 2016-2024.

## Data

The raw FARS and CRSS datasets are not committed to GitHub because they are several gigabytes in size. The notebook includes code to download and organize the data directly from NHTSA.

- FARS: Fatality Analysis Reporting System, fatal crashes
- CRSS: Crash Report Sampling System, nationally representative police-reported crashes

## Main file

- `project.ipynb`: data download, EDA, statistical analyses, and results interpretation

## Notes

CRSS analyses use sampling weights. FARS is treated as an unweighted census of fatal crashes.
