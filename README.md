# Outlier-detection-
This project is developed to automate the process of detecting outliers in agricultural data. The data has been collected from AgMarknet site. It's an enormous dataset spread across 7 years. Each year dataset contains 12 columns and approximately 30 lakh rows. Therefore, the code has been time and space optimised. Code has been written in Jupyter notebook.

# Code 1:

# Code 2:

# Code 3:
The data is grouped according to its Commodity type, State and Market Centre. Within these groups we have created 6 brackets of outliers that vary by a multiple, ‘K’, of the standard deviation.
The groups that have a single data point are not evaluated because the standard deviation is meaningless in these cases.
Methodology (The general formula): 
Mean of Modal Prices - (K * Standard Deviation of Modal Prices) < Modal Price < Mean of Modal Prices + (K * Standard Deviation of Modal Prices). We have processed the data for flags for K= 1, 2, …, 6
The range defined as such represents all data points within K standard deviations. Any data points that lie outside this range are ‘flagged’; where 1 represents an outlier and 0 represents a normal data point.
