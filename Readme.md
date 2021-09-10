# Credit Line Increase Model Card

### Basic information:

* **Person or organization developing model:** 
	* Arun Rajan, `arunrajan@gwu.edu`,  
	* Claudio Escudero, `claudioescudero@gwu.edu`,
	* Kyle Lyon, `kylelyon@gwu.edu`,
	* Elias Moreno, `emoreno@gwu.edu`
* **Model date:** August 29, 2021
* **Model version:** 1.0
* **License:** MIT
* **Model implementation code:** [DNSC_6301_Final_Project.ipynb](https://github.com/anirmal08/Project/blob/main/DNSC_6301_Final_Project.ipynb)

### Intended Use:
* **Primary intended uses:** This model is an example probability of default classifier, with an example use case 
       for determining eligibility for a credit line increase.
* **Intended users:** Students in GWU DNSC 6301 bootcamp.
* **Out-of-scope uses:** Any use beyond an educational example is out-of-scope.


### Training data:
* **Source of training data:** GWU Blackboard, kylelyon@gwu.edu
* **How training data was divided into training and validation data:**
	* 50% training, 
	* 25% validation, 
	* 25% test
* **Number of rows in training and validation data:**
	* Training rows: 15,000
	* Validation rows: 7,500
	* Test rows: 7,500

 
* **Data dictionary:**

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


### Test Data:
* Source of test data: GWU BlackBoard / 202103_Analytics Edge and Data Ethics_DNSC_6301_10 / Electronic Reserves
* Number of rows in test data: 7500
* State any differences in columns between training  and test data: None



### Model details:
* **Columns used as inputs in the final model:** LIMIT_BAL,PAY_0, PAY_2:PAY_6, BILL_AMT1:BILL_AMT6, PAY_AMT1:PAY_AMT6
* **Column(s) used as target(s) in the final model:** DELINQ_NEXT 
* **Type of model:** Decision Tree
* **Software used to implement the model:** Google Colab
* **Version of the modeling software:** Google Colab with Python 3.6.9
* **Hyperparameters or other settings of your model:** Test Size, Tree Depth, Adverse Impact Ratio - AIR (0.8) and Cut Off - change to 18%

### Quantitative Analysis:
* **Metrics used to evaluate your final model:**
	* AIR
	* Bias remediation
	* Accuracy
	* Variable importance
	* Average Impact Ratio test
	* Model performance
	* Fairness
* **State the final values of the metrics for all data:** Training, validation, and test data 
	* Training AUC: 0.78
	* Validation AUC: 0.75
	* Test AUC: 0.74
	* Asian-to-White AIR: 1.00
	* Black-to-White AIR: 0.85
	* Female-to-Male AIR: 1.02
	* Hispanic-to-White AIR: 0.83
* **Plots:**
	* ![heatmap](https://user-images.githubusercontent.com/90147914/132726809-609f406b-3c63-491a-90a1-d9c2f47d08cf.png)
	* ![iteration_plot](https://user-images.githubusercontent.com/90147914/132726838-7995bff7-a3d8-4e09-9351-51f3c7a701f3.png)
	* ![variable_importance](https://user-images.githubusercontent.com/90147914/132726875-7a3e815e-52e7-46a1-b66d-d708cd3befdf.png)


### Ethical Considerations:
* **Describe potential negative impacts of using your model:**
	* Math or software problems
	* Our model is not prepared to handle missing data. If missing data is presented, it would fail and risk becoming biased. There may also be syntax errors that would damage the code.  
* **Real-world risks: who, what, when or how**
	* There may be a real world risk of favoring a certain race over the other, or gender over the other. This happens due to discrimination and mitigation.
	* Risks include biased decision making with regards to the extension of credit line to     customers. This can happen if the code is manipulated or there is biased data entered into the model. There is a risk also that the original code was developed with unrecognized bias. 
* **Describe potential uncertainties relating to the impacts of using your model:**
	* Math or software problems
	* The software can continue to provide data that is incorrect and if it is not properly recognized and fixed this can go on and be built into the code.
* **Describe any unexpected or results:** 
	* None

