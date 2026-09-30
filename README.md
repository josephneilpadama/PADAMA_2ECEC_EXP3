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
```
</details>

The CSV file was imported using pd.read_csv(). Displaying the full DataFrame confirmed that all 32 vehicle models and their respective specification attributes were loaded accurately into memory without modifying the original source file.

## A. POSITIONAL AND LABEL-BASED SLICING
Display the shape and list of column names of cars. Using positional slicing with .iloc, extract rows 6 through 10 (where row 1 represents index 0). From this subset, select only the columns Model, mpg, cyl, hp, and gear using label-based indexing.

<details>
<summary><b>Click to Expand: Item A Code and Output</b></summary>
  
```python
print("Shape of DataFrame:", cars.shape)
print("\nList of Columns:")
print(cars.columns.tolist())

cars_6_to_10 = cars.iloc[5:10]
cars_6_to_10

cars_6_to_10_selected = cars_6_to_10[['Model', 'mpg', 'cyl', 'hp', 'gear']]

cars_6_to_10_selected
```
</details>

The .shape attribute and .columns.tolist() were used to retrieve the dimensions and all column names. Since 0-based indexing is used, positional slicing cars.iloc[5:10] was applied to extract rows 6 through 10. Label-based bracket indexing [['Model', 'mpg', 'cyl', 'hp', 'gear']] was then applied to filter the sliced rows down to the specified columns.

## B. MODEL LOOKUP
Use Boolean indexing on the Model column to locate specific vehicles without hardcoding row indices:

Display the complete row for Toyota Corolla and store it in toyota.
Display only Model, mpg, hp, and wt for Pontiac Firebird and store it in pontiac.

<details>
<summary><b>Click to Expand: Item B Code and Output</b></summary>

```python

toyota = cars[cars['Model'] == 'Toyota Corolla']
toyota

pontiac = cars[cars['Model'] == 'Pontiac Firebird'][['Model', 'mpg', 'hp', 'wt']]

display(pontiac)
```
</details>

Boolean conditions were applied directly to the Model column to find records dynamically. For Toyota Corolla, cars['Model'] == 'Toyota Corolla' extracted the complete matching row into toyota. For Pontiac Firebird, [['Model', 'mpg', 'hp', 'wt']] was appended to the Boolean filter to extract and store only the four required columns in pontiac.

## C. MULTI-MODEL SUBSETTING
Create a DataFrame named selected_cars containing only Datsun 710, Lotus Europa, and Ferrari Dino. Retain only the columns Model, mpg, cyl, hp, and gear. Verify that the final DataFrame contains exactly 3 rows and 5 columns.

<details>
<summary><b>Click to Expand: Item C Code and Output</b></summary>

```python

models = ['Datsun 710', 'Lotus Europa', 'Ferrari Dino']
cols = ['Model', 'mpg', 'cyl', 'hp', 'gear']

selected_cars = cars[cars['Model'].isin(models)][cols]
display(selected_cars)
```
</details>

A list of the three target models was defined and passed into .isin() to filter the dataset without multiple OR conditions. The required columns were extracted and assigned to selected_cars. Calling selected_cars.shape verified that the final DataFrame contains exactly 3 rows and 5 columns.
