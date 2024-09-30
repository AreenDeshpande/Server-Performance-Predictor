# **Data Center System Performance Prediction**

## **Overview**

This project focuses on predicting server performance in a busy data center using various hardware specifications. The goal is to develop a predictive model that can anticipate slowdowns and inefficiencies during peak hours, helping the IT team manage resources more efficiently. By predicting performance, administrators can plan ahead and prevent delays in data processing, ensuring smoother data center operations.

## **Project Purpose**

In a data center, servers handle large volumes of data and run critical operations. However, performance bottlenecks can arise due to various hardware factors, such as insufficient cooling or memory constraints. This project aims to:
- Analyze the relationship between hardware specifications and system performance.
- Build a predictive model to forecast server performance using these hardware attributes.
- Provide insights into potential performance slowdowns, especially during peak periods, so administrators can take preemptive action.

## **Dataset Description**

The dataset contains key hardware features of servers that are critical to their performance. The columns in the dataset are as follows:

- **ID**: Unique identifier for each server.
- **RAM Capacity**: The amount of RAM (in GB) available in each server.
- **Power Supply Wattage**: The wattage capacity of the server's power supply unit (PSU).
- **Cooling Efficiency**: The effectiveness of the server's cooling system, expressed as a percentage.
- **Storage (HDD)**: The capacity and speed of the server's hard disk drive.
- **Total Storage**: The total amount of storage (both HDD and SSD).
- **Activation Date**: The date the server was brought into operation.
- **System Information**: Detailed information about the server, including CPU and GPU specifications, core count, and foundries.
- **System Performance**: The target variable indicating the performance of the system (this is the predicted variable).

### **Dataset Modifications**

- **Cleaning Non-Numeric Values**: Several columns, such as `Cooling Efficiency`, contained non-numeric values (e.g., percentages, strings). These were cleaned by stripping out characters like `%` and coercing invalid entries to `NaN`.
- **Handling Missing Data**: Missing values were handled by either filling them with appropriate statistics (e.g., mean or median) or by removing rows with excessive missing values.
- **Feature Engineering**: New features such as `Total Storage` were derived by summing up individual storage components like HDD and SSD. Date-related features (e.g., server age) were also created using the `Activation Date`.

## **Model Used**

The project utilizes a **Random Forest Classifier** to predict server performance based on hardware specifications. Random Forest is a robust machine learning algorithm that builds multiple decision trees during training and outputs the mode of the classes (for classification tasks) of the individual trees.

### **Why Random Forest?**
- **Handling High-Dimensional Data**: With over 4000 columns, Random Forest efficiently handles a large number of features without overfitting.
- **Feature Importance**: It provides insights into which hardware specifications are most important in predicting system performance.
- **Resilience to Missing Data**: Random Forest can handle datasets with some missing values effectively.

### **Training Process**
- **Train-Test Split**: The dataset was split into training and testing sets to evaluate model performance.
- **Normalization**: Hardware specifications such as RAM and storage sizes were normalized to ensure that all features had similar scales.
- **Feature Importance**: Random Forest's built-in feature importance was used to identify which hardware factors had the greatest impact on system performance.
