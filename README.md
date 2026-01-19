# 🐧 Clustering Palmer Penguins Species: Hierarchical Approach

## 📌 Project Overview
This project implements an **Agglomerative Hierarchical Clustering** pipeline to identify natural groupings among Palmer Penguins based on physical attributes. **Unlike K-Means**, this approach builds a hierarchy of clusters, allowing for a detailed analysis of data relationships using **Dendrograms**.

The workflow focuses on discovering the optimal number of clusters through statistical variance reduction (**Ward's Method**) and visualizes the final segments using interactive 3D/2D plots.

## 📂 Dataset
The dataset used is the **Palmer Archipelago (Antarctica) penguin data**.
* **Source:** [Kaggle - Clustering Penguins Species](https://www.kaggle.com/datasets/youssefaboelwafa/clustering-penguins-species)
* **Key Features:**
    * `culmen_length_mm`, `culmen_depth_mm`: Bill dimensions.
    * `flipper_length_mm`: Wing length.
    * `body_mass_g`: Weight.
    * `sex`: Categorical gender feature.

## 🛠️ Technologies & Tools
* **Language:** Python
* **Data Processing:** Pandas, NumPy 
* **Clustering & Stats:** Scikit-Learn (AgglomerativeClustering), SciPy (Hierarchy/Dendrogram)
* **Preprocessing:** StandardScaler, LabelEncoding
* **Visualization:** Plotly Express (Interactive), Matplotlib (Dendrograms)

## ⚙️ Methodology

### 1. Data Preprocessing
* **Cleaning:** Handled missing values (nulls) to maintain statistical integrity.
* **Encoding:** Converted categorical data (`sex`) into numerical format suitable for distance calculation.
* **Feature Scaling:** Applied **StandardScaler** to normalize all features ($z = (x - \mu) / s$).
    * *Critical Step:* Hierarchical clustering is distance-based (Euclidean). Scaling ensures that features with large ranges (like `body_mass_g`) do not overpower smaller features (like `culmen_depth_mm`) during the linkage process.

### 2. The Dendrogram (Determining Clusters)
* Utilized **SciPy** to generate a Dendrogram tree.
* Applied **Ward’s Linkage Method** to minimize the variance within clusters.
* **Analysis:** By cutting the Dendrogram at the point of the longest vertical distance without crossing horizontal lines, the optimal number of clusters was determined to be **6** (reflecting the combination of Species and Gender).

### 3. Model Implementation
* **Algorithm:** `AgglomerativeClustering`
* **Parameters:**
    * `n_clusters=2`
    * `affinity='euclidean'`
    * `linkage='ward'`
* The model iteratively merged data points based on proximity until the target cluster count was reached.

## 📊 Results & Visualization
The project successfully segmented the penguins into distinct groups.
* **Interactive Plots:** Used Plotly to create scatter plots mapping `culmen_length` vs `flipper_length` (and other dimensions), colored by the predicted cluster.
* The hierarchical structure revealed clear boundaries between species, with further sub-groupings likely attributed to gender dimorphism.

## 👨‍💻 Author
**[Samir Mohamed]** *AI Engineer & Data Scientist*
