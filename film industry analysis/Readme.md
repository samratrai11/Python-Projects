Overview:

•	Dataset: https://www.kaggle.com/datasets/danielgrijalvas/movies

•	Tools used: Jupyter Notebook.

•	Language used: Python, Pandas, Seaborn, Matplotlib and Numpy.

•	ML models used: Linear Regression, scatter plot and heatmap.

Code explanation:

First block:

•	import pandas as pd: Imports the Pandas library and aliases it as pd. Pandas is commonly used for data manipulation and analysis.

•	import seaborn as sns: Imports the Seaborn library, which is used for statistical data visualisation.

•	import matplotlib: Imports the Matplotlib library, a widely used plotting library in Python.

•	import matplotlib.pyplot as plt: Imports the pyplot module from Matplotlib and aliases it as plt. This module provides a MATLAB-like interface for creating plots.

•	plt.style.use('ggplot'): Sets the plot style to 'ggplot', which is a popular style inspired by the Grammar of Graphics.

•	from matplotlib.pyplot import figure: Imports the figure function from Matplotlib. This function is used to create a new figure.

•	%matplotlib inline: Enables inline plotting, which means that the plots will be displayed directly below the code cells in a Jupyter Notebook or JupyterLab environment.

•	matplotlib.rcParams['figure.figsize'] = (12, 8) : 

Sets the default figure size for Matplotlib plots to (12, 8) inches. This means that if you create a plot without specifying the figure size, it will use these dimensions.

•	In summary, the code sets up the necessary libraries for data analysis and visualisation (Pandas, Seaborn, and Matplotlib), configures the plot style to 'ggplot', and sets the default figure size for Matplotlib plots. This is a typical setup for data visualisation in Python.

Second block:

•	import numpy as np: Imports the NumPy library and aliases it as np.

•	for col in df.columns:: Iterates through each column in the DataFrame df.

•	np.mean(df[col].isnull()): Calculates the mean of the boolean mask obtained by applying isnull() to the column. This effectively gives the proportion of missing values in the column.

•	print('{} - {}%'.format(col, round(pct_missing * 100))): Prints the column name and the percentage of missing values rounded to the nearest integer.

•	So, for each column in the DataFrame, it prints the column name and the percentage of missing values. This information is useful for assessing the completeness of your dataset and deciding how to handle missing values, such as imputation or removal of rows or columns with missing values.

Third block:

•	The code df.sort_values(by=['gross'], inplace=False, ascending=False) sorts the DataFrame df based on the values in the 'gross' column in descending order. Here's a breakdown of the parameters:
  
  o	by=['gross']: Specifies the column ('gross' in this case) based on which the sorting will be performed.
  
  o	inplace=False: This parameter, when set to False (which is the default), indicates that a new DataFrame will be returned with the rows sorted, and the original DataFrame df remains unchanged. If inplace is set to True, the sorting will be done in place, meaning the original DataFrame will be modified, and None will be returned.
  
  o	ascending=False: This parameter specifies the sorting order. When set to False, it sorts in descending order, which means higher values of 'gross' will come first.

Fourth Block:

•	The code sns.regplot(x="gross", y="budget", data=df) creates a scatter plot with a regression line (linear regression) using the Seaborn library. Here's a breakdown of the parameters:

  o	x="gross": Specifies the column in the DataFrame (df) that will be used for the x-axis values. In this case, it's the 'gross' column.

  o	y="budget": Specifies the column in the DataFrame (df) that will be used for the y-axis values. In this case, it's the 'budget' column.

  o	data=df: Specifies the DataFrame containing the data to be plotted. In this case, it's the DataFrame df.

  o	The sns.regplot function combines a scatter plot and a linear regression line. It's useful for visualizing the relationship between two variables and assessing whether there is a linear correlation between them.

•	Here's a brief explanation of what the plot shows:

  o	Each point on the scatter plot represents a data point with 'gross' on the x-axis and 'budget' on the y-axis.

  o	The regression line is a best-fit line that represents the linear relationship between 'gross' and 'budget' based on the data.

  o	The slope and intercept of the regression line are determined by the data, and the line provides an estimate of the trend or correlation between the two variables.

  o	This type of plot is often used to explore and visualize the correlation between two continuous variables and to understand the overall trend in the data. If the regression line has a positive slope, it suggests a positive correlation, while a negative slope suggests a negative correlation. The scatter points around the line indicate the variability of the data.

Fifth Block:

