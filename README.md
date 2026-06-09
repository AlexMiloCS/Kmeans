#  K-Means Clustering Visualization in Java

A custom, from-scratch implementation of the K-Means clustering algorithm in Java. This project generates synthetic 2D spatial data, applies the K-Means algorithm to find optimal cluster centers, and visualizes the results using graphical scatter plots.

---

##  Table of Contents
1. [Features](#-features)
2. [How It Works](#-how-it-works)
3. [Project Structure](#-project-structure)
4. [Getting Started](#-getting-started)

---
## About K-Means Clustering
**K-Means** is a popular unsupervised machine learning algorithm used to group unlabelled data into $K$ distinct, non-overlapping clusters. It works by iteratively assigning data points to the nearest cluster centroid (center point) and then recalculating those centroids based on the new cluster boundaries.

The goal of the algorithm is to minimize the total variance (or error)—meaning it tries to keep the data points within each cluster as close to their centroid as possible. In this project, K-Means is used to discover spatial patterns in 2D geometric data using Euclidean distance!
---
##  Features
* **Synthetic Data Generation:** Generates 1,200 data points clustered within specific geometric rectangles to simulate a real-world dataset.
* **Algorithmic Optimization:** To avoid falling into local minima, the algorithm runs 15 separate times for each $K$ value, automatically selecting the iteration with the lowest total error.
* **Multiple Cluster Testing:** Simultaneously computes and evaluates clusters for $K \in \{3, 6, 9, 12\}$.
* **Visual Output:** Utilizes `JFreeChart` to generate beautiful, color-coded graphical scatter plots of the clustered data and their corresponding centroids.

---

##  How It Works
1. **Initialization:** The algorithm starts by randomly assigning $K$ center points (centroids) within the bounds of the generated dataset.
2. **Assignment:** Every data point (`Entry`) is assigned to the nearest centroid using the **Euclidean distance** formula:
   $$d = \sqrt{(x - x_c)^2 + (y - y_c)^2}$$
3. **Update:** Once all points are assigned, the centroid's position is updated to the mean $(x, y)$ coordinates of all points belonging to that cluster.
4. **Iteration:** Steps 2 and 3 are repeated until the centroids stabilize (up to 1,000 iterations).

---
## Getting Started

### Prerequisites
* **Java Development Kit (JDK):** Version 8 or higher.
* **JFreeChart Library:** Because this project creates graphical plots, you must download the `jfreechart` and `jcommon` `.jar` files and include them in your project's build path/dependencies.

### Installation & Execution
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/K-Means-Clustering.git](https://github.com/yourusername/K-Means-Clustering.git)
   cd K-Means-Clustering
   ```
2. **Compile the code:**
Ensure your classpath includes the JFreeChart libraries, then compile all Java files:
```bash
javac -cp ".:path/to/jfreechart.jar:path/to/jcommon.jar" *.java
```
3. **Run the program:**
Execute the Main class to run the algorithms and generate the plots:
```bash
java -cp ".:path/to/jfreechart.jar:path/to/jcommon.jar" Main
```
Upon running, the program will calculate the optimal clusters and open four separate Swing windows displaying the scatter plots for 3, 6, 9, and 12 clusters. You can check your console output to see the minimized error values for each iteration.
##  Project Structure

```text
├── Cluster.java                # Represents a cluster centroid and handles position updates
├── CreateScatterPlot.java      # Swing GUI class using JFreeChart to plot the clusters
├── Create_SDO.java             # Generates the synthetic 1,200-point 2D dataset
├── Entry.java                  # Represents a single (x,y) data point
├── K_Means.java                # Core clustering algorithm and logic
└── Main.java                   # Entry point, runs the algorithm for K=3,6,9,12
```
