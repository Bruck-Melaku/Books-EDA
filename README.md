# Book List Exploratory Data Analysis (EDA)
This repository contains an exploratory data analysis (EDA) of a book list dataset using Python.
The goal is to uncover insights about book trends, ratings, genres, and other interesting patterns using data visualization and analysis techniques.

## Objective

The main objectives of this EDA are:

- Understand the distribution of ratings, genres, and publication years
- Identify popular authors and highly rated books
- Visualize trends over time
- Detect correlations and patterns in the dataset

## Tools & Libraries Used

- **Python** (Jupyter Notebook)
- **Pandas** – for data manipulation and cleaning
- **Matplotlib** – for basic data visualization
- **Seaborn** – for advanced statistical visualizations

## Import required libraries
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

## Load the data into python
```python
df = pd.read_csv("Books_Data_Clean.csv")
```

## Show the 1st 5 rows of the data
```python
df.head()
```

## Describing the basic stats of the data
```python
df.describe()
```

## Cleaning the data: Removing any inconsistent publishing year entries
```python
df = df[df["Publishing Year"] > 1900]
```

## The total amount of rows and columns
```python
df.shape
```

## Datatypes for each column
```python
df.dtypes
```

## Show the total amount of duplicates
```python
df.duplicated().sum()
```

## Show the total amount of null values
```python
df.isna().sum()
```

## Removes the null values in column: Book Name
```python
df.dropna(subset = "Book Name", inplace = True)
```

## Make a histograph of Distribution of Publishing Year
```python
plt.hist(df["Publishing Year"])
plt.xlabel("Publishing Year")
plt.ylabel("Frequency")
plt.title("Distribution of Publishing Year")
plt.show()
```

## Make a bar graph of Number of Books in each Genre
```python
df["genre"].value_counts().plot(kind = "bar")
plt.xlabel("Genre")
plt.ylabel("Number of Books")
plt.title("Number of Books in each Genre")
plt.show()
```

## Show the mean Book average rating for each Author
```python
df.groupby("Author")["Book_average_rating"].mean().sort_values(ascending = False)
```

## Make a boxplot of Book Ratings Count for Each Genre
```python
sns.boxplot(x = "genre", y = "Book_ratings_count", data = df)
plt.xlabel("Genre")
plt.ylabel("Book Ratings Count")
plt.title("Box Plot of Book Ratings Count for Each Genre")
plt.show()
```

## Make a Scatter plot of Sale Price vs Units Sold
```python
plt.scatter(df["sale price"], df["units sold"])
plt.xlabel("Sale Price")
plt.ylabel("Units Sold")
plt.title("Scatter plot of Sale Price vs Units Sold")
plt.show()
```

## Make a piechart of Language Distribution of Books
```python
language_counts = df["language_code"].value_counts()
plt.pie(language_counts, labels = language_counts.index, startangle = 90)
plt.title("Language Distribution of Books")
plt.show()
```

## Show the sum of publisher revenue for each publisher
```python
df.groupby("Publisher ")["publisher revenue"].sum().sort_values(ascending = False)
```

## Show the mean book ratings count for each author rating
```python
df.groupby("Author_Rating")["Book_ratings_count"].mean().sort_values(ascending = False)
```

## Show the maximum book ratings count for each author rating
```python
df.groupby("Author_Rating")["Book_ratings_count"].max()
```

## Make a Scatter Plot of Book Average Rating vs Book Ratings Count
```python
plt.scatter(df["Book_average_rating"], df["Book_ratings_count"])
plt.xlabel("Book Average Rating")
plt.ylabel("Book Ratings Count")
plt.title("Scatter Plot of Book Average Rating vs Book Ratings Count")
plt.show()
```

## Make a Bar graph of the Total Gross Sales for each Author
```python
total_gross_sales_by_author = df.groupby("Author")["gross sales"].sum()
total_gross_sales_by_author.sort_values(ascending = False).head(20).plot(kind = "bar")
plt.xlabel("Author")
plt.ylabel("Total Gross Sales")
plt.title("Total Gross Sales for each Author")
plt.show()
```

## Make a boxplot of Box Plot of Units Sold for each Author
```python
sns.boxplot(x = "Author_Rating", y = "units sold", data = df)
plt.xlabel("Author Rating")
plt.ylabel("Units Sold")
plt.title("Box Plot of Units Sold for each Author")
plt.show()
```

## Make a linegrapgh of the Total units sold over the years
```python
df.groupby("Publishing Year")["units sold"].sum().plot(kind = "line")
plt.xlabel("Publishing Year")
plt.ylabel("Total Units Sold")
plt.title("Total units sold over the years")
plt.show()
```
