# churn_chi_squared
Feature relationship of churn data with chi squared test.

A.  Describe a real-world organizational situation or issue in the Data Dictionary you chose, by doing the following:
1.  Provide one question that is relevant to your chosen data set. You will answer this question later in the task through an analysis of the cleaned data, using one of the following techniques: chi-square, t-test, or analysis of variance (ANOVA).
Does a customers opinion on service reliability affect the churn rate of a customer?
2.  Explain how stakeholders in the organization could benefit from an analysis of the data.
It is important to understand the relationship of service reliability to your churn rate. This allows for better decisions on what customers find valuable. It also allows business to get a better understanding of the value proposition of their product. 
3.  Identify all of the data in your data set that are relevant to answering your question in part A1.
There are 2 columns in our dataset that are needed to answer this question. We will need the Item4 and Churn columns. This will allow us to associate the reliability survey response of each customer to whether or not that customer canceled service in the last month. 
 
B.  Describe the data analysis by doing the following:
1.  Using one of the following techniques, write code (in either Python or R) to run the analysis of the data set:
	
# Import data set
df = pd.read_csv(r"C:\Users\woote\Desktop\WGU MSDA\[03] D207\churn_clean.csv")
pd.set_option('display.max_columns', None)
df.head()

# Preparing Contingency Table to run Chi-Squared Test
chiDf = pd.crosstab(df.Churn, df.Item4)
chiDf.head()

# Running Chi-Squared Test
chi2, p_value, dof, expected = chi2_contingency(chiDf)

# Interpreting Results
alpha = .05
if p_value < alpha:
    print(f"There is significant association between the variables: P Value = {p_value}")
    print("========================")
    print(f"Chi-Squared Statistic: {chi2}")
    print("========================")
    print(f"Degrees of Freedom: {dof}")
    print("========================")
    print(f"Expected Frequencies: {expected}")
else:
    print(f"There is no significant association between the variables: P Value = {p_value}")
    print("========================")
    print(f"Chi-Squared Statistic: {chi2}")
    print("========================")
    print(f"Degrees of Freedom: {dof}")
    print("========================")
    print(f"Expected Frequencies: {expected}") 

