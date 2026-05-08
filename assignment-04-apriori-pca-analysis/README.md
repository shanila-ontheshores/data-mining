# Assignment 04: Apriori Market Basket Analysis and PCA Projection

This folder contains the cleaned notebook and documentation for **Data Mining Assignment 04**. The assignment has two major parts:

- **4A:** Restaurant sales analysis using transaction preprocessing, Apriori frequent itemset mining, and a package-discount revenue simulation.
- **4B:** Numeric data analysis using interactive 2D/3D visualization, centering, projection onto a line and a plane, covariance analysis, eigen decomposition, and PCA-style projection.



---

## Folder Structure

```text
assignment-04-apriori-pca-analysis/
├── README.md
├── docs/
│   └── assignment_04_instruction.docx
├── notebooks/
│   └── assignment_04_apriori_pca_analysis.ipynb
├── outputs/
│   ├── html/
│   │   ├── q4b_01_original_2d_scatter.html
│   │   ├── q4b_02_centered_2d_scatter.html
│   │   ├── q4b_03_centered_2d_with_line.html
│   │   ├── q4b_04_projection_on_line.html
│   │   ├── q4b_05_original_3d_scatter.html
│   │   ├── q4b_06_centered_3d_scatter.html
│   │   ├── q4b_07_centered_3d_with_given_plane.html
│   │   ├── q4b_08_projection_on_given_plane.html
│   │   ├── q4b_09_pca_plane_projection.html
│   │   └── q4b_10_u_basis_2d_coordinates.html
│   └── logs/
│       └── results_summary.txt
└── requirements.txt
```

---

## What Is Done in This Assignment

### Part 4A: Restaurant Sales and Apriori

The restaurant dataset contains order-level sales records. Each row represents one order, and each dish has two adjacent columns: quantity ordered and unit price.

The notebook does the following:

1. Loads the restaurant sales dataset.
2. Checks missing values, duplicate rows, and column structure.
3. Separates dish quantity columns from price columns.
4. Converts dish quantities into binary transaction data.
5. Calculates original total sales as the baseline revenue.
6. Implements Apriori-style frequent itemset mining.
7. Finds frequent four-item combo packages using minimum support.
8. Selects the most frequent four-item package.
9. Applies the assignment’s 5% discount and 5% sales-increase assumption.
10. Estimates extra sales from associated items using conditional probability.
11. Compares the new total sales against the original total sales.

### Part 4B: Projection and Numeric Data Analysis

The second part uses a numeric dataset with class labels. The notebook uses the diabetes dataset and keeps numeric features for visualization and projection.

The notebook does the following:

1. Loads the assigned numeric dataset.
2. Cleans invalid or missing values.
3. Converts the dataset into numeric arrays.
4. Creates interactive 2D plots using the first two dimensions.
5. Centers the first two dimensions.
6. Draws the line `x1 = -x2`.
7. Projects centered 2D points onto that line.
8. Creates interactive 3D plots using the first three dimensions.
9. Centers the first three dimensions.
10. Draws the plane spanned by `[1, -2, 1]ᵀ` and `[2, 1, 0]ᵀ`.
11. Projects centered 3D points onto the plane.
12. Computes the covariance matrix using centered data.
13. Computes eigenvalues and eigenvectors.
14. Checks orthonormality.
15. Builds `U = [u1, u2]` from the top two eigenvectors.
16. Projects data using `x' = UUᵀx`.
17. Computes new 2D coordinates using `[x']ᵤ = Uᵀx`.

---

## Key Results

### 4A: Apriori and Discount Simulation

| Result Item | Value |
|---|---:|
| Total orders | 6,307 |
| Number of dish columns | 116 |
| Minimum support | 0.001 |
| Frequent 4-itemsets found | 11 |
| Original total sales | 5,111,310.00 |
| Selected package support | 0.190% |
| Orders containing selected package | 12 |
| Original package revenue | 15,745.00 |
| Revenue change from package discount + package sales increase | -39.36 |
| Associated item uplift | 391.25 |
| Final revenue change | +351.89 |
| Final percentage change | +0.007% |

