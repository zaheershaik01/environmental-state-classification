# Classification of Environmental IoT Device States Using Machine learning

This project, submitted in partial fulfillment of the requirement for the Bachelor of Technology in Computer Science and Engineering, develops a machine learning model to classify environmental states using IoT sensor telemetry data.

## 📖 Abstract

Traditional environmental monitoring relies on sensors sending data to a central database for manual analysis. This approach suffers from delays, scalability issues, and inefficient data processing. This project addresses these limitations by creating an innovative monitoring system that uses Internet of Things (IoT) sensor data and Artificial Intelligence (AI) models.

The objective is to overcome traditional methods by enabling real-time, automated, and intelligent data analysis. The system uses a rich dataset from environmental monitoring stations—including parameters like temperature, humidity, smoke, LPG gas, and noise levels—and integrates it into an AI-based platform. This platform utilizes advanced machine learning algorithms, specifically **Random Forest**, to analyze data patterns and identify environmental states as "stable," "normal," etc..

## 🎯 Problem Statement

The core problem is the inadequacy of conventional environmental monitoring methods in the face of escalating challenges like climate change and pollution. Traditional approaches often rely on sporadic data collection, leading to delayed responses. Furthermore, the massive volume of real-time data from modern IoT sensors is difficult to process and interpret efficiently. This project aims to create an integrated system that can continuously collect, process, and analyze this real-time data to facilitate timely decision-making.

## 📊 Dataset

The project uses the `iot_telemetry_data.csv` dataset.

**Features Include:**
* **ts:** Timestamp of the reading.
* **device:** The unique identifier for the device. This is also used as the target variable.
* **co:** Carbon Monoxide level.
* **humidity:** Humidity percentage.
* **light:** Boolean value indicating light detection.
* **lpg:** Liquefied Petroleum Gas level.
* **motion:** Boolean value indicating motion detection.
* **smoke:** Smoke level.
* **temp:** Temperature.

**Target Variable:**
The `device` column was label-encoded to create the target variable `condition`, representing three distinct environmental states:
* **0:** `00:0f:00:70:91:0a` (Stable conditions, cooler and more humid)
* **1:** `1c:bf:ce:15:ec:4d` (Highly variable temperature and humidity)
* **2:** `b8:27:eb:bf:9d:51` (Stable conditions, warmer and dryer)

## ⚙️ Project Workflow

The project follows a standard machine learning workflow:

1.  **Library Imports:** Import necessary libraries like Pandas, NumPy, Seaborn, Matplotlib, and Scikit-learn.
2.  **Data Loading:** Load the `iot_telemetry_data.csv` dataset.
3.  **Data Preprocessing:**
    * Drop the `motion` column as it was not useful for prediction.
    * Apply `LabelEncoder` to the `device` (target) and `light` (feature) columns to convert them to numerical values.
4.  **Exploratory Data Analysis (EDA):**
    * Perform univariate analysis (KDE plots) to understand feature distributions.
    * Perform multivariate analysis (box plots) to see relationships between features and the target condition.
    * Generate a correlation heatmap.
5.  **Data Cleaning:**
    * Remove columns with high multicollinearity (`lpg`, `smoke`, `co`).
    * Identify and remove outliers from the dataset.
    * Apply `StandardScaler` to the `humidity` and `temp` columns to standardize the data.
6.  **Data Splitting:** Split the cleaned data into training and testing sets.
7.  **Model Building & Evaluation:**
    * **Model 1 (Baseline):** A **Decision Tree Classifier** is trained and evaluated.
    * **Model 2 (Proposed):** A **Random Forest Classifier** is trained and evaluated.
8.  **Prediction:** Use the trained models to make predictions on unseen test data.

## 📈 Results

The performance of the two models was compared using classification reports and confusion matrices. The Random Forest model significantly outperformed the Decision Tree.

* **Decision Tree Classifier (Baseline):**
    * **Accuracy:** 75%
    * **Performance:** The model struggled significantly with class 1, showing a precision and recall of 0.00 for that class.

* **Random Forest Classifier (Proposed):**
    * **Accuracy:** 98%
    * **Performance:** The model demonstrated excellent and well-balanced precision, recall, and F1-scores across all three environmental state classes, proving it to be a robust and effective solution.

## 🚀 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/environmental-iot-classification.git](https://github.com/your-username/environmental-iot-classification.git)
    cd environmental-iot-classification
    ```

2.  **Install the required libraries:**
    A `requirements.txt` file should contain:
    ```
    numpy
    pandas
    matplotlib
    seaborn
    scikit-learn
    ```
    Install them using pip:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the project:**
    The project is available as a Jupyter Notebook or Python script.
    ```bash
    jupyter notebook "Project.ipynb"
    ```
    *(Note: The source code is provided in the document under `Chapter 9`)*

## 🔮 Future Scope

This project lays the foundation for several future enhancements:
* **Advanced Models:** Explore deep learning networks to potentially improve accuracy further.
* **Data Enrichment:** Expand the dataset with more environmental variables and sensor data.
* **Real-Time Integration:** Incorporate real-time data streams from live IoT devices.
* **Deployment:** Deploy the predictive model into a real-world IoT system for automated decision-making.
* **Anomaly Detection:** Integrate anomaly detection methods to identify abnormal environmental conditions for early intervention.

## 🧑‍💻 Authors & Acknowledgements

**Submitted by:**
* SHAIK ZAHEER (22RA1A05I7)
* M.PRANAY (22RA1A0593)

**Under the guidance of:**
* Mr. RAKESH (Assistant Professor, CSE Dept.)

**KOMMURI PRATAP REDDY INSTITUTE OF TECHNOLOGY, GHATKESAR**
