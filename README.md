# Supermarket Sales Analysis and Predictive Modeling

## Abstract
This project, developed within the scope of the Supervised Machine Learning course, applies exploratory data analysis (EDA) and predictive modeling techniques to a supermarket sales dataset. The primary objective is to predict the total amount spent by a customer on a purchase, a regression problem involving a continuous target variable. Additionally, classification models are employed to categorize spending behavior. The study encompasses data wrangling, exploratory analysis, and the application of Linear and Logistic Regression algorithms.

## Authors
*   Ilie Iftime (112779)
*   Guilherme Real (124456)
*   Marin Cepeleaga (123550)

## Course Context
This project was developed in 2024 as part of the 2nd year curriculum for the Supervised Machine Learning course.

## Project Structure

```text
1st EDA project/
├── .ipynb_checkpoints/
├── sales.csv
└── Tut1_Sales_VFINAL2.ipynb
```

## 1. Introduction
The objective of this project is to predict the total amount spent by a customer on a purchase based on a set of variables provided in the dataset. This problem falls under the category of regression, as the target variable (total spent) is continuous.

Through data exploration and the application of Data Wrangling and Exploratory Data Analysis (EDA) techniques, the dataset was prepared and split into training and testing subsets. Following preprocessing, Linear Regression models were utilized to predict purchase values, while Logistic Regression was applied for classification scenarios (categorizing high versus low spending).

## 2. Dataset
The dataset was sourced from [data.world](https://data.world/mitcholsmo/supermarket-sales) to conduct this supervised machine learning project. 

The dataset contains 1000 instances spread across the following columns:
*   `total`: Total amount paid after discount (Float)
*   `discount`: Total discount amount applied (Integer, originally Float)
*   `quantity`: Number of products purchased (Integer)
*   `bags`: Number of bags requested (Integer)
*   `rating`: Customer satisfaction score from 1 to 5 (Integer)
*   `staff`: Number of employees in the supermarket at the time of sale (Integer)
*   `outlet`: Supermarket identifier ("A", "B", "C")
*   `gender`: Customer gender ("Male", "Female")
*   `payment`: Payment method ("Credit", "Cash")

## 3. Data Wrangling
The data preprocessing phase involved several key transformations to prepare the dataset for analysis:
*   **Column Cleaning:** Stripped whitespace from column names.
*   **Discount Conversion:** Divided the `discount` column by 100 to convert it from cents to the base currency unit.
*   **Feature Engineering:**
    *   Created `total_bruto` (gross total before discount) by adding `total` and `discount`.
    *   Created `discount_percentage` by calculating the percentage of the discount relative to the gross total.
    *   Created `quantity_discount_interaction` to analyze the discount applied per item.
*   **Feature Selection:** Removed the `outlet` and `bags` columns as they were not relevant to the specific context of the study.

## 4. Exploratory Data Analysis (EDA)
The EDA phase utilized Python libraries including Pandas, NumPy, Matplotlib, and Seaborn to visualize distributions, relationships, and correlations.

### Key Visualizations and Insights:
*   **Distributions (Histograms):** The majority of transaction totals fall within the 80-100 range. Discounts show a higher frequency at lower values, decreasing for median values and rising again for larger discounts.
*   **Categorical Distributions (Countplots):** The customer base is evenly distributed between genders. Credit/Debit cards are the preferred payment method by a margin of 50 occurrences.
*   **Relationships (Scatterplots and Boxplots):** 
    *   Higher discounts are concentrated in the 0.6 to 1% range, primarily on intermediate purchase values.
    *   Female customers tend to spend slightly more than male customers.
    *   Cash is predominantly used for higher-value purchases.
    *   Outlets with more staff show a slight tendency toward higher spending, suggesting customer service may influence purchasing behavior.
*   **Correlation (Heatmap and Pairplot):** A strong positive correlation exists between `total` and `quantity`, as well as between `total` and `discount`. The `rating` variable shows no clear correlation with other numerical variables, indicating that the amount spent or the discount received does not directly affect customer satisfaction ratings.
*   **Density (2D KDE Plot):** High spending density is concentrated among customers purchasing up to 10 items, but total spending increases significantly for higher quantities.

## 5. Predictive Modeling
The dataset was split into an 80/20 ratio for training and testing.

### 5.1 Linear Regression
A Linear Regression model was trained to predict the continuous `total_bruto` variable based on discount, rating, and bags.
*   **Training Performance:** MAE: [Insert Value], MSE: 118.25, R²: 0.77
*   **Testing Performance:** MAE: [Insert Value], MSE: 131.45, R²: 0.77
*   **Analysis:** The model demonstrated a reasonable predictive capability (77% accuracy). However, the scatter plot of Predictions vs. Real Values indicated difficulties in accurately predicting extreme or anomalous values.

### 5.2 Logistic Regression
A Logistic Regression model was applied to a classification task. The `total` variable was binarized based on the median into "High Spend" (1) and "Low Spend" (0).
*   **Training Accuracy:** 83%
*   **Testing Accuracy:** 86%
*   **F1-Score:** 83% (Train), 86% (Test)
*   **Analysis:** The model showed solid performance in classifying customers into distinct spending brackets. The Confusion Matrix and Classification Report were utilized to evaluate precision and recall.

## 6. Conclusion
The primary objective of this project was to predict the total amount spent by a customer. Through Data Wrangling, valuable features were engineered, and EDA provided critical insights into customer behavior, such as the strong correlation between quantity and total spend, and the prevalence of specific payment methods for high-value transactions.

In the predictive modeling phase, Linear Regression proved to be the most appropriate model for the continuous prediction of spending, achieving approximately 77% accuracy. While Logistic Regression achieved higher accuracy (86% on test data) for classification scenarios, its utility was more restricted given the continuous nature of the primary problem. 

Overall, combining supervised learning techniques with robust data manipulation allowed for the construction of predictive models that offer reliable insights into customer consumption behavior. Future improvements could include incorporating additional variables or employing more sophisticated algorithms.

## 7. References
*   Navlani, A., Fandango, A., & Idris, I. (2024). *Python data analysis* (3rd ed.). Packt Publishing.
*   VanderPlas, J. (2016). *Python data science handbook: Essential tools for working with data*. O'Reilly Media.

## 8. Environment Setup and Installation
To replicate this analysis and run the Jupyter Notebook, follow the steps below to configure a Python virtual environment and install the necessary dependencies.

### Prerequisites
*   Python 3.x installed on your system.
*   A terminal or command prompt (PowerShell, Bash, etc.).
*   Jupyter Notebook or Visual Studio Code with the Jupyter extension.

### Step 1: Create a Virtual Environment
Navigate to the root directory of the project (`1st EDA project`) and create a virtual environment:

```bash
python -m venv venv
```

### Step 2: Activate the Virtual Environment
Activate the environment based on your operating system:

*   **Windows (PowerShell):**
    ```powershell
    .\venv\Scripts\Activate.ps1
    ```
*   **Windows (Command Prompt):**
    ```cmd
    .\venv\Scripts\activate.bat
    ```
*   **macOS / Linux:**
    ```bash
    source venv/bin/activate
    ```

### Step 3: Install Required Packages
With the virtual environment activated, install the necessary data science and machine learning libraries:

```bash
pip install jupyter pandas numpy matplotlib seaborn scikit-learn
```

### Step 4: Launch the Notebook
Start the Jupyter Notebook server from the terminal:

```bash
jupyter notebook
```

Alternatively, open Visual Studio Code, navigate to the project folder, and open `Tut1_Sales_VFINAL2.ipynb`. Ensure the kernel is set to the `venv` environment created in Step 1.