Selected four-item package:

```text
BBQ Chicken Pizza
Mountain Dew
Pepsi
Water 500ml
```

Conclusion: the discount strategy increased total sales slightly because the uplift from associated items was larger than the package-only loss caused by discounting.

### 4B: Numeric Analysis

| Result Item | Value |
|---|---:|
| Raw dataset shape | 768 × 9 |
| Cleaned dataset shape | 392 × 9 |
| Label column | Outcome |
| Number of classes | 2 |
| Projected PCA-style data shape | 392 × 3 |
| New U-basis coordinate shape | 392 × 2 |

Eigenvalues in descending order:

```text
[958.52991598, 147.92836195, 9.54083702]
```

This means the first two eigenvectors capture the dominant spread of the centered 3D data.

---

## Interactive Outputs

The Plotly visualizations were exported as HTML files in:

```text
outputs/html/
```

Open them in a browser to inspect the interactive plots.

Important files:

| Output | Purpose |
|---|---|
| `q4b_01_original_2d_scatter.html` | Original data using first two dimensions |
| `q4b_02_centered_2d_scatter.html` | Centered 2D data |
| `q4b_03_centered_2d_with_line.html` | Centered 2D data with line `x1 = -x2` |
| `q4b_04_projection_on_line.html` | Projection of 2D points onto the line |
| `q4b_05_original_3d_scatter.html` | Original 3D data |
| `q4b_06_centered_3d_scatter.html` | Centered 3D data |
| `q4b_07_centered_3d_with_given_plane.html` | Centered 3D data with assigned plane |
| `q4b_08_projection_on_given_plane.html` | Projection onto assigned plane |
| `q4b_09_pca_plane_projection.html` | Projection onto PCA-style eigenvector plane |
| `q4b_10_u_basis_2d_coordinates.html` | Final 2D coordinates in the U-basis |

---

## Requirement Mapping

### Assignment 4A

| Assignment Requirement | Where It Is Done in Notebook | Explanation |
|---|---|---|
| Load restaurant sales data | `Part 4A: Restaurant Sales and Apriori Analysis` | Reads the sales file into a pandas DataFrame. |
| Understand row/order format | `4A.1 Data Quality Checks` | Checks Date, OrderId, dish columns, and price columns. |
| Calculate total price per order | `4A.3 Original Total Sales Baseline` | Multiplies quantity by unit price for each dish and sums across dishes. |
| Keep only dish columns for Apriori | `4A.2 Transaction Matrix for Apriori` | Removes Date, OrderId, and price columns from transaction input. |
| Convert nonzero values to 1 | `4A.2 Transaction Matrix for Apriori` | Converts quantity > 0 to 1 and quantity = 0 to 0. |
| Find popular combo package using Apriori | `4A.5` to `4A.9` | Generates itemsets, prunes candidates, counts support, and extracts frequent four-itemsets. |
| Apply 5% discount to package | `4A.10 Discount Simulation` | Applies the discount to the selected four-item package. |
| Assume 5% increase in package sales | `4A.10 Discount Simulation` | Multiplies package revenue by the sales increase factor. |
| Add uplift from other associated items | `Associated Item Uplift` | Uses `p(item \| package)` to estimate extra associated-item revenue. |
| Compare final sales with original sales | `4A.11 Final Sales Comparison` | Calculates new total sales, revenue change, and percentage change. |

### Assignment 4B

