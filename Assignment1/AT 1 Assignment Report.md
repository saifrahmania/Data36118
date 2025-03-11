# Introduction:

 
To cope up with the dynamic global and economic changes and the rapid advancement of technology the Australian Government has taken a significant effort to modernize, how skills are classified and understood within the workforce and everything has been done through the Jobs and Skills Australia (JSA). The main purpose of this initiatives was to replace the old Australian Skills Classification (ASC) and a new National Skills Taxanomy (NST) will take ASC’s place. The main purpose of this report was to check analyze the data that have been collected about the current job market and the ongoing trends and provide an overview of the data about the future trend. The report will also provide a detailed analysis of the data and the trends that have
been observed.
---
# 1. Data Setup:
## 1.1 Data Loading:  
The initial phase of our data analysis involved of loading the Australian Skills Classification (ASC) classification [dataset](https://www.jobsandskills.gov.au/consultations/national-skills-taxonomy-discussion-paper) which was hosted in a xlxs format which is straight forward to work with and manipulating or formatting. This xlxs file contained lots of sheets based where later this dataset containing several spreadsheets has been manipulated and merged together into one single, csv files then all the analysis have been run on it 
```python
import pandas as pd

url = "https://path_to_data.csv"
data = pd.read_csv(url)
print(data.head())
```
## 1.2 Data Cleaning: 
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

## 1.3 Data Processing with NLP:
**Natural Language processing (NLP)** is one of the most important sector of Generative Artificial Intelligence (GenAI) which is used to process and analyze large amount of textual data. In this report, we have used NLP to process the textual data in the dataset. We have used the **nltk** library to process the textual data. We have used the **word_tokenize** method to tokenize the textual data and the **FreqDist** method to find the frequency distribution of the words in the textual data. We have also used the **stopwords** method to remove the stopwords from the textual data. In this assignment we had to use almost all of the NLP techniques to process the textual data in the dataset to retrieve information about the future job market trends. 

# 2. Text Analysis
## 2.1 Most Frequent Words
Analyzing **Top 20 Most Frequent Words** from the dataset to get an idea about the most common words that are used in the dataset we can find the highlights of the important emphasis within the job rolesand skills descriptions. Words like  "ensure" (12,778 occurrences) and "equipment" (12,227 occurrences) reflect a significant focus on compliance, safety, and operational standards in technical fields. Similarly, "relevant," "information," and "requirements" are also appeared inthe dataset quite frequently and that shows the coherence and regularity across the industries. Some other terms such as "data" and "technical" also provide a significant importance on the growing needs of the digitan proficiencies and technical sills but thse vocabularies are not the only things where we should give our focus on the upcomin job markets
It can be considered as a suggestion that can be used to predict the future job market trends but not considering as the only factor to predict the future job market trends. 

![Top 20 Most Frequent used words](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Bar%20frequently%20used%20words.png)





```python
## 2.2 Name Entity Recognition
## 2.3 N-Grams
## 2.4 Dependency Tree
## 2.5 TF-IDF
## 2.6 Similarity
## 2.7 Clustering

# 3. Language Modeling 
## 3.1 Topic Model
## 3.2 Sentiment Analysis
## 3.3 Top Words by Topic
## 3.4 Topic Coherence

# 4. Conclusion