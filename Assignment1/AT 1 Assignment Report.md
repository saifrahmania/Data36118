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
*Figure 1: Bar chart of the top 20 most frequently used words in the dataset.*



## 2.2 N-Grams
From the Top 20 Most common or frequently used we also can find several insights that can help us the to predict the upcoming most common or significantly important professions in the upcoming job markets. Motst frequent used bigrams such as **"health safety"** and **"technical knowledge "** give us the strong messasge that in future the job market will also experience a significant dominance by the health and safety professionals and the technical knowledge will be the most important skill that will be required in the upcoming job markets. Similarly, most frequent used trigrams such as **"specialist technical knowledge"** and **"work health safety"**confirm the with demand of people who have highly specialized skills the work health and safety professionals will be in high demand in the upcoming job markets.

![Top 20 Most Frequent Bigrams](https://github.com/saifrahmania/Data36118/blob/083030f7c8ef7190785dbf58bec071f2cf262d6b/Assignment1/figs/Top%2020%20Most%20Frequent%20Bigrams%20in%20skills%20Descriptions.png)
*Figure 2: Bar chart of the top 20 most frequently used bigrams in the dataset.*

These patterns depict that industries such as healthcare, engineering, and constriction are extremely prioritizing the health and safety standards of their employees and there might be a probability that skilled workers  who also have the significant knowledge about work health and safety knowledge will be highly in demand in the upcoming job markets. The emphasis on terms related to project management and protective equipment also suggests that the roles demand not only the expertise but also the the ability to manage and lead projects with safety and efficiency.

![Top 20 Most Frequent Trigrams](https://github.com/saifrahmania/Data36118/blob/083030f7c8ef7190785dbf58bec071f2cf262d6b/Assignment1/figs/Top%2020%20Most%20Frequent%20Trigrams%20in%20Skills%20Descriptions.png)
*Figure 3: Bar chart of the top 20 most frequently used trigrams in the dataset.*

So, it can be said that n-gram analysis helped us with very important informations or knowledges that can be used to predict the future job market trends.

![Most frequently used wordcloud](https://github.com/saifrahmania/Data36118/blob/932ad7542064564a7f58facbfa392991f5ef2088/Assignment1/figs/Word%20cloud%20Mot%20frequently%20used%20wordcloud.png)
*Figure 4: Word cloud of the most frequently used words in the dataset.*

from the given bigram and trigram network graph we can we will also get a clear idea about the most common and frequently used words in the dataset and the most common and frequently used words in the dataset are the most important words that can be used to predict the future job market trends.

![Most frequently used bigram network graph](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/bigram%20network%20graph.png)
*Figure 5: Network graph of the most frequently used bigrams in the dataset.*
![Most frequently used trigram network graph](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/trigram%20network%20graph.png)
*Figure 6: Network graph of the most frequently used trigrams in the dataset.*
![Top 20 Bigram](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/top%2020%20bigram.png)
*Figure 7: Top 20 Most Used Bigram*

From the bargraph and the box plot we can also notice that most skill descriptions in the dataset contain between 25 and 40 words. While there are descriptions that are shorter or longer, these are less common. A very small number of descriptions are unusually long (over 80 words) which can be considered outliers based on the length of the descriptions.
![Bar plot of the length of skill descriptions](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/bar%20graph%20description%20length.png)
*Figure 8: Bar chart of the length of skill descriptions in the dataset.*
![Box plot of the length of skill descriptions](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/box%20plot%20description%20length.png)
*Figure 9: Box plot of the length of skill descriptions in the dataset.*

## 2.3 Dependency Tree
The dependency tree of the dataset shows the relationship among words that provides a clear explanation of different entities and their relationships each other. 
- 1. **"Track and monitor resource supply, stock, use, demand, state, or quality in order to ensure the effective supply, allocation and use of materials, equipment, finances or human resources."**
    - This sentence uses coordinated verbs "Track" and "monitor" to emphasize continuous oversight of various aspects like supply and demand. The use of an infinitive phrase "in order to ensure" introduces the purpose of this monitoring—effective management and utilization of resources, highlighting a goal-directed action within organizational operations.
- 2. **"Adjust resources and address issues or bottlenecks as required."**
    - Here, the verbs "Adjust" and "address" are central, pointing to responsive actions in operational management. The phrase "as required" signifies these adjustments are conditional and tailored to specific needs or challenges, suggesting adaptability in operational strategies.
- 3. **"Direct and oversee health care operations."**
    - Simple yet powerful, this sentence uses the verbs "Direct" and "oversee" to depict authoritative control and supervision, indicating a hierarchical and management-focused approach in healthcare settings.

- 4. **"This may involve providing technical or specialist expertise and guidance or undertaking project management tasks such as determining and managing resourcing, scheduling, and ensuring compliance with relevant legislation, codes, and standards."**
    - The modal "may" introduces potential activities, expanding the scope of duties to include both providing expertise and managing projects. The detailed list that follows "such as" outlines specific project management tasks, stressing the comprehensive nature of responsibilities and the critical need for compliance and adherence to standards.
- 5. **"Undertake patient identification procedures to match patients to intended procedures or treatments in order to ensure patients receive the care intended for them and to prevent errors or adverse outcomes."**
    - The verb "Undertake" introduces a procedural action focused on patient safety and accuracy in healthcare delivery. The use of "in order to" twice emphasizes the goals of accuracy in treatment and error prevention, underlining the high stakes and meticulous care required in healthcare environments.
By analyzing the dependency tree, we can say that, each sentence is structured to clearly define roles, responsibilities, and goals within an organizational framework, often with a focus on compliance, efficiency, and careful management of resources and operations. These analyses highlight how each action fits into broader operational objectives, ensuring clarity and purpose in the workflow.

From the sentence that we can find from the dependency the true focuses mostly on operational and precedural actions within the organizational and helthcare settings. The dataset also highlights skills related to project managements, resource allocation and complaince with regulations and standards

While these sentences do not directly mention or analyze trends in skills specifically for Australia, they do imply certain skill sets that are likely to be valuable:

- **Resource Management:** Skills in effectively tracking, monitoring, and adjusting resources, including human resources, finances, and materials, are highlighted. This suggests a trend towards valuing operational efficiency and resource optimization in various sectors.

- **Project Management:** The mention of undertaking project management tasks, including scheduling and compliance, points towards the need for strong project management capabilities. This includes planning, execution, and regulation adherence, which are critical in both business and healthcare settings.

- **Healthcare Management:** Directing and overseeing healthcare operations, along with ensuring patient safety through meticulous identification and treatment procedures, underscore the importance of specialized healthcare management skills.

- **Regulatory Compliance:** Ensuring compliance with legislation, codes, and standards across different operations suggests a continuing trend towards the importance of regulatory knowledge and compliance management.

 - **Technical Expertise:** Providing technical or specialist expertise and guidance indicates a demand for specialized knowledge and skills, which can be crucial in technology-driven or technically complex fields.

These points suggest a broader trend where management, technical expertise, compliance, and efficiency are likely to remain important in the Australian job market, reflecting global trends in professional skills demand.

## 2.5 TF-IDF and Similarity

The analysis using TF-IDF vectorization, cosine similarity, and Latent Dirichlet Allocation (LDA) on the dataset shows the structural and thematic similarities within the text data of the **ANZCO Descriptions** column. The TF-IDF vectorization displays the importance of words by their constant use and uniqueness, revealing key terms such as 'equipment,' 'information,' and 'requirements' that are central to the dataset. The cosine similarity matrix, which shows varied similarity scores such as 1.0 for identical comparisons and lower scores like 0.092 for documents with less similaity, and from these insights we can determine how closely related different documents are which help us while groupings with most similar fields or similarities in content focus. 
![TF-IDF Score Distribution](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/TFIDF%20Score%20distribution.png)
*Figure 10: Distribution of TF-IDF scores for the dataset.*
![TF-IDF Scatterplot](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/TFIDF%20Score%20scatter%20plot.png)
*Figure 11: Scatter plot of TF-IDF scores for the dataset.*

![TF-IDF Cosin Similarity Index](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/TFIDf%20cosin%20similarity%20idx.png)
*Figure 12: Cosine similarity matrix for the dataset.*


## 2.5 Clustering
The silhouette analysis for KMeans clustering with cluster counts ranging from 2 to 5 shows different levels of cluster quality. At two clusters, the silhouette plot shows significant overlap and do not fit properly, as indicated by a mix of positive and negative silhouette scores, suggesting weak cluster definitions. Adding a third cluster improves the separation and decreases the number of negative scores, though a minor amount of  overlaps still exist. Four clusters offer more defined clustering with two clusters achieving higher silhouette scores but still featuring some misfit within one cluster. Expanding to five clusters does not necessarily enhance clarity but increases variability, with some clusters showing tight groupings and others mixed or negative values. This analysis suggests that three or four clusters may offer the most balanced clustering, minimizing misclassification while avoiding overfitting.
![Silhouette Analysis for Cluster 2](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Silhouette%20analysis%20for%20KMeans%20clustering%202.png)
*Figure 13: Silhouette analysis for KMeans clustering with 2 clusters.*
![Silhouette Analysis for Cluster 3](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Silhouette%20analysis%20for%20KMeans%20clustering%203.png)
*Figure 14: Silhouette analysis for KMeans clustering with 3 clusters.*
![Silhouette Analysis for Cluster 4](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Silhouette%20analysis%20for%20KMeans%20clustering%204.png)
*Figure 15: Silhouette analysis for KMeans clustering with 4 clusters.*
![Silhouette Analysis for Cluster 5](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Silhouette%20analysis%20for%20KMeans%20clustering%205.png)
*Figure 16: Silhouette analysis for KMeans clustering with 5 clusters.*
![Distribution Cluster](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Distribution%20of%20Clusters.png)<br>
*Figure 17: Distribution of Clusters*

If we look at the cluster distribution, we can see that more cluster we make more evenly the occupations become divided and it becomes easier to make the distribution
![Top 10 Topic of cluster](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Ten%20Cluster.png)
*Figure 18: Top 10 Topic of cluster*



# 3. Language Modeling 
## 3.1 Topic Model
The LDA model shows five most import themes such as interpersonal and organizational skills, operational and procedural nuances, medical and regulatory details, technical and safety requirements, and business and financial management. These themes dipict different skill sets and knowledge areas and their relationship can be found in the dataset from technical proficiencies to compliance and interpersonal abilities.
These are critical for merging programs or difing the job roles within organizations. The detailed topic words from LDA such as 'activities,' 'staff,' and 'provide' for organizational skills, or 'order,' 'data,' and 'materials' for operational aspects, offer a granular view of the dataset's focus, that explains the  strategic planning and educational alignment to industry needs in a wider manner.
![Topic wise LDA Graph](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/Topicwise%20LDA%20Model.png)
*Figure 19: Topic wise LDA Graph*
## 3.2 Sentiment Analysis
While doing the analysis  it has been found that there is a pattern in the dataset and this relationship can be relationship into a histogram 
![Sentiment Analysis](https://github.com/saifrahmania/Data36118/blob/main/Assignment1/figs/sentiment%20analysis.png)<br>
*Figure 20: Sentiment analysis of the dataset.*

Here are the findings that can be found in the graph:

- Certral Tendency: Most of the sentiments are concentrated around zero, along with the neutrality,  with the most entries (13,976) between -0.02 and 0.02.
- Negative Sentiment: Negative sentiments are less common and range from -0.50 to -0.10, i.e., the bin from -0.14 to -0.10 has 1,761 entries, suggesting a presence of mild negative sentiments.
- Positive Sentiment: The variaty of positive sentiment are also visible but not as extreme as the other sentiment, such as, the bin from 0.10 to 0.14 has 1,098 entries, showing moderate positivity, extending up to a maximum of 0.70 with decreasing frequency.
- Sentiment Extremes: Extreme positive and negative sentiment are quite rare, which mostly visible to neutral and mild sentiments
- Skewness and Depression: The distribution is  centered with a slight skew towards positive sentiments, particularlywith the higher positive scores such as 0.50 to 0.54 with 425 entries.

## 3.3 Top Words by Topic
The analysis of the top words by topic from the LDA model output provides a deep dive into the thematic structures within the dataset. Here's an analysis based on the extracted top words for each topic and the overall coherence score:

### Analysis of Top Words by Topic:

**Topic 1: Compliance and Record Management**
- Dominated by terms like "information," "records," "requirements," and "policies," this topic likely pertains to the regulatory and compliance aspects, emphasizing the importance of maintaining and ensuring accurate records and adhering to specific standards or policies.

**Topic 2: Patient and Healthcare Data Management**
- With words such as "patient," "issues," "data," and "service," this topic centers around healthcare services, focusing on patient data handling and issue resolution, highlighting the relevance of information management in healthcare settings.

**Topic 3: Social Practices and Environmental Considerations**
- Highlighting terms like "example," "environments," "social," and "practices," this topic suggests a focus on environmental and social contexts, possibly discussing best practices and principles in social care or community-oriented environments.

**Topic 4: Inventory and Record Keeping**
- Key terms such as "record," "stock," "keeping," and "monitoring" indicate this topic's focus on inventory management and systematic record keeping, essential for operational efficiency in business or organizational contexts.

**Topic 5: Project Management and Technical Operations**
- With "include," "providing," "technical," and "project," this topic is clearly about project management and technical operations, emphasizing the integration of specialized knowledge into practical applications.

**Topic 6: Education and Learning Development**
- This topic, with words like "learning," "skills," "students," and "development," revolves around educational settings and learning development, stressing the importance of supporting student growth and skills enhancement.

**Topic 7: Service Provision and Safety**
- Terms such as "provide," "services," "safely," and "support" suggest a focus on service delivery, particularly in contexts requiring adherence to safety standards and organizational policies to support client or customer needs effectively.

**Topic 8: Staff Management and Research Activities**
- Highlighting "activities," "staff," and "research," this topic deals with managing staff and conducting research, indicating a strong emphasis on knowledge generation and operational management within teams.

**Topic 9: Healthcare Planning and Patient Care**
- With terms like "medical," "care," "plans," and "treatment," this topic pertains to medical and healthcare planning, focusing on patient care strategies and treatment planning, essential for effective healthcare delivery.

**Topic 10: Operational Safety and Material Handling**
- Dominated by "equipment," "safety," "work," and "materials," this topic focuses on operational safety and handling of materials and equipment, crucial for maintaining safe working environments and complying with safety standards.


## 3.4 Topic Coherence
The coherence score of 0.4338, though not exceptionally high, is indicative of a moderate level of semantic similarity within the words that define each topic. This score helps in understanding how meaningfully the top words are associated with the topics, suggesting that while there is a reasonable thematic consistency, there might be room for refining the model to achieve clearer, more distinct topic separations.

This analysis offers valuable insights into the key themes prevalent in the dataset, aligning closely with specific professional domains and operational areas. Adjustments to model parameters or further textual preprocessing might enhance the distinctiveness and relevance of the topics, potentially improving the coherence score.

# 4. Conclusion

This insight is valuable for identifying areas for policy development, operational improvements, or training programs, highlighting the need for continuous model evaluation to refine insights and support strategic decision-making in organizations. The findings underscore the relevance of adapting analytical models to better meet organizational needs and extract actionable insights from complex datasets.