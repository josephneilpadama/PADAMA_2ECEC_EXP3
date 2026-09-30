# Experiment 4: Data Wrangling and Data Visualization

**Name:** Padama, Joseph Neil C.  
**Section:** 2ECE-C  
**Date Submitted:** September 17, 2026  

---

## Objectives

At the end of this laboratory activity, the student should be able to:
1. load a CSV dataset into a Pandas DataFrame;
2. select rows and columns using positional and label-based indexing;
3. filter records using conditions on a DataFrame column; and
4. extract a well-defined subset of data without changing the source data.
---

### Setup

The initial code imports Pandas as `pd`, loads the `cars.csv` dataset into a DataFrame named `cars`, and previews the entire dataset to inspect its structure and features.

<details>
<summary><b>Click to Expand: Initial Setup Code and Output</b></summary>

```python
import pandas as pd

# Load the cars.csv dataset
cars = pd.read_csv('cars.csv')
cars