| Assignment Requirement | Where It Is Done in Notebook | Explanation |
|---|---|---|
| Load assigned numeric dataset | `Part 4B: Projection, Covariance, and PCA-Style Analysis` | Downloads and reads the numeric dataset. |
| Convert to NumPy array | `4B.1 Original 2D Interactive Plot` | Converts DataFrame features and labels into arrays. |
| Plot first two dimensions | `4B.1 Original 2D Interactive Plot` | Uses Plotly with class-specific marker shapes. |
| Center first two dimensions | `4B.2 Centered 2D Data` | Subtracts the mean vector from the first two dimensions. |
| Draw line `x1 = -x2` | `4B.3 Centered 2D Data with Line` | Uses direction vector `[1, -1]`. |
| Project points onto line | `4B.4 Projection onto the Line x1 = -x2` | Computes projection with `(x·u)u`. |
| Plot first three dimensions | `4B.5 Original 3D Interactive Plot` | Uses Plotly 3D scatter. |
| Center first three dimensions | `4B.6 Centered 3D Data` | Subtracts the 3D mean vector. |
| Plot assigned plane | `4B.7 Centered 3D Data with Given Plane` | Builds plane from `[1, -2, 1]ᵀ` and `[2, 1, 0]ᵀ`. |
| Project points onto plane | `4B.8 Projection onto the Given Plane` | Uses an orthonormal basis and projection matrix. |
| Compute covariance matrix | `4B.9 Numeric Data Analysis` | Uses `(DᵀD) / n` for centered data matrix `D`. |
| Compute eigenvalues/eigenvectors | `Eigenvalues, Eigenvectors, and Orthonormality Check` | Uses NumPy eigen decomposition. |
| Sort eigenvectors by eigenvalues | Same section | Sorts eigenvalues in descending order and rearranges eigenvectors. |
| Verify orthonormality | Same section | Checks `VᵀV`. |
| Form `U = [u1, u2]` | `Principal Subspace Matrix U` | Selects the two eigenvectors with largest eigenvalues. |
| Project with `x' = UUᵀx` | `Projection Using x' = U Uᵀx` | Projects centered 3D data onto the eigenvector plane. |
| Compute `[x']ᵤ = Uᵀx` | `2D Coordinates in the U-Basis` | Converts projected data into 2D coordinates. |

---

## Notes for Explanation / Viva

- **Why calculate original total sales first?**  
  Because the discount strategy must be compared against a baseline. Without original total sales, there is no way to calculate whether the promotion increased or decreased revenue.

- **Why convert dish quantities to 0/1 for Apriori?**  
  Apriori analyzes whether items appear together in transactions. It does not need the number of units ordered, only whether the item was present.

- **Why use support?**  
  Support measures how often an itemset appears in all transactions. A higher support package is a stronger candidate for a combo offer.

- **Why use conditional probability for associated items?**  
  `p(item | package)` estimates how likely another item is ordered when the selected package appears. This supports the assumption that package promotions can also affect related item sales.

- **Why center data before projection/PCA?**  
  Centering moves the data mean to the origin. Projection and covariance analysis are based on variation around the mean, not absolute coordinate location.

- **Why use eigenvectors?**  
  Eigenvectors of the covariance matrix show the directions of greatest spread in the data. The two largest eigenvalues define the two most important projection directions.

---

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook notebooks/assignment_04_apriori_pca_analysis.ipynb
```

The restaurant sales dataset is not included in this repository. Place it in a local `data/` folder or update the dataset path in the notebook.

Suggested local layout:

```text
assignment-04-apriori-pca-analysis/
├── data/
│   └── assignemnt4.csv
└── notebooks/
    └── assignment_04_apriori_pca_analysis.ipynb
```

---

## Libraries Used

- pandas
- numpy
- plotly
- mlxtend
- openpyxl
- kagglehub

---

## Dataset Notes

- **4A Restaurant Sales Dataset:** used for order-level market basket analysis and revenue simulation.
- **4B Diabetes Dataset:** used for numeric visualization, projection, covariance, and eigen-analysis.

Datasets are not pushed to the repository to keep the repo lightweight and avoid accidental redistribution issues.
