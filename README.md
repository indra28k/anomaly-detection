# Anomaly Detection Project

## Anomalous Score >= 2
(The result of the model gives the Range from 1-10, so if the scores is >=3, its a anomalous record)

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Algorithms Used](#algorithms)

<h2 id="introduction">Introduction</h2>
Anomaly detection plays a crucial role in identifying and mitigating potential security threats. This project focuses on detecting anomalies in user login behavior, which can help identify suspicious activities such as unauthorized access attempts or compromised user accounts. The project utilizes machine learning techniques, specifically XGBoost, to train an anomaly detection model based on a labeled dataset. The trained model can then be used to classify new login events as normal or anomalous based on their features.

<h2 id="installation">Installation</h2>
1. Clone the repository:
```
git clone https://github.com/indra-siripurapu/anomaly-detection.git
cd anomaly-detection
```

2. Create and activate a virtual environment (optional but recommended):
```
python3 -m venv env
source env/bin/activate
```

3. Install the required dependencies:
```
pip install -r requirements.txt
```

4. Download the dataset:
The dataset used for training and testing the anomaly detection model should be placed in the "data" directory. Make sure to follow the appropriate data format and column structure.

<h2 id="usage">Usage</h2>

### Data Preparation
1. Place your login data file (Login_Data.csv) in the project root directory.
2. Open the anomaly_detection_stgi.ipynb notebook in Jupyter Notebook or JupyterLab.
3. Execute the notebook cells to preprocess the data, perform feature engineering, and create the target variable.
4. Save the preprocessed data to a file:
```
data.to_csv("preprocessed_data.csv", index=False)
```

### Model Training
1. Open the anomaly_detection_stgi.ipynb notebook in Jupyter Notebook or JupyterLab.
2. Execute the notebook cells to load the preprocessed data, split it into training and testing sets, and train the model.
3. Save the trained model to a file, such as a pickle file (.pkl), for future use and deployment. This file will be used to load the trained model during the anomaly detection process.
```python
import pickle
 
with open("regressor_model.pkl", "wb") as file:
    pickle.dump(regressor, file)
```

### Running the FastAPI Server
1. Open the fast_api.py file.
2. Update the file path to the trained model:
```python
with open("regressor_model.pkl", "rb") as file:
    model = pickle.load(file)
```

3. Open the terminal and navigate to the project folder:
```
cd anomaly-detection-project
```

4. Run the FastAPI server:
```
uvicorn fast_api:app --reload
```

5. Open your web browser and visit http://localhost:8000 to ensure the server is running. You should see a "Hello, World!" message.

### Detecting Anomalies
1. To detect anomalies, make a POST request to the /docs endpoint using an API client like cURL or Postman.
2. Set the request URL to http://localhost:8000/docs and provide the following JSON payload:
```json
{
    "Country": <country_value>,
    "Device_Type": <device_type_value>,
    "Login_Successful": <login_successful_value>,
    "LoginRatio": <login_ratio_value>,
    "Final_Browser_Category": <final_browser_category_value>,
    "Total_Device_Types": <total_device_types_value>,
    "Total_IP_Addresses": <total_ip_addresses_value>,
    "Total_Countries": <total_countries_value>,
    "Total_Browser_Categories": <total_browser_categories_value>,
    "Time_Difference_in_sec": <time_difference_value>
}
```

3. Replace the <value> placeholders with the corresponding feature values for anomaly detection.
4. The API will respond with the predicted anomaly score for the provided data.
5. (The result of the model gives the Range from 1-10, so if the scores is >=3, its a anomalous record) Anomalous Score >= 2

<h2 id="algorithms">Algorithms Used</h2>
The following algorithms are used in this project:
- XGBoost: XGBoost is an optimized gradient boosting algorithm that is commonly used for classification and regression tasks. It is known for its speed and performance in handling large datasets.

## Maintainer
This project is maintained by Indra Kumar Siripurapu.

Indra Kumar Siripurapu is a Senior Data Analyst with over 8 years of experience specializing in data validation, reconciliation, and compliance-focused reporting. With a strong background in SQL, Power BI, and enterprise data systems, he focuses on translating complex reporting requirements into accurate, audit-ready outputs.

**Contact Information:**
- Email: indra.siripurapu22@gmail.com
- Role: Senior Data Analyst
- Key Skills: SQL, Power BI, SSRS, Tableau