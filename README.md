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

# Results

## Overview

We analyzed two national crash databases to see if shared e-scooters changed when drunk driving crashes happened. The Crash Report Sampling System (CRSS) covers all police reported collisions. The Fatality Analysis Reporting System (FARS) covers only fatal crashes. We compared patterns from before scooters launched (2016 to 2017) to after they became widespread (2018 to 2023).

## Finding 1: Overall DUI Rates Did Not Change

In the CRSS data, we built a model to predict whether a crash involved alcohol. The post 2018 odds ratio was about 0.89 with a p-value around 0.007. This means the weighted proportion of police reported DUI crashes was slightly lower after 2018, even after we accounted for time trends, seasonal patterns, and the pandemic years. Our Poisson count model gave a similar result with a rate ratio of about 0.90. Since both estimates fall below 1, the CRSS results do not suggest an increase in DUI crash involvement after 2018.

The FARS results showed even less evidence of a change. The DUI proportion model, the Poisson count model, and the nighttime timing model all produced post-period estimates very close to 1. None of these results were statistically significant. This suggests that fatal DUI crash patterns remained broadly stable across the entire study period.

This indicated that after 2018, which includes the rise of shared e-scooters, was not associated with an increase in DUI crashes. If anything, the CRSS data pointed to a small decrease. The FARS data showed no meaningful change at all.

## Finding 2: Late Night Remains the Highest Risk Period

We built a separate model focused specifically on whether DUI crashes became more concentrated during late-night hours after 2018. For CRSS, this nighttime timing model was not statistically significant. The odds ratio was about 1.04 with a p-value of around 0.57. This means that while DUI crashes remain heavily concentrated between 10 PM and 2 AM, the share of crashes occurring during these late-night hours did not change after 2018. The timing pattern appears stable across the pre-scooter and post-scooter periods. For FARS, the nighttime timing model also showed no significant change. This is consistent with what we saw in our EDA plots. The pre and post-period curves and heatmaps looked very similar, with DUI crashes consistently peaking during late-night hours.

This means that the introduction of shared e-scooters did not alter when DUI crashes tend to happen. Late night remains the highest risk period, just as it was before scooters arrived.

## Finding 3: Chi-Square Tests Confirm Stable Timing Distributions

We conducted chi-square tests to compare whether DUI-related crashes are distributed differently across the 24 hours of the day before and after 2018. Large datasets like ours can produce statistically significant chi-square results even for very small differences. However, our EDA plots clearly show that the overall pattern remains similar. DUI crashes are consistently most concentrated during late-night hours, especially around weekend nightlife periods.

This highlights that any statistical differences detected by the chi-square tests are likely driven by the large sample size rather than meaningful changes in crash timing. The visual evidence strongly supports the conclusion that the hourly distribution of DUI crashes stayed stable.

## Summary of Findings

Taken together, these results do not support the idea that the post 2018 period was associated with an increase in DUI-related crashes or a major shift in when those crashes occur. The CRSS data actually showed a small decrease in DUI crash proportion, while FARS showed no meaningful change. These findings suggest that national DUI crash patterns remained relatively stable across the pre-scooter and post-scooter periods.

It is important to be clear about what these results do not say. We cannot conclude that shared e-scooter programs did not affect DUI crashes. Our analysis used national crash data and a broad post 2018 indicator. We did not use city-level scooter rollout data or a treatment control design. Therefore, these results are best interpreted as descriptive evidence. Within national CRSS and FARS crash data, we simply do not observe a clear post 2018 increase or timing shift in DUI-related crashes.

## Limitations and What We Would Do Next

### Limitations of This Study

- **Single national cutoff**: Our analysis treated 2018 as the cutoff for the post-scooter period. But scooter programs did not launch everywhere at the same time. Some cities got scooters in 2018, others in 2019 or later, and some still do not have them. Using a single national cutoff lumps together cities with very different scooter histories. This makes it harder to detect true effects.

- **No scooter crash identification**: We could not identify which crashes involved scooters. This is a critical limitation. Our hypothesis is specifically about intoxicated people riding scooters. But our data does not tell us whether a DUI crash involved a scooter, a car, a bicycle, or a pedestrian. Without this information, we are testing a very indirect relationship. The effect we are looking for, if it exists, is diluted by all the DUI crashes that have nothing to do with scooters.

- **Pandemic disruptions**: The pandemic created unusual conditions. The 2020 to 2021 period was unlike any other in recent history. Traffic volumes dropped dramatically. Driving patterns changed. Alcohol consumption patterns shifted. Police enforcement changed. These disruptions make it harder to isolate the effect of scooter programs, especially since our post period includes these unusual years.

- **National aggregation masks local effects**: Scooter programs are local. Their effects, if any, are likely to be strongest in cities with high scooter usage. By analyzing the entire country, we average together high scooter cities with low scooter cities and places that have no scooters at all. This could hide real effects that exist only in certain places.

### What We Would Do With More Time and Data

- **Analyze cities separately**: We would focus on cities with high scooter adoption rates, those in the top quarter of per-person scooter trips. We would compare them to cities with few or no scooters. This would provide a stronger test of whether scooter density matters.

- **Identify scooter crashes directly**: We would try to obtain data that specifically identifies crashes involving e-scooters. Some local police departments and hospitals collect this information. Focusing only on scooter-involved DUI crashes would give us a much more direct test of whether intoxicated scooter riding increased after scooters became available.

- **Use interrupted time series models**: We would apply more sophisticated statistical methods that account for pre-existing trends, seasonal patterns, and correlations between crashes on nearby days. This approach would better isolate the effect of scooter introduction from other things that changed over time.

## Conclusion

Our analysis did not find evidence that shared e-scooters changed when DUI crashes happened. However, important limitations mean this question remains open for future research. We could not identify the scooter-involved crashes directly. We also could not examine local effects in scooter-heavy cities. A null finding at the national level does not rule out meaningful local effects. The pandemic-related anomaly also shows how sensitive crash patterns are to major societal disruptions. Future research using more detailed data and stronger study designs is needed to definitively answer whether shared e-scooters help, harm, or have no effect on alcohol impaired traffic safety.