•	The code df.corr(method='pearson') computes the Pearson correlation coefficients between all pairs of numerical columns in the DataFrame df. 

  o	df: This assumes that df is a Pandas DataFrame.

  o	.corr(): This method computes the pairwise correlation of columns in the DataFrame.
  
  o	method='pearson': Specifies the correlation method to be used, and in this case, it's the Pearson correlation coefficient. The Pearson correlation measures the linear relationship between two variables and ranges from -1 (perfect negative correlation) to 1 (perfect positive correlation), with 0 indicating no linear correlation.
  
  o	The resulting output is a correlation matrix, where each entry represents the Pearson correlation coefficient between the corresponding pair of columns. This matrix provides insights into how strongly and in what direction different numerical variables are correlated in the DataFrame. Positive values indicate a positive correlation, negative values indicate a negative correlation, and values closer to 0 suggest a weaker or no linear correlation.

•	The code df.corr(method='kendall') calculates the Kendall rank correlation coefficients between all pairs of numerical columns in the DataFrame df. 

  o	method='kendall': Specifies the correlation method to be used, and in this case, it's the Kendall rank correlation coefficient. The Kendall correlation measures the strength and direction of the monotonic relationship between two variables. It is particularly suitable for identifying relationships that are not necessarily linear.

•	The code df.corr(method='spearman') calculates the Spearman rank correlation coefficients between all pairs of numerical columns in the DataFrame df. Here's an explanation:

  o	method='spearman': Specifies the correlation method to be used, and in this case, it's the Spearman rank correlation coefficient. The Spearman correlation assesses the strength and direction of the monotonic relationship between two variables, similar to the Kendall correlation. Like Kendall, Spearman is less sensitive to outliers and suitable for detecting non-linear relationships.

Sixth Block:

•	correlation_matrix = df.corr(): This calculates the correlation coefficients between all pairs of numeric columns in the DataFrame df and stores the result in the variable correlation_matrix.

•	sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm'):

  o	This line uses Seaborn to create a heatmap of the correlation matrix. The annot=True parameter adds numeric annotations to the cells, and cmap='coolwarm' sets the colormap to a combination of cool and warm colors.

•	Overall, the code is a visualization tool to help you quickly understand the correlation structure between numeric features in your dataset. The colors in the heatmap represent the strength and direction of correlations, with cooler colors indicating negative correlations, warmer colors indicating positive correlations, and darker shades indicating stronger correlations. The annotations provide the actual numeric values of the correlation coefficients.

Seventh block:

•	df.apply(lambda x: x.factorize()[0]):
  
  o	The apply function is used to apply a function along the axis of the DataFrame.

  o	lambda x: x.factorize()[0] is an anonymous function (lambda function) applied to each column x.

  o	x.factorize()[0] returns an array of the factorized version of the values in each column. The factorization assigns unique integer labels to each unique value in the column.

  o	.corr(method='pearson'):

  o	After the factorization, the code calculates the Pearson correlation matrix for the transformed DataFrame.

  o	method='pearson' specifies the correlation method to be Pearson.

•	In summary, this code is factorizing the values in each column of the DataFrame, essentially replacing each unique value with a corresponding integer label. Then, it calculates the Pearson correlation matrix for the factorized data. This may be useful in situations where you want to examine the correlation structure based on the ordinal relationships between values rather than their original numerical values.

Eight Block:

•	correlation_matrix = df.apply(lambda x: x.factorize()[0]).corr(method='pearson')

sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')

plt.title("Correlation matrix for Movies")

plt.xlabel("Movie features")

plt.ylabel("Movie features")

plt.show(): 

  o	this code helps visualize the correlation structure among movie features by converting categorical values to numeric labels and then creating a heatmap of the resulting correlation matrix. The heatmap provides insights into how strongly and in what direction different movie features are correlated based on their ordinal relationships.

•	correlation_mat = df.apply(lambda x: x.factorize()[0]).corr()
corr_pairs = correlation_mat.unstack()
print(corr_pairs):

  o	df.apply(lambda x: x.factorize()[0]).corr():
	Applies the factorize method to each column (x) in the DataFrame, converting categorical values into unique numeric labels.
	Calculates the correlation matrix for the factorized DataFrame.

  o	corr_pairs = correlation_mat.unstack():
	Transforms the correlation matrix into a Series of correlation pairs using the unstack method. This results in a Series with a MultiIndex where each index corresponds to a pair of column names, and the values are the correlation coefficients.

  o	print(corr_pairs):
	Prints the correlation pairs. The output will display the pairs of column names along with their corresponding correlation coefficients.

  o	In summary, this code is exploring and printing the correlation relationships between pairs of columns after transforming categorical values into numeric labels using the factorize method. The resulting output provides information about how each pair of features is correlated based on their ordinal relationships.

