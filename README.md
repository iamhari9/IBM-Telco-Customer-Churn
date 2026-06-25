# 📱 IBM Telco Customer Churn Analysis

<img width="800" height="348" alt="0_6hXwLKd67L__lTsg" src="https://github.com/user-attachments/assets/b5bd6ec8-763e-4c11-ac5f-fe7ef1bf1ab9" />

**Author:** Đỗ Thanh Hải  
**Tools Used:** Python

## 📑 Table of Contents
[📌 1. Project Overview](#1-project-overview)  
[❓ 2. Business Understanding](#2-business-understanding)  
[📂 3. Dataset Overview](#3-dataset-overview)  
[🧹 4. Data Preparation](#4-data-preparation)  
[🔍 5. Exploratory Data Analysis](#5-exploratory-data-analysis)  
[💡 6. Key Findings & Business Recommendations](#6-key-findings--business-recommendations)  

## 📌1. Project Overview
Customer churn is one of the most critical challenges in the telecommunications industry. Losing existing customers not only reduces revenue but also increases customer acquisition costs.  
This project analyzes customer churn behavior using the IBM Telco Customer Churn dataset to identify key churn drivers and provide actionable business recommendations for improving customer retention.

## ❓2. Business Understanding
### Business Problem
Customer churn is a major challenge for telecommunication companies. Acquiring new customers is often more expensive than retaining existing ones, making customer retention a critical factor for long-term business growth and profitability.

The company wants to understand:  
✔️ Which customer groups are most likely to churn?  
✔️ What factors contribute to customer churn?  
✔️ Why customers leave the service?  
✔️ How customer retention can be improved?  

### Project Objectives
The objectives of this project are:  
✔️ Analyze customer characteristics associated with churn.  
✔️ Identify the most influential factors affecting customer retention.  
✔️ Explore customer churn reasons and categories.  
✔️ Discover high-risk customer groups with elevated churn rates.  
✔️ Provide actionable recommendations to improve customer retention and reduce churn.  

## 📂3. Dataset Overview
### Dataset Information
* Dataset: IBM Telco Customer Churn
* Total Records: 7,043 customers
* Format: .xlsx

## 🧹4. Data Preparation
### Data Cleaning
* Checked for missing values
* Converted data types
* Handled missing values in Total Charges

### Feature Engineering
Created:
* Tenure Group
* Charge Group
* Churn Reason Category

## 🔍5. Exploratory Data Analysis
### 1. Overview Analysis
🔢**Calculate Metrics**
```
# Total Customers
total_customers = len(telco)

# Churned Customers
churned_customers = (telco['Churn Label'] == 'Yes').sum()

# Churn Rate
churn_rate = (churned_customers / total_customers) * 100

print(f'Total Customers: {total_customers}')
print(f'Churned Customers: {churned_customers}')
print(f'Churn Rate: {churn_rate:.2f}%')
```
🔢**Results:**
* Total Customers: 7043
* Churned Customers: 1869
* Churn Rate: 26.54%

🔢**Summary:**  
The company has a churn rate of approximately 26.54%, meaning that for every 100 customers, nearly 27 stop using the service. This is a relatively high number, especially in the telecommunications industry, because customers tend to have long-term contracts with the company they subscribe to.

---

### 2. Churn Analysis
#### 2.1. Churn Rate by Contract
<img width="691" height="455" alt="image" src="https://github.com/user-attachments/assets/b79bd651-700b-45c2-b48a-a5dc388f4dc1" />

#### 2.2. Churn Rate by Tenure
<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/f0b40e22-4e95-48c4-84d1-a1b2324218e5" />

#### 2.3. Churn Rate by Contract and Tenure
<img width="667" height="470" alt="image" src="https://github.com/user-attachments/assets/33e978e0-184c-4103-913f-854cf3afd06c" />

#### 2.4. Churn Rate by Monthly Charges
🔢**Calculate mean and median of Monthly Charges by Churn Label**
```
telco.groupby('Churn Label')['Monthly Charges'].agg(['mean','median'])
```

🔢**Results**  
<img width="239" height="124" alt="image" src="https://github.com/user-attachments/assets/5a6fa831-80cb-461d-81fe-ac432d149703" />

🔢**Visualization**  
<img width="571" height="455" alt="image" src="https://github.com/user-attachments/assets/f6d7351d-3a4d-45c0-834a-c73fc7ba0770" />

#### 2.5. Churn Rate by Contract and Monthly Charges
<img width="574" height="455" alt="image" src="https://github.com/user-attachments/assets/7d362349-f8e4-4f96-82e9-9375e225dc5b" />

#### 2.6. Churn Rate by Payment Method
<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/c9051083-aa67-4013-ac0c-ce2e183ad3ff" />

#### 2.7. Churn Rate by Internet Service
<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/45f3bb4b-6876-4de1-b157-8d9e8a0d417f" />

#### 2.8. Churn Rate by Tech Support
<img width="543" height="455" alt="image" src="https://github.com/user-attachments/assets/1b282dfd-1080-4d01-8966-6294268d3faa" />

---

#### 📊**Observation**
<table>
  <thead>
    <tr>
      <th> Factor </th>
      <th> Analysis </th>
      <th> Insight </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td> Contract </td>
      <td> Customers using month-to-month contracts have the highest churn rate among the three contract types, while customers using two-year contracts have the lowest churn rate </td>
      <td> Long-term service commitment helps reduce customer churn rates </td>
    </tr>
    <tr>
      <td> Tenure </td>
      <td> The churn rate is inversely proportional to the length of time a customer uses a service, meaning the longer a customer uses a service, the harder it is for them to leave. Customers using the service in the first year have the highest churn rate, which decreases significantly in the second year </td>
      <td> The majority of customers stop using the service in the early stages of the customer lifecycle </td>
    </tr>
    <tr>
      <td> Contract and Tenure </td>
      <td> The month-to-month customer segment has a higher churn rate than other segments, especially those using the service for the first 12 months, which has the highest churn rate at 51.4% </td>
      <td> This is the high-risk customer segment, which the company needs to focus more resources on </td>
    </tr>
    <tr>
      <td> Monthly Charges </td>
      <td> Customers with high churn rates typically pay higher fees, with an average difference of approximately $13 per month </td>
      <td> The higher the amount customers have to pay, the higher the churn rate </td>
    </tr>
    <tr>
      <td> Contract and Monthly Charges </td>
      <td> Customers with higher monthly charges have a higher churn rate in the month-to-month group </td>
      <td> Significant impact of service pricing on customers without long-term commitment </td>
    </tr>
    <tr>
      <td> Payment Method </td>
      <td> Customers using electronic checks have a higher churn rate compared to other payment methods, possibly due to the inconvenience of manual operation and verification </td>
      <td> Encourage customers to use automated payment methods such as bank transfer or credit card </td>
    </tr>
    <tr>
      <td> Internet Service </td>
      <td> Fiber Optic customers experience a higher churn rate compared to DSL, despite it being a modern and popular service with significantly higher speeds </td>
      <td> The reason is likely due to higher customer expectations for Fiber Optic or issues encountered during service use such as cable breaks, slow speeds during peak hours, etc </td>
    </tr>
    <tr>
      <td> Tech Support </td>
      <td> Customers who do not use Tech Support have a significantly higher churn rate. However, customers who do use Tech Support still have a churn rate of around 15% </td>
      <td> Technical support plays a crucial role in customer retention, but the quality of support services needs improvement</td>
    </tr>
  </tbody>
</table>

---

### 3. Churn Driver Analysis
#### 3.1 Top Churn Reasons
<img width="860" height="435" alt="image" src="https://github.com/user-attachments/assets/83fd2bda-36c8-420b-8dcb-29c70e74907a" />

In general, the most common reasons why customers stop using a service relate to competitors, attitude of customer supports, and service quality.

#### 3.2 Churn Reason Category Distribution
🔢**Create Churn Reason Category**
```
reason_mappinng = {
    'Competitor made better offer' : 'Competitor',
    'Competitor had better devices' : 'Competitor',
    'Competitor offered higher download speeds' : 'Competitor',
    'Competitor offered more data' : 'Competitor',

    'Attitude of service provider' : 'Customer Service',
    'Attitude of support person' : 'Customer Service',
    'Poor expertise of online support' : 'Customer Service',
    'Poor expertise of phone support' : 'Customer Service',

    'Price too high' : 'Price',
    'Long distance charges' : 'Price',
    'Extra data charges' : 'Price',

    'Product dissatisfaction' : 'Service Quality',
    'Service dissatisfaction' : 'Service Quality',
    'Lack of self-service on Website' : 'Service Quality',
    'Lack of affordable download/upload speed' : 'Service Quality',
    'Network reliability' : 'Service Quality',
    'Limited range of services' : 'Service Quality',

    'Moved' : 'Personal',
    'Don\'t know' : 'Personal',
    'Deceased' : 'Personal'
}

telco['Churn Reason Category'] = telco['Churn Reason'].map(reason_mappinng)
```
🔢**Calculate total number of reasons for each category**
```
churn_reason_category = telco[telco['Churn Label'] == 'Yes']['Churn Reason Category'].value_counts()
churn_reason_category
```
🔢**Visualization**  
<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/734405f4-e57e-4337-af1f-ad8a8525809d" />
<img width="815" height="790" alt="image" src="https://github.com/user-attachments/assets/99134f24-7c24-4a06-9540-852725b8af48" />

🔢**Insight**
* Competitors are the biggest reason for customers quitting services
* In addition, service quality and customer support are also reasons for high churn rates

## 💡6. Key Findings & Business Recommendations
### **1. Customers using Month-to-Month Contracts Exhibit the Highest Churn Rate**
📓 Recommendation: Encourage customers to switch to one-year or two-year contracts.

🔹 Actions  
* Offer 1-2 months of free service for customers who sign long-term contracts.
* Launch seasonal promotional campaigns.
* Implement a customer loyalty program to reward long-term commitment.

### **2. Nearly Half of Customer Churn Occurs Within the First Year**
📓 Recommendation: Focus retention efforts on the early stages of the customer lifecycle.

🔹 Actions  
* Send welcome emails with service guides and support contact information.
* Conduct monthly follow-up calls to check customer satisfaction and address potential issues.

### **3. Customers with Higher Monthly Charges Tend to Churn More Frequently**
📓 Recommendation: Reassess the value proposition offered to high-paying customers.

🔹 Actions  
* Develop more flexible pricing plans tailored to different customer segments.
* Provide additional benefits and exclusive offers for premium customers.

### **4. Fiber Optic Service Shows an Unusually High Churn Rate**
📓 Recommendation: Improve the quality of Fiber Optic services and enhance the overall customer experience.

🔹 Actions  
* Investigate potential technical issues affecting service quality.
* Monitor and analyze customer support requests related to Fiber Optic services.

### **5. Tech Support Significantly Reduces Customer Churn**
📓 Recommendation: Integrate Tech Support into existing service packages instead of offering it as a standalone package.

🔹 Actions  
* Include Tech Support in packages while adjusting pricing accordingly to improve retention.
* Offer on-site technical assistance for customers who require additional support.

### **6. Competitors Are the Primary Driver of Customer Churn**
📓 Recommendation: Develop customer retention programs to prevent customers from switching to competitors.

🔹 Actions  
* Introduce a loyalty rewards system with points and exclusive benefits.
* Identify high-risk customers and provide personalized retention offers before they leave.
