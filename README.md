# Advanced Research Methods – Final Project  
## Galaxy Watch Heart Rate Data Preprocessing

This repository contains the **data cleaning and preprocessing pipeline** for Galaxy Watch heart rate (HR) data used in the Advanced Research Methods final project.

The main purpose of this repository is to provide an **analysis-ready heart rate dataset** merged with participant-level metadata, so that further statistical analysis or modeling can be performed without additional preprocessing.

---

## Project Scope

- Device: **Samsung Galaxy Watch**
- Signal used: **Heart Rate (HR)**
- Participants: **P02 – P06** (subset used for preprocessing demonstration)
- Data type: **Time-series physiological data**
- My responsibility in the project:
  - Cleaning raw HR data
  - Standardizing identifiers
  - Merging with metadata
  - Exporting a clean dataset for downstream analysis

---
## Repository Structure
'''Advanced_Research_Methods_Final/
│
├── data/
│ ├── raw/
│ │ ├── HR2.csv
│ │ ├── HR3.csv
│ │ ├── HR4.csv
│ │ ├── HR5.csv
│ │ ├── HR6.csv
│ │ └── Meta.csv
│ │
│ └── processed/
│ └── galaxywatch_hr_clean_final.csv
│
├── notebooks/
│ └── hr_data_cleaning.ipynb
│
└── README.md '''



---

## Raw Data Description

### HR*.csv files
Each HR file corresponds to one participant’s Galaxy Watch heart rate recording and contains:

- `timestamp` : Unix timestamp (ms)
- `heart_rate` : Heart rate value (bpm)
- `hrstatus`, `ibi`, `ibistatus` : Device-specific status fields
- `uid` : Participant identifier (e.g., P02, P03, …)

### Meta.csv
Participant-level metadata:

| Column | Description |
|------|------------|
| UID | Participant ID |
| AGE | Age of participant |
| GENDER | Biological sex |
| TSST | Trier Social Stress Test score |
| SSST | Social Stress Scale score |
| GalaxyWatch | Wearing side (L/R) |

---

## Data Cleaning Steps (Summary)

All preprocessing steps are implemented in:
notebooks/hr_data_cleaning.ipynb


### Step 1: Load raw HR files
- All HR*.csv files are loaded
- Files are concatenated into a single dataframe

### Step 2: Standardize participant IDs
- Converted `uid` → `UID`
- Ensured consistent formatting (e.g., `P2` → `P02`)
- Removed whitespace and enforced uppercase

### Step 3: Basic data cleaning
- Removed missing or invalid heart rate values
- Filtered physiologically implausible HR values  
  (kept range: **30–220 bpm**)

### Step 4: Merge with metadata
- HR time-series merged with `Meta.csv` using `UID`
- Each HR observation now contains demographic and stress-related variables

### Step 5: Final validation & export
- Checked for missing metadata after merge
- Exported clean dataset as:

- 
---

## Final Output Dataset

**File:**  
`data/processed/galaxywatch_hr_clean_final.csv`

**Main columns:**

- `UID`
- `timestamp`
- `heart_rate`
- `AGE`
- `GENDER`
- `TSST`
- `SSST`
- `GalaxyWatch`

This file is **analysis-ready** and can directly be used for:

- Descriptive statistics
- Stress-related HR analysis
- Time-series visualization
- Regression or mixed-effects models

---

## How to Continue the Project

If you are continuing this project:

1. Use `galaxywatch_hr_clean_final.csv` as the main dataset
2. Aggregate HR over time if needed (mean HR, HRV, etc.)
3. Relate HR features to:
   - TSST / SSST scores
   - Gender or age differences
4. Extend preprocessing to additional participants if required

---

## Notes & Limitations

- Only **Galaxy Watch HR data** was used (no PPG, ACC, or skin temperature)
- Dataset is a subset for demonstration and methodology validation
- Further signal-level analysis (e.g., HRV from IBI) is optional and not required

---

## Author

Preprocessing & data cleaning: **Talatcan Gültekin**

Advanced Research Methods – Final Project