•	sorted_pairs = corr_pairs.sort_values(kind="quicksort")
print(sorted_pairs):

  o	corr_pairs.sort_values(kind="quicksort"):

  o	Uses the sort_values method to sort the correlation pairs in ascending order based on the correlation coefficients.

  o	The kind="quicksort" parameter specifies the sorting algorithm to be used (quicksort in this case).

  o	print(sorted_pairs):

  o	Prints the sorted correlation pairs. The output will display the pairs of column names along with their corresponding correlation coefficients, arranged in ascending order based on the correlation values.

  o	In summary, this code allows you to inspect the correlation pairs between columns, sorted by their correlation coefficients. It provides a way to identify which pairs of columns have the strongest positive or negative correlations based on the ordinal relationships after the factorize transformation

Ninth Block:

•	strong_pairs = sorted_pairs[abs(sorted_pairs) > 0.5]
print(strong_pairs):

  o	abs(sorted_pairs) > 0.5:
	Calculates the absolute values of the correlation coefficients in sorted_pairs.
	Compares each absolute value with 0.5, creating a boolean mask where True represents correlation coefficients with an absolute value greater than 0.5.

  o	sorted_pairs[abs(sorted_pairs) > 0.5]:
	Uses boolean indexing to filter the correlation pairs based on the condition. Only pairs with correlation coefficients greater than 0.5 (or less than -0.5) are included in strong_pairs.

  o	In summary, this code identifies and prints pairs of columns with strong correlations (either positive or negative) based on the specified threshold of 0.5. It helps highlight the relationships between pairs of features that exhibit a significant correlation in the dataset.

•	CompanyGrossSum = df.groupby('company')[["gross"]].sum()
CompanyGrossSumSorted = CompanyGrossSum.sort_values('gross', ascending = False)[:15]
CompanyGrossSumSorted = CompanyGrossSumSorted['gross'].astype('int64') 
CompanyGrossSumSorted:

•	In summary, this code calculates the total 'gross' revenue for each company, sorts the companies based on their total 'gross' revenue in descending order, takes the top 15 companies, and converts their 'gross' values to the int64 data type. The resulting variable CompanyGrossSumSorted likely contains the top 15 companies with their total gross revenue represented as integers.




Tenth Block:

•	df['Year'] = df['released'].astype(str).str[:4]:

  o	df['released'].astype(str):
	Converts the 'released' column to a string data type. This is done to ensure that the subsequent string slicing operation works as expected.

  o	.str[:4]:
	Uses string slicing to extract the first four characters (characters 0 to 3) from each string in the 'released' column.
	This assumes that the date in the 'released' column is formatted as YYYY-MM-DD or a similar format where the year is represented by the first four characters.

  o	In summary, this code creates a new column 'Year' in the DataFrame df based on the first four characters of the 'released' column, effectively extracting the year from the date information in the 'released' column.

•	df.groupby(['company', 'year'])[["gross"]].sum():

  o	df.groupby(['company', 'year']):
	Groups the DataFrame df based on two columns: 'company' and 'year'.
	This means that the data will be organized into groups where each group corresponds to a unique combination of 'company' and 'year'.

  o	[["gross"]]:
	Selects only the 'gross' column from the grouped data. The double square brackets ([["gross"]]) indicate that the result should be a DataFrame with a single column, 'gross'.

  o	.sum():
	Calculates the sum of the 'gross' values within each group.
	This operation is applied independently to each group formed by the unique combinations of 'company' and 'year'.

  o	The result is a new DataFrame that shows the total 'gross' revenue for each combination of 'company' and 'year'. The grouping operation allows you to analyze the aggregated gross revenue for different companies over different years in your dataset.

•	CompanyGrossSum = df.groupby(['company', 'year'])[["gross"]].sum()
CompanyGrossSumSorted = CompanyGrossSum.sort_values(['gross','company','year'], ascending = False)[:15]
CompanyGrossSumSorted = CompanyGrossSumSorted['gross'].astype('int64') 
CompanyGrossSumSorted:

  o	In summary, this code sequence aggregates the total 'gross' revenue for each combination of 'company' and 'year', sorts the results in descending order based on the total 'gross', and then selects the top 15 combinations. Finally, it converts the selected 'gross' values to the int64 data type.

Eleventh Block:

•	for col_name in df_numerized.columns:
    	if(df_numerized[col_name].dtype == 'object'):
        	df_numerized[col_name]= df_numerized[col_name].astype('category')
        	df_numerized[col_name] = df_numerized[col_name].cat.codes:

  o	iterates through each column in the DataFrame.

  o	Checks if the data type of the column is 'object' (typically indicating categorical data).

  o	If the column is categorical, it converts it to the 'category' data type and then applies label encoding using the cat.codes attribute. Label encoding assigns a unique numerical code to each unique category.

  o	this code snippet modifies the DataFrame df by converting its categorical columns into a numerical representation using label encoding. The resulting DataFrame df_numerized contains the same information as df, but with categorical variables represented by numerical codes.


        


