# Assignment 01: Dataset Visualization and Descriptive Analysis

This assignment implements the first Data Mining coursework task using the Diabetes dataset from Kaggle. The work focuses on dataset preparation, NumPy conversion, descriptive statistics, and interactive visual analysis using Plotly.

The assignment is mainly about understanding how a dataset behaves before applying mining or machine learning algorithms. The notebook works like a small visual data-profiling pipeline: it loads the dataset, selects the required real-valued dimensions, checks the class labels, creates 2D and 3D plots, adds class mean points, and generates several statistical visualizations.

## Dataset

**Dataset used:** Diabetes Dataset  
**Source:** Kaggle dataset `mathchi/diabetes-data-set`  
**File:** `diabetes.csv`  
**Rows:** 768  
**Columns:** 9  
**Class label:** `Outcome`

The original dataset contains diagnostic measurements related to diabetes prediction. For the assignment requirements, the notebook selects the first three real-valued dimensions and keeps the final class label column:

| Selected Column | Role |
|---|---|
| `Pregnancies` | First real-valued dimension |
| `Glucose` | Second real-valued dimension |
| `BloodPressure` | Third real-valued dimension |
| `Outcome` | Class label |

For the circle segment plot and parallel coordinates plot, the notebook uses the first seven real-valued dimensions from the full dataset.

## What Is Done in This Assignment

The notebook completes the following workflow:

1. Loads the Diabetes dataset using `kagglehub` or a local `diabetes.csv` file.
2. Reads the CSV file into a pandas DataFrame.
3. Checks for missing values and negative numeric values.
4. Checks whether the dataset contains identifier columns such as ID, serial number, or name.
5. Selects the first three real-valued dimensions and the class label.
6. Saves the four-column working dataset to `outputs/diabetes_first_three_dimensions.csv`.
7. Converts the selected DataFrame into a NumPy array.
8. Creates interactive 2D and 3D scatter plots using class-based marker shapes.
9. Calculates class-wise mean points and overlays them on the 2D and 3D scatter plots.
10. Draws histograms for the first three dimensions.
11. Calculates standard deviation for the first three dimensions.
12. Draws boxplots for all selected dimensions.
13. Draws class-wise grouped boxplots.
14. Creates a 3 × 3 scatterplot matrix.
15. Creates a circle segment plot for the first seven real-valued features.
16. Creates a parallel coordinates plot for the first seven real-valued features.

## Repository Structure

```text
data-mining/
└── assignment-01-data-visualization/
    ├── README.md
    ├── docs/
    │   └── assignment_01_instruction.docx
    ├── notebooks/
    │   └── assignment_01_data_visualization.ipynb
    ├── outputs/
    │   └── html/
    │       ├── q07_interactive_2d_scatter.html
    │       ├── q08_interactive_3d_scatter.html
    │       ├── q09_2d_scatter_with_class_means.html
    │       ├── q10_3d_scatter_with_class_means.html
    │       ├── q11_histogram_pregnancies.html
    │       ├── q11_histogram_glucose.html
    │       ├── q11_histogram_blood_pressure.html
    │       ├── q13_boxplots_first_three_features.html
    │       ├── q14_boxplots_by_class.html
    │       ├── q15_scatter_matrix.html
    │       ├── q16_circle_segment_plot.html
    │       └── q17_parallel_coordinates.html
    └── requirements.txt
```

## How to Run

Install the required libraries:

```bash
pip install -r assignment-01-data-visualization/requirements.txt
```

Then open the notebook:

```bash
jupyter notebook assignment-01-data-visualization/notebooks/assignment_01_data_visualization.ipynb
```

If `kagglehub` cannot download the dataset in your environment, manually download `diabetes.csv` from Kaggle and place it in:

```text
assignment-01-data-visualization/data/diabetes.csv
```

The notebook will automatically look for the dataset in the local `data/` folder before attempting to download it.

## Visual Outputs

The plots are generated with Plotly, so they are interactive inside Jupyter Notebook. HTML copies are also saved in `outputs/html/`.

| Output | File |
|---|---|
| 2D scatter plot | `outputs/html/q07_interactive_2d_scatter.html` |
| 3D scatter plot | `outputs/html/q08_interactive_3d_scatter.html` |
| 2D scatter with class means | `outputs/html/q09_2d_scatter_with_class_means.html` |
| 3D scatter with class means | `outputs/html/q10_3d_scatter_with_class_means.html` |
| Histograms | `outputs/html/q11_histogram_*.html` |
| Boxplots | `outputs/html/q13_boxplots_first_three_features.html` |
| Class-wise boxplots | `outputs/html/q14_boxplots_by_class.html` |
| Scatterplot matrix | `outputs/html/q15_scatter_matrix.html` |
| Circle segment plot | `outputs/html/q16_circle_segment_plot.html` |
| Parallel coordinates | `outputs/html/q17_parallel_coordinates.html` |

