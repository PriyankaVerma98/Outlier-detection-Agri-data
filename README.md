# Methods for Outlier-detection
This project is developed to detect outliers to identify price and quantity shocks in agriculture markets. The data has been collected from [AgMarknet website](https://agmarknet.gov.in/Default.aspx). We used a large dataset spread across 7 years, where each year dataset contains 12 features and approximately 3 million rows. Therefore, the code has been time and space optimised to run under 3min on 4 GB RAM. The scripts were written in Jupyter notebook.

# Code 1:
The data is filtered using loops and lists; we filter using Commodity type and Market Centre. We define a band for normal data points using Coefficient of Variation and the difference between the modal price of each data point from the moving average.
If the difference between the modal price and its corresponding moving average is greater than the coefficient of variation then the data point is marked an outlier.

# Code 2:
Once again, the data is filtered using loops and lists; we filter using Commodity type, Market Centre and the State. For each filtered set we calculate the 7-window centred moving average, the absolute of the difference between the moving average and the modal price, the standard deviation and the mean. We define a range such that: 

Lower Band: Mean - (Standard Deviation) * K

Upper Band: Mean + (Standard Deviation) * K
, Where K = 1, 2 or 3

If the difference lies outside the range where k=1 then flag1 is marked 1 to represent an outlier. Otherwise, flag1 is marked 0 to represent a normal data point. Similarly, we calculate flag2 and flag3.


# Code 3:
The data is grouped according to its Commodity type, State and Market Centre. Within these groups we have created 6 brackets of outliers that vary by a multiple, ‘K’, of the standard deviation.
The groups that have a single data point are not evaluated because the standard deviation is meaningless in these cases.
Methodology (The general formula): 

Mean of Modal Prices - (K * Standard Deviation of Modal Prices) < Modal Price < Mean of Modal Prices + (K * Standard Deviation of Modal Prices). 

We have processed the data for flags for K= 1, 2, …, 6. The range defined as such represents all data points within K standard deviations. Any data points that lie outside this range are ‘flagged’; where 1 represents an outlier and 0 represents a normal data point.

The results of the confusion matrix for all flags along with the calculated accuracy, precision, recall and F1 Score is shown in the image.

![Screenshot 2021-11-06 at 1 56 34 PM](https://user-images.githubusercontent.com/39693183/140603301-5e541196-e084-4f74-b0f1-e704eb22e45d.png)
Note: f1, f2, ...,f6 represent flag1, flag2,..., flag 6
