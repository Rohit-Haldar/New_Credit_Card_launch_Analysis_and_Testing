# New Credit Card launch Analysis and Testing
This project aims to identify the target consumer group for a new credit card launch by analyzing key demographic and financial factors, including age group, income level, occupation type, credit limit, and credit score. By leveraging these variables, the goal is to determine the ideal segment of consumers who are most likely to benefit from and adopt the new credit card product.

### Data Source 
https://codebasics.io/courses/math-and-statistics-for-data-science

### Methodology 
The project is divided into Two Phases 

#### Phase 1 : Focuses on data cleaning and analysing to find out the target consumer group 

1. ```Data Import and Initial Setup```:  Utilized the pandas library to load the dataset, which was in CSV format, for further analysis.

2. ```Handling Missing Values in Annual Income```: The dataset contained null values in the annual income column. Since income varies across occupations,  imputed these null values by calculating and replacing them with the median income specific to each occupation category.

3. ```Outlier Detection and Handling```: To manage outliers,  applied the IQR (Interquartile Range) method. Any values falling outside of acceptable thresholds were adjusted, replacing them with occupation-wise medians where necessary to ensure consistency and prevent skewed analysis.

4. ```Credit Score Duplicates```: Upon reviewing the credit score data,  discovered 1004 entries, although there were only 1000 customers. I identified and removed the duplicates to maintain data integrity.

5. ```Credit Limit Imputation```: The credit limit column had missing values. To address this,  created a new column categorizing customers based on their credit score range, and  filled the missing values by assigning appropriate credit limits according to their credit score range.

6. ```Outstanding Debt Anomalies```: There were cases where outstanding debts exceeded the credit limits, which was illogical. I corrected this by capping the outstanding debt values to their respective credit limits.

7. ```Platform Null Values in the Transaction Table```: The platform column had 4941 missing values. I filled these missing entries with "Amazon," as it was the most frequent platform in the transaction data.

8. ```Outliers in Transaction Amount```: I addressed outliers in the transaction amount column by applying the IQR method and replaced extreme values with the median transaction amount, grouped by product category.

#### Findings 
#### Phase 2 : After finalizing the Target Comsumer group , its time to work further on Credit card Launch . Phase 2 was further divided into 4 steps : 

Step 1: ```Campaign Planning```
The first step involved determining the optimal campaign period and setting up a test group for A/B testing. In a meeting with the Product Manager (assumed), it was established that the test must detect a minimum of 0.4 standard deviation difference between the control and test groups. Using the law of statistical power and effect size, the required sample size was determined to be 100 customers out of the pool of ```256``` in age group ```18-25```. This was aligned with the business's budget constraints, making it feasible for a trial run.

Step 2: ```Campaign Execution```
The campaign was then executed for the test group, ensuring that all operational aspects were in line with the established test setup.

Step 3: ```Post-Campaign Data Collection```
After running the campaign, data was collected, revealing a 40% conversion rate within the test group. Based on this conversion rate, the control group size was finalized to 40 consumers (excluding the original 100 customers in the test group). The dataset for analysis was assumed to be provided by the marketing team. 

So now we have 40 customers in both control group and test group.

Step 4: ```Hypothesis Testing and Decision-Making```
The final step involved assessing whether the new credit card performed better than the control using A/B testing. Hypothesis testing was applied to determine the effectiveness of the campaign, providing data-driven insights for business decisions.

1. By comparing the avg transaction between the control group and test group , had a little hope that new credit card was performing better , but soley based on that we cannot make decision. For that we have to do A / B testing .
2. After conducting A / B testing , z score = ```2.748297374569113``` which is greter than the z critical ( caluclated at 5 % significance level )  = ```1.6448536269514722``` . Also calculated p value at 5 % significance level  = ```0.002995282462202502``` which less than 1 . Thus we can reject the Null hypothesis. 
3. So overall , it is concluded that  null hypothesis which  was Old credit card 's avg transaction is more than New credit card is rejected and New credit card has more avg transctions than old credit card .
4. At the end calculated 95 % confidence interval for test group , which states that after launching the New Credit Card the avg transaction will be between 227 and 245 . 
