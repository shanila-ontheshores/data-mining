# CSC 551 Data Mining and Warehousing Coursework

This repository contains four solo programming assignments completed for **CSC 551: Data Mining and Warehousing** as part of my MSc in Computer Science coursework. The assignments cover the full early data-mining workflow: data preparation, exploratory visualization, feature engineering, recommendation systems, clustering, association mining, projection, and PCA-style numeric analysis.

The goal of this repository is to document the hands-on coding work behind the course, not only the final outputs. Each assignment has its own folder with a cleaned notebook, assignment instruction file, generated outputs, and a detailed README explaining what was implemented and where each requirement is handled in the code.

---

## Repository Overview

| Assignment | Topic | Main Methods | Dataset(s) | Folder |
|---|---|---|---|---|
| 01 | Dataset visualization and descriptive analysis | pandas, NumPy, Plotly, histograms, boxplots, scatter matrix, class means, parallel coordinates | Diabetes dataset | [`assignment-01-data-visualization`](assignment-01-data-visualization/) |
| 02 | Movie recommender systems | Content-based filtering, TF-IDF, cosine similarity, user-user CF, item-item CF, RMSE | Netflix ratings, IMDb metadata, CMU movie summaries | [`assignment-02-movie-recommender`](assignment-02-movie-recommender/) |
| 03 | KMeans clustering | Custom KMeans, MNIST clustering, Bangla text clustering, t-SNE, DBI, Dunn index, purity, Rand index | Diabetes, MNIST, Prothom Alo news | [`assignment-03-kmeans-clustering`](assignment-03-kmeans-clustering/) |
| 04 | Apriori and projection analysis | Apriori frequent itemsets, revenue simulation, centering, projection, covariance matrix, eigen decomposition, PCA-style projection | Restaurant sales dataset, Diabetes dataset | [`assignment-04-apriori-pca-analysis`](assignment-04-apriori-pca-analysis/) |

---

## Skills Demonstrated

This coursework repository demonstrates practical data mining work across four different problem types:

- Loading, cleaning, and preparing tabular datasets with pandas and NumPy
- Converting structured data into numerical arrays for analysis
- Building interactive 2D and 3D visualizations with Plotly
- Using class labels for visualization and external validation
- Creating descriptive statistics, histograms, boxplots, scatter matrices, and parallel coordinate plots
- Building a content-based movie recommender from metadata and plot-summary features
- Implementing similarity-based recommendation using cosine similarity
- Implementing user-user and item-item collaborative filtering
- Evaluating recommender predictions with RMSE
- Implementing KMeans clustering logic from scratch
- Clustering tabular data, image data, and text data
- Building TF, normalized TF, IDF, and TF-IDF matrices manually for text clustering
- Using internal and external clustering validation metrics
- Applying Apriori-style frequent itemset mining to transaction data
- Simulating the business effect of a combo-package discount
- Performing centering, line projection, plane projection, covariance analysis, eigen decomposition, and PCA-style projection

---

## Assignment Details

### Assignment 01: Dataset Visualization and Descriptive Analysis

**Folder:** [`assignment-01-data-visualization`](assignment-01-data-visualization/)

This assignment focuses on understanding a dataset before applying data mining algorithms. The notebook loads the Diabetes dataset, selects the required real-valued dimensions, converts the selected data into a NumPy array, and creates multiple interactive visualizations.

**Dataset used:** Diabetes dataset from Kaggle

**Main work completed:**

- Loaded the dataset using pandas
- Removed identifier-style columns where applicable
- Selected the first three real-valued dimensions and the class label
- Converted the cleaned DataFrame into a NumPy array
- Created interactive 2D and 3D scatter plots using Plotly
- Used class-specific marker shapes for visual separation
- Calculated class-wise mean points and overlaid them on scatter plots
- Created histograms, boxplots, class-wise boxplots, and a scatter matrix
- Created circle segment and parallel coordinates plots for seven dimensions

