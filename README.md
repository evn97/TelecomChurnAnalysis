# TelecomChurnAnalysis
**About this Dataset:**
This data source (Telco Customer Churn) provides information about a companies customers and their churn (cancelation of service). It includes various potentially identifying factors (such as age, gender, etc...) and use produt & service use data (call frequency, minutes, payment method, etc...).

The dataset includes 7043 examples and 21 factors, which applied machine learning and data analysis can be used to create a prediction of churn. This is not only beneficial to understanding factors that might increase a customers potential churn risk, but also to develop methods to prevent churn. This concept is applicable to a wide variety of industry as it could result in increased customer retention, increased revenue for a company and potentially customer satisfaction metrics. 

The dataset is available at: https://www.kaggle.com/datasets/blastchar/telco-customer-churn

**Executive Summary**:
Identifying a customers risk of churn is paramount for any business since it enables proactive measures to retain clients and profit. Churn, the rate at which customers discontinue their association with with a company, poses a substantial threat to revenue and market stability. By developing extensive and unique analytical tools accompanied with customer relationship management processes a business can identify early signs of dissatisfaction and deploy apt intervention. Reichheld and Schefter (2000) identified this process whereby customer retention heavily influences long-term profitability and emphasized the financial impact of preventing churn. Moreover, the cost for acquisitioning new customers exceeds that of retaining existing ones (Blattberg et al, 2001). Keeping with the theme of Telecommunication, often customer fees such as: equipment, postage & packaging, line installation or "takeover" fees and administrative charges are generated when acquiring a new customer. Not to mention product incentives that can include gifts, vouchers for the customer at the cost of the business. It is already clear that understanding churn  contributes to financial stability, but by employing unique approaches to customers at risk of churn a business fosters a sense of brand loyalty and allows for them to fortify their market position and remain competitive within the market space.

**Data Overview**:

**Dataset Features**
* **customerID**: A unique ID that represents an inidividual customer.
* **gender**: If the customer is either male or female (option limited)
* **Senior Citizen**: If the customer is a elderly or not (1,0)
* **Partner**: If the customer has a marital or an established relationship (Yes, No)
* **Dependents**: If the customer has any dependents or not (Yes, No)
* **tenure**: The number of months that they have been a customer
* **Phone service**: If the customer has an active Phone Service (Yes, No)
* **Multiple Lines**: If the customer has multiple Phone Services (Yes, No, No Phone Service)
* **Internet Service**: If the customer has a provided Internet Service (DSL, Fibre optic, No)
* **Online Security**: If the customer has any online security Service (Yes, No, No internet service)
* **Device Protection**: If the customer has device protection or not (Yes, No, No internet service)
* **Tech Support**: If the customer has tech support or not (Yes, No, No internet service)
* **StreamingTV**: If the customer has streamed tv service (Yes, No, No internet service)
* **Streaming**: If the customer streams any movies or not (Yes, No, No internet service)
* **Contract**: Type of contract comitment the customer has with the company (Month-to-month, One year, Two year)
* **Paperless Billing**: If the customer has a elected for physical bills (Yes, No)
* **Payment Method**: How the customers payents are made (Electronic check, Mailed check, Bank transfer (automatic), Credit Card (automatic))
* **Monthly Charges**: The recurring charges for the customer each month
* **Churn Label**: If the customer churned or not (Yes or No)

**Data Processing**
WA_Fn-UseC_-Telco-Customer-Churn.csv was imported into a commonly available database system, google docs.
![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/39cb6c60-82a0-431f-9283-b4ba9234dbd7)

The above .csv was then formatted into a brief table to spot for incosnsitencies and to explore the scope of the dataset.
![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/7292dcb3-cdad-4918-ae2e-de78b1f447cb)

As the dataset contained 7043 rows of data, each collumn had to be searched for "null value" or blanks as to understand whether errors could occur when performing trend analysis.

![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/6b13a0bb-3245-4fe3-af90-8194acccb9d3)

During this process, 11 rows were found to be incomplete data sets as "Total Charges" did not return values for customers whos tenure was <1. This is due to Total Charge being = to monthly charge **x** tenure. These results were then ommited from the set as Churn always resulted in No as they were considered "new customers", as the focus of this work is focused on exploring the relationship churn with existing or loyal customers (tenure ≥ 1). Leading to the total remaining examples being 7032. 
![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/38999458-66ee-481b-9ee4-20f5b65c3098)