## Requirement Mapping

| Assignment Requirement | Where It Is Done in the Notebook | Explanation |
|---|---|---|
| 1. Download the assigned dataset | Section 2: Load the Dataset | Uses `kagglehub.dataset_download()` if `diabetes.csv` is not found locally. |
| 2. Read CSV using pandas | Section 2: Load the Dataset | Reads the dataset with `pd.read_csv()`. |
| 3. Discard ID/name/identifier columns | Section 4: Remove Identifier Columns and Select Required Dimensions | Checks for ID-like column names. The Diabetes dataset does not contain an ID column. |
| 4. Keep first three real-valued dimensions and label | Section 4 | Selects `Pregnancies`, `Glucose`, `BloodPressure`, and `Outcome`. |
| 5. Convert DataFrame to NumPy array | Section 5 | Uses `working_df.to_numpy()` and stores class label meanings. |
| 6. Use Plotly for interactive plots | Section 6: Plotting Helper | All visualizations use Plotly and are saved as interactive HTML files. |
| 7. 2D plot using first two dimensions | Section 7 | Creates a Plotly 2D scatter plot using class-specific marker shapes. |
| 8. 3D plot using first three dimensions | Section 8 | Creates a Plotly 3D scatter plot using class-specific marker shapes. |
| 9. Add class mean points to 2D plot | Section 9 | Calculates class-wise means and overlays larger mean markers. |
| 10. Add class mean points to 3D plot | Section 10 | Repeats the same mean overlay logic for the 3D plot. |
| 11. Histogram for each first-three dimension | Section 11 | Draws one histogram per selected feature. |
| 12. Calculate standard deviation | Section 12 | Calculates sigma using pandas `.std()`. |
| 13. Boxplots for first three dimensions | Section 13 | Draws boxplots for all data points across the selected features. |
| 14. Boxplots for each class separately | Section 14 | Uses a melted DataFrame to draw grouped class-wise boxplots. |
| 15. 3 × 3 scatter matrix | Section 15 | Uses `px.scatter_matrix()` for the first three dimensions. |
| 16. Circle segment plot for first seven dimensions | Section 16 | Normalizes the first seven numeric features and plots them on a circular/radar-style plot. |
| 17. Parallel coordinates for first seven dimensions | Section 17 | Uses `go.Parcoords()` with class-based line coloring and original feature scales. |

## Explanation Notes

### Why were identifier columns removed?
Identifier columns such as ID, serial number, patient name, or record number do not describe the actual properties of the data point. They are only used to identify rows. Keeping them can mislead visualization or analysis because their numeric values may look meaningful even though they are not real features.

### Why were only three dimensions selected first?
The assignment specifically asks to keep the first three real-valued dimensions and the class label. This makes the dataset suitable for 2D and 3D visualization while keeping the analysis simple and interpretable.

### Why convert the DataFrame to a NumPy array?
NumPy arrays are the basic numerical format used by many machine learning and data mining algorithms. Converting the DataFrame shows that the cleaned tabular data can be used for later numerical processing.

### Why use different shapes for classes?
Different marker shapes allow the class information to be visible even when colors are not enough. This is especially useful in dense scatter plots.

### What do the mean points show?
The class mean point summarizes the average position of each class in the selected feature space. If class means are far apart, the selected features may help separate the classes. If they overlap heavily, the selected features may not separate classes clearly by themselves.

### Why use histograms and boxplots?
Histograms show the distribution of a single feature. Boxplots summarize median, quartiles, spread, and outliers. Together, they help identify feature skewness, variation, and unusual values.

### What does the scatterplot matrix show?
The scatterplot matrix shows pairwise relationships between the selected features. It helps identify visible separation, correlation, and overlapping class patterns.

### What do circle segment and parallel coordinates plots add?
Both visualizations help inspect more than three dimensions at once. The circle segment plot gives a compact radial comparison after normalization, while the parallel coordinates plot keeps feature axes visible and allows class-colored comparison across seven dimensions.

## Tools Used

- Python
- pandas
- NumPy
- Plotly
- kagglehub
- Jupyter Notebook