**Skills shown:** exploratory data analysis, interactive visualization, basic statistical summaries, feature inspection, class-aware plotting.

---

### Assignment 02: Movie Recommender Systems

**Folder:** [`assignment-02-movie-recommender`](assignment-02-movie-recommender/)

This assignment implements a movie recommendation pipeline using both content-based filtering and collaborative filtering. The content-based section builds movie feature vectors from metadata and plot summaries. The collaborative filtering section predicts ratings using user-user and item-item similarity.

**Datasets used:**

- Netflix Prize movie rating data
- IMDb non-commercial datasets
- CMU Movie Summary Corpus

**Main work completed:**

- Loaded and cleaned Netflix, IMDb, and CMU movie data
- Merged movie metadata, plot summaries, and rating information
- Built a unified movie dataframe with content features and rating statistics
- Encoded writers, directors, genres, and languages as one-hot vectors
- Converted cast/star information into a fixed-length vector
- Cleaned plot summaries and built a controlled vocabulary
- Calculated TF, IDF, and TF-IDF features for plot summaries
- Concatenated all content features into a full movie feature matrix
- Computed movie-to-movie cosine similarity
- Returned top similar movies for a given input title
- Implemented user-user collaborative filtering
- Implemented item-item collaborative filtering
- Evaluated rating predictions using RMSE

**Key result from the notebook:** item-item collaborative filtering gave the lowest RMSE among the evaluated rating-prediction methods.

**Skills shown:** recommender systems, feature engineering, text vectorization, similarity search, sparse/high-dimensional feature construction, rating prediction, model evaluation.

---

### Assignment 03: KMeans Clustering

**Folder:** [`assignment-03-kmeans-clustering`](assignment-03-kmeans-clustering/)

This assignment applies KMeans clustering to three different data types: tabular data, image data, and Bangla news text. The first part implements KMeans logic directly. The later parts extend clustering to MNIST digit images and Prothom Alo news articles.

**Datasets used:**

- Diabetes dataset for tabular clustering
- MNIST handwritten digit dataset for image clustering
- Prothom Alo news data from Bangla NLP resources for text clustering

**Main work completed:**

- Implemented centroid initialization from randomly selected data points
- Assigned points to clusters using distance from centroids
- Counted cluster memberships and recomputed centroids
- Used objective-function convergence as the stopping criterion
- Visualized tabular clustering in an interactive 3D Plotly plot
- Clustered MNIST images as 784-dimensional vectors
- Reshaped MNIST centroids into 28 × 28 images for visual validation
- Used t-SNE to visualize MNIST clusters in 3D
- Processed Bangla news text using tokenization, normalization, stemming, and stopword removal
- Used Zipf-style filtering to build a controlled vocabulary
- Calculated TF, normalized TF, IDF, and TF-IDF manually for text documents
- Clustered 1,200 Bangla news documents into six groups
- Evaluated clusters with Davies-Bouldin index, approximate Dunn index, purity, and Rand index

**Skills shown:** unsupervised learning, custom algorithm implementation, clustering validation, image-vector representation, text preprocessing, manual TF-IDF construction, dimensionality reduction for visualization.

---

### Assignment 04: Apriori and PCA-Style Projection Analysis

**Folder:** [`assignment-04-apriori-pca-analysis`](assignment-04-apriori-pca-analysis/)

This assignment has two parts. The first part uses restaurant order data to find frequent dish combinations and estimate the effect of a discount strategy. The second part performs numeric data analysis with centering, projection, covariance, eigenvectors, and PCA-style dimensionality reduction.

**Datasets used:**

- Restaurant sales analysis dataset by dish and date
- Diabetes dataset for numeric projection and PCA-style analysis

**Main work completed:**