The results were then aggrigated into understand the range of customer tenure using whatifs formulas as max value for tenure is 72 months, then plotted as a graph to understand how proportunate tenure was.
![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/42de3a21-0fa1-4dcb-b161-178b1a941d8b)
![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/32f8c96d-fd9a-47d2-9a8c-0cc105790f19)

Then to understand the average tenure of a customer who had churned vs a non-churned customer the following formulas were implemented:
=AVERAGEIF('WA_Fn-UseC_-Telco-Customer-Churn'!U2:U7033,"=Yes",'WA_Fn-UseC_-Telco-Customer-Churn'!F2:F7033)
=AVERAGEIF('WA_Fn-UseC_-Telco-Customer-Churn'!U2:U7033,"=No",'WA_Fn-UseC_-Telco-Customer-Churn'!F2:F7033)
This resulted in an average of 17.97 tenure for a churned customer vs an average of 37.65 for non-churned customer.

Then to understand the average customer charges vs churn label the previous approach was implemented and adapted using the following formula:
=AVERAGEIF('WA_Fn-UseC_-Telco-Customer-Churn'!U2:U7033,"=Yes",'WA_Fn-UseC_-Telco-Customer-Churn'!S2:S7033)
=AVERAGEIF('WA_Fn-UseC_-Telco-Customer-Churn'!U2:U7033,"=No",'WA_Fn-UseC_-Telco-Customer-Churn'!S2:S7033)
This resulted in an average of 74.44 monthly charge for a churned customer vs an average of 61.27 for a non-churned customer.

Then to understand the average total charges vs churn label: 
=AVERAGEIF('WA_Fn-UseC_-Telco-Customer-Churn'!U2:U7033,"=Yes",'WA_Fn-UseC_-Telco-Customer-Churn'!T2:T7033)
=AVERAGEIF('WA_Fn-UseC_-Telco-Customer-Churn'!U2:U7033,"=No",'WA_Fn-UseC_-Telco-Customer-Churn'!T2:T7033)
This resulted in an average of 1531.80 Total charge for a churned customer vs an average of 2555.34 for a non-churned customer.

**Results Interpretation**

From the above analysis the following conclusions can be drawn from the dataset:

1. **Tenure**:
   The dataset indicated that customers who have been with the company longer are less likely to churn, as shown by the lower average tenure for churned customers.
2. **Monthly Charges**
   The dataset indicates that customers who have a higher monthly charge are more likely to churn.
3. **Total Charges**
   The data indicates that customers who've accumulated a higher total charge are less likely to churn.

Now that the above interpretations have been drawn it is important to understand whether any factors in the data set such as: gender, dependents, phone service etc... could influence churn. Therefore a catagorical analysis was performed with the results show below:

**Gender**
Male: 2549 Churn = No, 939 Churn = Yes
Female: 2625 Churn = No, 930 Churn = Yes

**Senior Citizen**
No: 4508 Churn = No, 1393 Churn = Yes
Yes: 666 Churn = No, 476 Churn = Yes

**Partner**
No: 2441 Churn = No, 1200 Churn = Yes
Yes: 2733 Churn = No, 669 Churn = Yes

**Dependents**
No: 3653 Churn = No, 1763 Churn = Yes
Yes: 1521 Churn = No, 106 Churn = Yes

**Phone Service**
No: 4662 Churn = No, 1699 Churn = Yes
Yes: 512 Churn = No, 170 Churn = Yes

**Multiple Lines**
No: 2541 Churn = No, 849 Churn = Yes
Yes: 512 Churn = No, 170 Churn = Yes
No Phone Service: 2121 Churn = No, 850 churn = Yes

**Internet Service**
DSL: 1962 Churn = No, 459 Churn = Yes
Fiber Optic: 1799 Churn = No, 1297 Churn = Yes
No: 1413 Churn = No, 113 Churn = Yes

**Online Security**
Yes: 2037 Churn = No, 1461 Churn = Yes
No: 1413 Churn = NO, 113 Churn = Yes
No internet Service: 1724 Churn = No, 295 Churn = Yes

**Online Backup**
Yes: 1855 Churn = No, 1233 Churn = Yes
No: 1413 Churn = NO, 113 Churn = Yes
No Internet Service: 1906 Churn = No, 523 Churn = Yes

**Device Protection**
Yes: 1413 Churn = No, 113 Churn = Yes
No: 1884 Churn = No, 1211 Churn = Yes
No Internet Service: 1877 Churn = No, 545 Churn = Yes

**Tech Support**
Yes: 1413 Churn = No, 113 Churn = Yes
No: 2027 Churn = No, 1446 Churn = Yes
No Internet Service: 1734 Churn = No, 310 Churn = Yes

