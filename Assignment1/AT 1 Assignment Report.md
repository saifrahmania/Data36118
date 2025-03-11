# Introduction:

 
To cope up with the dynamic global and economic changes and the rapid advancement of technology the Australian Government has taken a significant effort to modernize, how skills are classified and understood within the workforce and everything has been done through the Jobs and Skills Australia (JSA). The main purpose of this initiatives was to replace the old Australian Skills Classification (ASC) and a new National Skills Taxanomy (NST) will take ASC’s place. The main purpose of this report was to check analyze the data that have been collected about the current job market and the ongoing trends and provide an overview of the data about the future trend. The report will also provide a detailed analysis of the data and the trends that have
been observed.
---
# Data Setup:
## Data Loading:  
The initial phase of our data analysis involved of loading the Australian Skills Classification (ASC) classification [dataset](https://www.jobsandskills.gov.au/consultations/national-skills-taxonomy-discussion-paper) which was hosted in a xlxs format which is straight forward to work with and manipulating or formatting. This xlxs file contained lots of sheets based where later this dataset containing several spreadsheets has been manipulated and merged together into one single, csv files then all the analysis have been run on it 
```python
import pandas as pd

url = "https://path_to_data.csv"
data = pd.read_csv(url)
print(data.head())
```
## Data Cleaning: 
While I was working with the data cleaning at that time I have found lots of empty values and columns what was cleaned and handled to make an perfect dataset on I can work and can retrieve a significant insights that can be used for predicting the upcoming trend of future job market. In order to clean the data, set we had to consider a lot of factors such as data cleaning data manipulation, handling missing values and constantly checking data integrity. We also had to take into consideration that there is minimal or no duplicate data at all. 
```python
# Check for missing values and duplicates
print("Missing Values:\n", data.isnull().sum())
data.drop_duplicates(inplace=True)

# Standardize textual data
data['Skills Statement'] = data['Skills Statement'].str.lower().str.strip()
data['ANZSCO Description'] = data['ANZSCO Description'].str.lower().str.strip()

# Inspect the first few rows to confirm changes
print("First Few Rows:\n", data.head())
```

## Data Processing with NLP:
**Natural Language processing (NLP)** is one of the most important sector of Generative Artificial Intelligence (GenAI) which is used to process and analyze large amount of textual data. In this report, we have used NLP to process the textual data in the dataset. We have used the **nltk** library to process the textual data. We have used the **word_tokenize** method to tokenize the textual data and the **FreqDist** method to find the frequency distribution of the words in the textual data. We have also used the **stopwords** method to remove the stopwords from the textual data. In this assignment we had to use almost all of the NLP techniques to process the textual data in the dataset to retrieve information about the future job market trends. 