- Loaded restaurant order-level sales data
- Separated dish quantity columns from price columns
- Converted dish quantities into binary transaction data
- Calculated original total sales as a revenue baseline
- Generated frequent itemsets using Apriori-style logic
- Selected a frequent four-item combo package
- Simulated a 5% discount and 5% sales increase assumption
- Estimated associated-item uplift using conditional probability
- Compared final revenue against the original sales baseline
- Loaded and centered numeric data for projection analysis
- Projected 2D data onto the line `x1 = -x2`
- Projected 3D data onto a plane spanned by two given vectors
- Computed the covariance matrix from centered data
- Calculated eigenvalues and eigenvectors
- Sorted eigenvectors by eigenvalues
- Built a two-vector basis from the dominant eigenvectors
- Projected data using `x' = UUᵀx`
- Converted projected data into new 2D coordinates using `Uᵀx`

**Skills shown:** association rule mining, market-basket analysis, business interpretation, vector projection, linear algebra for data mining, covariance analysis, eigen decomposition, PCA-style dimensionality reduction.

---

## Datasets

Large raw datasets are not included in this repository. The notebooks are structured so that datasets can be placed in local `data/` folders when rerunning the work.

| Dataset | Used In | Notes |
|---|---|---|
| Diabetes dataset | Assignment 01, 03A, 04B | Used for visualization, KMeans clustering, and projection analysis |
| Netflix Prize ratings | Assignment 02 | Used for collaborative filtering and RMSE evaluation |
| IMDb non-commercial datasets | Assignment 02 | Used for movie metadata such as title, year, genre, crew, and cast |
| CMU Movie Summary Corpus | Assignment 02 | Used for plot-summary text features |
| MNIST | Assignment 03B | Used for image clustering and centroid visualization |
| Prothom Alo news dataset | Assignment 03C | Used for Bangla text clustering |
| Restaurant sales dataset | Assignment 04A | Used for Apriori itemset mining and revenue simulation |

---

## Main Libraries

The assignments use the following Python libraries:

- pandas
- NumPy
- scikit-learn
- Plotly
- matplotlib
- seaborn
- TensorFlow / Keras
- nltk or text-processing utilities
- mlxtend-style Apriori logic / custom Apriori logic depending on the section
- Jupyter Notebook

Some assignments also export interactive Plotly figures as `.html` files. GitHub may not render these directly in the browser, so download/open the HTML files locally to inspect the interactive plots.

---

## Repository Structure

```text
data-mining/
├── assignment-01-data-visualization/
│   ├── README.md
│   ├── docs/
│   ├── notebooks/
│   └── outputs/
├── assignment-02-movie-recommender/
│   ├── README.md
│   ├── docs/
│   ├── notebooks/
│   └── outputs/
├── assignment-03-kmeans-clustering/
│   ├── README.md
│   ├── docs/
│   ├── notebooks/
│   └── outputs/
├── assignment-04-apriori-pca-analysis/
│   ├── README.md
│   ├── docs/
│   ├── notebooks/
│   └── outputs/
└── README.md
```

---

## How to Run

Clone the repository:

```bash
git clone https://github.com/shanila-ontheshores/data-mining.git
cd data-mining
```

Install the dependencies for a specific assignment:

```bash
pip install -r assignment-01-data-visualization/requirements.txt
```

Open the notebook for the assignment you want to inspect:

```bash
jupyter notebook assignment-01-data-visualization/notebooks/assignment_01_data_visualization.ipynb
```

For assignments that use large public datasets, download the dataset from the original source and place it in the expected local `data/` folder described in that assignment's README.

---

## Notes

- These assignments were completed individually for academic coursework.
- The repository is organized for review and portfolio presentation.
- Each assignment folder contains its own README with a requirement-by-requirement mapping.
- Raw datasets and large generated files are excluded when appropriate to keep the repository lightweight.
- Interactive outputs are saved separately where available.

---

## Author

**Sabrina Masum Meem**  
MSc in Computer Science  
Independent University, Bangladesh  
Course: CSC 551 Data Mining and Warehousing
