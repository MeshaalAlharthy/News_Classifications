# Arabic News Classification
This repository contains a simple rule-based text classification model for categorizing Arabic news articles. The dataset consists of news articles, each containing a title, content, and a link to the full article. The goal is to classify the articles into predefined categories based on the content using a keyword-based rule approach.

Project Structure
Dataset: The dataset includes four columns: Title, Content, Link, and Category.

Classification Method: The classification is done by checking the presence of certain keywords in the content and mapping it to the corresponding category.

Tools Used:

Python

pandas

Jupyter Notebooks

Requirements
To run this project, you need the following Python packages:

pandas

You can install the required packages using pip:

bash
نسخ
pip install pandas
Usage
Download the dataset (processed_data.csv) and place it in the same directory as the Jupyter notebook.

Open the Jupyter notebook and run the code cells.

The dataset will be loaded and analyzed, and a rule-based classification function will be applied to categorize the articles.

The result will display the distribution of the predicted categories.

Example Code
python
نسخ
import pandas as pd

# Load the dataset
df = pd.read_csv('processed_data.csv')

# Define the rule-based classification function
def classify_category(text):
    if pd.isna(text):
        return 'Unknown'
    text = text.lower()
    if any(word in text for word in ["الاعمال", "الشركات", "شركه", "الناشءه"]):
        return 'ريادة أعمال'
    elif any(word in text for word in ["يمكن", "عام", "بشكل"]):
        return 'علوم وتكنولوجيا'
    elif any(word in text for word in ["المتحده", "الامم", "الامين"]):
        return 'أخرى'
    else:
        return 'Unknown'

# Apply the function to classify categories
df['Predicted_Category'] = df['Content'].apply(classify_category)

# Display the distribution of predicted categories
predicted_category_distribution = df['Predicted_Category'].value_coun
print(predicted_category_distribution)
