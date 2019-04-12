<h1 align="center">Machine learning</h1>


<img align="right" width="500" src="https://www.kaggle.com/static/images/education/homepage-illustration.png">

> #### Exploratory Data Analysis
> 1. [**Data manipulation (Pandas)**](#data-manipulation-with-pandas)
> 2. [**Visualization (Matplotlib & Seaborn)**](#visualization-with-matplotlib-and-seaborn)
> 3. [**Dimensionality reduction**](#dimensionality-reduction)
>
> #### Preprocessing
> 4. [**Feature engineering**](#3-improve-generalization-and-avoid-overfitting-try-in-that-order)
> 4. [**Feature selection**](#3-improve-generalization-and-avoid-overfitting-try-in-that-order)
> 5. [**Clustering**](#clustering)
>
> #### Models
> 3. [**Decision trees**](#2-choose-training-hyperparams)
> 3. [**Random forest**](#2-choose-training-hyperparams)
> 3. [**Gradient boosting**](#2-choose-training-hyperparams)
> 3. [**Support vector machine**](#2-choose-training-hyperparams)
> 3. [**Time series**](#2-choose-training-hyperparams)
>
> #### Validation and metrics
>
> #### Resources

TODO: [Gaussian mixture models](https://scikit-learn.org/stable/modules/mixture.html)


# Data manipulation with [Pandas](https://pandas.pydata.org)
> - [**Kaggle learn Pandas**](https://www.kaggle.com/learn/pandas)

- Import pandas library `import pandas as pd`
- Read a CSV file into a pandas dataframe `df = pd.read_csv("file.csv")`
- Get dataframe info:
  - Show firt/last rows `df.head()` `df.tail()`
  - Get shape: `df.shape`. Get columns: `df.columns.tolist()`.
  - Print some info (like missings and types): `df.info()`
  - Has missings? `df.isnull().any().any()`
  - Describe numerical atributes `df.describe()`
  - Describe categorical atributes `df.describe(include=['object', 'bool'])`
- Do some data exploration
  - Get some column (return a series) `df["column"]`
  - Get some columns (return a df) `df[["column1", "column1"]]`
  - Apply function to column `.mean()` `.std()` `.median()` `.max()` `.min()` `.count()`
  - Count unique values `.value_counts()`
- Filter dataframe rows
  - One condition `df[df["column"]==1]`
  - Multiple conditions `df[(df["column1"]==1) & (df["column2"]=='No')]`
- Save it in a CSV [`df.to_csv("sub.csv", index=False)`](http://pandas.pydata.org/pandas-docs/stable/user_guide/io.html#io-store-in-csv)

# Visualization with [Matplotlib](https://matplotlib.org/) and [Seaborn](https://seaborn.pydata.org/)
> - [**Kaggle learn visualization**](https://www.kaggle.com/learn/data-visualization)
> - [**Python graph gallery**](https://python-graph-gallery.com)

### Numerical data distribution
<table>
<tr>
    <td><a href="https://python-graph-gallery.com/histogram">
        <img src="https://python-graph-gallery.com/wp-content/uploads/HistogramBig-150x150.png" width="100px"/></td>
    <td><a href="https://python-graph-gallery.com/density-plot">
        <img src="https://python-graph-gallery.com/wp-content/uploads/DensityBig-150x150.png"   width="100px"/></td>
    <td><a href="https://python-graph-gallery.com/boxplot">
        <img src="https://python-graph-gallery.com/wp-content/uploads/Box1Big-150x150.png"      width="100px"/></td>
    <td><a href="https://python-graph-gallery.com/violin-plot">
        <img src="https://python-graph-gallery.com/wp-content/uploads/ViolinBig-150x150.png"    width="100px"/></td>
</tr>
<tr>
    <td>Histogram</td>
    <td>Density plot</td>
    <td>Box plot</td>
    <td>Violin plot</td>
</tr>
<tr>
    <td>df.plot.hist()<br>sns.distplot()</td>
    <td>df.plot.kde()<br>sns.kdeplot()</td>
    <td>df.plot.box()<br>sns.boxplot()</td>
    <td>sns.violinplot()</td>
</tr>
</table>

### Comparing numerical features
<table>
<tr>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/ScatterPlotBig-150x150.png"      width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/ScatterConnectedBig-150x150.png" width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/BubblePlotBig-150x150.png"       width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/HeatmapBig-150x150.png"          width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/2dDensityBig-150x150.png"        width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/CorrelogramBig-150x150.png"      width="100px"/></td>
</tr>
<tr>
<td>Scatter plot</td>
<td>Line plot</td>
<td>Bubble plot</td>
<td>Heatmap</td>
<td>Density plot 2D</td>
<td>Correlogram</td>
</tr>
<tr>
<td>df.plot.scatter()<br>plt.scatter()<br>sns.scatterplot()</td>
<td></td>
<td></td>
<td>plt.imshow(np)<br>sns.heatmap(df)
</td>
<td>df.plot.hexbin()</td>
<td>scatter_matrix(df)<br>sns.pairplot()</td>
</tr>
</table>


### Ranking
<table>
<tr>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/BarBig-150x150.png"      width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/LollipopBig-150x150.png" width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/Parallel1Big-150x150.png"       width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/SpiderBig-150x150.png"          width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/WordcloudBig-150x150.png"        width="100px"/></td>
</tr>
<tr>
<td>Bar plot</td>
<td>Lollipop plot</td>
<td>Parallel coords.</td>
<td>Radar chart</td>
<td>Word cloud</td>
</tr>
<tr>
<td>plt.scatter()<br>sns.scatterplot()</td>
<td></td>
<td>parallel_coordinates(df, 'cls')</td>
<td></td>
<td></td>
</tr>
</table>

### Part of a whole

<table>
<tr>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/StackedBig-150x150.png"      width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/PieBig-150x150.png" width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/DoughnutBig-150x150.png"       width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/DendrogramBig-150x150.png"          width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/TreeBig-150x150.png"        width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/VennBig-150x150.png"      width="100px"/></td>
</tr>
<tr>
<td>Stacked bar plot</td>
<td>Pie chart</td>
<td>Donut chart</td>
<td>Dendrogram</td>
<td>Treemap</td>
<td>Venn diagram</td>
</tr>
</table>


### Evolution

<table>
<tr>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/LineBig-150x150.png"      width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/AreaBig-150x150.png" width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/StackedAreaBig-150x150.png"       width="100px"/></td>
<td><img src="https://python-graph-gallery.com/wp-content/uploads/StreamBig-150x150.png"          width="100px"/></td>
</tr>
<tr>
<td>Line chart</td>
<td>Area chart</td>
<td>Stacked area chart</td>
<td>Stream graph</td>
</tr>
</table>


# Dimensionality reduction

> - Read [Curse of dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality)
> - [Manifold learning](https://scikit-learn.org/stable/modules/manifold.html)
> - [Matrix factorization](https://scikit-learn.org/stable/modules/decomposition.html)

Method    | Name                                 | Based in  | Code
:--------:|--------------------------------------|-----------|-----
**PCA**   | Principal Component Analysis         | Linear    |
**t-SNE** | t Stochastic Neighbor Embedding      | Neighbors |
**AE**    | Autoencoder (2 or 3 at hidden layer) | Neural    |
**VAE**   | Variational Autoencoder              | Neural    |
**LSA**   | Latent Semantic Analysis             |           |
**SVD**   | Singular Value decomposition         | Linear?   |
**LDA**   | Linear Discriminant Analysis         | Linear    |

- Projection based
  - ISOMAP
  - UMAP
- Sparse coding

### PCA

```python
from sklearn.decomposition import PCA

pca = PCA(n_components=2)
pca.fit(X)
```


### T-SNE

Read [How to use t-SNE effectively](https://distill.pub/2016/misread-tsne)

```python
from sklearn.manifold import TSNE

tsne   = TSNE(random_state=0)
x_tsne = tsne.fit_transform(x)

# And plot it:
plt.scatter(x_tsne[:, 0], x_tsne[:, 1]);
```

# Preprocessing
- **Feature extraction**
  - Color features
  - Texture features
- [**Feature selection**](https://scikit-learn.org/stable/modules/feature_selection.html): Reduce number of attributes.
  - Wrapper: Su usa un classificador
    - MultiObjectiveEvolutionarySearch: Mejor para muchas generaciones. 10000 Evals
    - PSO: Particule Search optimization: Mejor para pocas generaciones.
    - RFE: Recursive feature elimination
  - Filters:
    - InfoGAIN: Cantidad de informacion
    - Correlation Featue Selection


# Clustering
Separate data in groups, useful for labeling a dataset.
- Knowing K
  - **K-Means**
  - **Mean-Shift**
- Without knowing K
  - **DBSCAN**: Density-Based Spatial Clustering of Applications with Noise. 




# Simple models
Good for starting point (baseline), meta-features (input to other models), stacking (final output).
- **Logistic regression**: For classification
- **Linear regression**: For regrssion
- Instance and distances based:
  - **K nearest neighbors (KNN)**: Used in recommendation systems. k = 5, 10 or sqrt(Num samples).
  - **Weighted KNN**: Closer samples are more imortant. Better than KNN.
  - **Fuzzy KNN**: Sample pionts class labels are multiclass vetor (distance to class centroids).
  - **Parzen**: Define a window size (with gaussian shape for ex.) and select those samples. (k would be variable).
  - Utilidad: Conjunto multieditado y condensado: Para reducir el dataset y limparlo.
  - Utilidad 2 : Para pedecir atributos missing
- **Decision tree**: J48, C4.5 No need to normalize data.
- **Support Vector Machines (SVM)**
  - with liear kernel
  - with RBF kernel: Very good one
- **Naive bayes**
- **Rule based**: PART, JRip, FURIA (fuzzy)


# Ensamble models
Stronger models.
- **Random forest**: Rows & atribs bagging + Decision tress [classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html), [regressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html)
  - Deeper trees
- **Extra trees**: [classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.ExtraTreesClassifier.html), [regressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.ExtraTreesRegressor.html)
- **Adaboost**
- **Gradient boosting**: Works great with heterogeneous data and small datasets (unlike neural nets). [link1](http://explained.ai/gradient-boosting/index.html), [link2](https://medium.com/mlreview/gradient-boosting-from-scratch-1e317ae4587d), [link3](http://blog.kaggle.com/2017/01/23/a-kaggle-master-explains-gradient-boosting/)
  - Tree depth from 3 to 6
  - [**XGBoost**](https://github.com/dmlc/xgboost), [**LightGBM**](https://github.com/Microsoft/LightGBM), [**CatBoost**](https://github.com/catboost/catboost) 💪 **Scikit-learn**: [classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html), [regressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingRegressor.html)

# Gradient boosting
- Works great with heterogeneous data and small datasets (unlike neural nets). [link1](http://explained.ai/gradient-boosting/index.html), [link2](https://medium.com/mlreview/gradient-boosting-from-scratch-1e317ae4587d), [link3](http://blog.kaggle.com/2017/01/23/a-kaggle-master-explains-gradient-boosting/)
- Tree depth from 3 to 6
- [**XGBoost**](https://github.com/dmlc/xgboost), [**LightGBM**](https://github.com/Microsoft/LightGBM), [**CatBoost**](https://github.com/catboost/catboost) 💪 **Scikit-learn**: [classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html), [regressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingRegressor.html)


# Time series analysis
- Time series: Sequence of values of some feature (obtained in constant time periods).
- Goal: Get the forecast (predict future values).

# Others
- Self Organizing Map
- [Autoencoder](/teoría/modelos/autoencoder.md): Para comprimir información
- Restricted boltzmann machine: Como el autoencoder pero va y vuelve
- Competitive learning
- Hebbian learning
- Evolutionary algorithms
  - Check [Platypus](https://platypus.readthedocs.io/en/latest/index.html)

---

# Resources
- [ML overview](https://vas3k.com/blog/machine_learning/)
