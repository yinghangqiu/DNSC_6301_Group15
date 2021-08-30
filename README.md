# DNSC_6301_Group15
# Credit Line Increase Model Card

### Basic Information

* **Group Members**: Jamir Burns(Jamir@gwu.edu), Yinghang Qiu(Yinghang@gwu.edu), Jiujiu Yang(Jiujiu@gwu.edu), Wenyuan Zou(Wenyuan@gwu.edu)
* **Model date**: August 28, 2021
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code:  https://colab.research.google.com/drive/1rCrc4nKAUJvOyZh4KFW-ST5tzWkF5lrE


### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Jamir Burns, Yinghang Qiu, Jiujiu Yang, Wenyuan Zou

* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

### Training Data

* Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

* **Source of training data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500

### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

### Model details
* Columns used as inputs in the final model: 
* Columns used as target(s) in the final model:
* Type of model: Depth=6
* Software used to implement the model :
* Version of the modeling software:
* Hyperparameters or other settings of your model:

### Quantitative analysis
* Metrics used to evaluate your final model: Confusion Matrix; AIR
* State the final values of the metrics for all data:
Confusion matrix by RACE=1
             actual: 1 actual: 0
predicted: 1       447       387
predicted: 0       139       501
(Hispanic)

Confusion matrix by RACE=2
             actual: 1 actual: 0
predicted: 1       449       348
predicted: 0       157       537
(Black)

Confusion matrix by RACE=3
             actual: 1 actual: 0
predicted: 1       176       813
predicted: 0        72      1228
(White)

Confusion matrix by RACE=4
             actual: 1 actual: 0
predicted: 1       186       784
predicted: 0        59      1217
(Asian)

White proportion accepted: 0.568
Hispanic proportion accepted: 0.434
hispanic-to-white AIR: 0.76

White proportion accepted: 0.568
Black proportion accepted: 0.465
black-to-white AIR: 0.82

White proportion accepted: 0.568
Asian proportion accepted: 0.568
asian-to-white AIR: 1.00

Confusion matrix by SEX=1
             actual: 1 actual: 0
predicted: 1       546       905
predicted: 0       179      1292
(Male)

Confusion matrix by SEX=2
             actual: 1 actual: 0
predicted: 1       712      1427
predicted: 0       248      2191
(Female)

Male proportion accepted: 0.503
Female proportion accepted: 0.533
female-to-male AIR: 1.06
![image](https://user-images.githubusercontent.com/89756854/131276170-b156488a-918a-4a2d-8b7e-918fe31e7680.png)

* Provide any plots related to your data or final model: 

Data Histograms

![image](https://user-images.githubusercontent.com/89756854/131276416-23a77ffc-0e5b-4a06-9fdd-30e08aae0bc1.png)

Heat Map

![image](https://user-images.githubusercontent.com/89756854/131276440-49f65a56-dcb5-4f84-a3b6-f77a0264d242.png)

Iteration Plot

![image](https://user-images.githubusercontent.com/89756854/131276462-c4e7afe0-d7c2-401d-ba89-663c0f54467d.png)

### Ethical considerations
* Describe potential negative impacts of using your model: 
  * Math or software problems: In this data set’s variables there’s correlation of DELINQ_NEXT and Race, which is a negative impact