**Streaming TV**
Yes: 1413 Churn = No, 113 Churn = Yes
No: 1868 Churn = No, 942 Churn = Yes
No Internet Service: 1893 Churn = NO, 814 Churn = Yes

**Streaming Movies**
Yes: 1413 Churn = No, 113 Churn = Yes
No: 1847 Chrun = No, 938 Churn = Yes
No Internet Service: 1914 Churn = no, 818 Churn = Yes

**Contract**
Month-to-month: 2220 Churn = No, 1655 Churn = Yes
Two Year: 1307 Churn = No, 166 Churn = No
One Year: 1647 Churn = No, 48 Churn = Yes

**Payment Method**:
Mailed Check: 1286 Churn = No, 258 Churn = Yes
Electronic Check: 1290 Churn = No, 232 Churn = Yes
Bank Transfer (automatic): 1294 Churn = No, 1071 Churn = Yes
Credit card (automatic): 1304 Churn = No, 308 Churn = Yes

The above data was tracked as to identify any patterns that could influence churn and enable for targetted stratergies amongst data retention.

To understand the initial "churn rate" I totalled and converted the sums into a % using the formula below:
![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/0ad76681-d154-494d-9068-188125bfba27)

No = 73.46%, Yes = 26.54% therefore churn "rate" is measured at 26.54%

Afterwards, I wanted to test 3 promising hypothesis': 

1. Phone Service Impact Churn:
   Null: there is no significant relationship between phone service and churn
   Alternative: there is a significatn relationship between phone service and churn.
   
3. Contract Type Imapct Churn:
   Null: there is no significant relationship between contract type and churn
   Alternative: there is a significatn relationship between contract type and churn.
   
5. Seniority affects churn:
   Null: there is no significant relationship between contract type and churn
   Alternative: there is a significatn relationship between contract type and churn.

To test the above I implemented a Chi Square Test: χ2=∑ni=1(Oi−Ei)2Ei, Results below:
![image](https://github.com/evn97/TelecomChurnAnalysis/assets/144129868/374c8f72-0fa9-4358-8176-1a9408ffe8dd)

**Interpretation**:
Hypothesis 1 (Phone Service Impacts Churn) as the p-value is 0.34 which is greater than the significance level of 0 we fail to reject the null hypothesis. This suggests that there is no significance in Phone Service Impacting Churn.
Hypothesis 2 (Contract Type Impacts Churn) as the p-value is 0 which is less than the significance level of 0 the null hypothesis fails indicating a relationship between Contract Type and Churn risk in this dataset.
Hypothesis 3 (Seniority Impacts Churn) as the p-value is 0 which is less than the significance level of 0 the null hypothesis fails indicating a relationship between Seniority and Churn risk in this dataset.

**Suggestions for a next step?**:
Increased customer diversity to allow for additional segmentation using defining characteristics such as: race and religion
Machine Learning Model: By implementing logistic regression we can help to build predictive models for churn and therefore better help businesses prevent it.

**Data Quality**
Overall the source quality for the data seems very high, with a comprehensive set of variables and attributes for analysing churn. It includes key information such as demographic and services making it appropriate for a wide range of analytical tasks. However, a more thorough cleaning process must be undertaken prior to further analysis.

**Conclusion**:
In conclusion, while identifying and mitigating churn risks is paramount for businesses, the ever-evolving landscape calls for continuous improvement and innovation. To deepen our understanding and refine our strategies, there is a compelling need for further analysis of churn dynamics. Verbeke et al (2013) has demonstrated the effectiveness of machine based learning in churn prediction models in ehancing the precision of risk identfiication. Furthermore, multidimensional approaches such as this allow for businesses to navigate the complexities of churn and adapt better for the future.


**Bibliography**:
Reicheld, F. and Schefter, P. (2000) E-loyalty: Your secret weapon on the web, Harvard Business Review. Available at: https://hbr.org/2000/07/e-loyalty-your-secret-weapon-on-the-web (Accessed: 10 January 2024). 

Blattberg, R.C., Getz, G. and Thomas, J.S. (2001) Customer equity: Building and managing relationships as valuable assets. Boston, Mass: Harvard Business School Press. 

Verbeke, W. et al. (2013) Credence Quality Coordination and Consumers’ willingness-to-pay for ... Available at: https://www.researchgate.net/publication/236923110_Credence_quality_coordination_and_consumers’_willingness-to-pay_for_certified_halal_labelled_meat (Accessed: 10 January 2024). 
