# Smart Energy Optimization -- Synthetic Dataset Repository

## Overview

This repository contains the 60,000-row (Approximate) synthetic dataset used in the
research paper:

"Smart Energy Optimization and Load Balancing with Machine Learning"

The dataset was generated programmatically to simulate residential
appliance load behavior and overload conditions. It was used to train
and evaluate the machine learning models described in the manuscript.

This repository is provided to ensure research transparency,
reproducibility, and data availability for reviewers and readers.

------------------------------------------------------------------------

## Dataset Description

File included:

synthetic_overload_data.csv

Total Rows: \~60,000\
Time Resolution: 1 row per minute\
Duration Covered: 44 days\
Sampling Interval: 1 minute

The dataset simulates three household electrical loads:

-   Load 1 -- Room Heater\
-   Load 2 -- Water Heater\
-   Load 3 -- Microwave Oven

Each row represents a timestamped snapshot of appliance states and
current consumption values.

------------------------------------------------------------------------

## Dataset Columns

  Column Name      Description
  ---------------- ------------------------------------------------------
  hour             Hour of the day (0--23)
  min              Minute of the hour (0--59)
  date             Date (DD/MM/YYYY)
  load1State       ON/OFF state of Load 1 (0 or 1)
  load2State       ON/OFF state of Load 2 (0 or 1)
  load3State       ON/OFF state of Load 3 (0 or 1)
  load1Current     Current (Amps) of Load 1
  load2Current     Current (Amps) of Load 2
  load3Current     Current (Amps) of Load 3
  totalCurrent     Sum of all load currents
  overload         Binary overload indicator (1 = overload, 0 = normal)
  overloadLoadNo   Load number responsible for overload

------------------------------------------------------------------------

## Synthetic Data Generation Logic

The dataset was generated using a controlled simulation approach with
the following assumptions:

-   Appliances operate only after 6:30 PM\
-   All appliances turn ON at 7:00 PM on active days\
-   Monday and Sunday are treated as OFF days\
-   Current ranges:
    -   Room Heater: 4.0 -- 5.0 A
    -   Water Heater: 3.0 -- 4.0 A
    -   Microwave: 6.5 -- 7.5 A
-   Overload threshold: 10 Amperes

If total current exceeds 10A, the overload flag is set to 1 and the
highest-consuming appliance is identified.

The generation process ensures realistic load fluctuation and controlled
overload events for supervised learning.

------------------------------------------------------------------------

## Data Usage in the Paper

This dataset was used to:

-   Train the Ridge Regression forecasting model\
-   Train the Random Forest baseline model\
-   Perform overload classification\
-   Evaluate MAE, RMSE, R², Precision, Recall, and F1-score

A time-series split (70% training, 15% validation, 15% testing) was
applied during model evaluation.

------------------------------------------------------------------------

## Reproducibility

The dataset was generated using Python. Running the provided generation
script will reproduce the same structured dataset format.

------------------------------------------------------------------------

## Important Note

This dataset is synthetic and simulation-based, designed for controlled
experimental validation of the proposed system architecture.

Real-world multi-household validation is ongoing work and will be
included in future research phases.

------------------------------------------------------------------------

## Contact

MD Akib Rahman\
Department of Computer Science and Engineering\
International University of Business Agriculture and Technology\
Email: akibrahman5200@gmail.com
