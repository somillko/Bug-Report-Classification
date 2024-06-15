# Bug-Report-Classification
Determining the type of Bug so that relevant developer can be applied.

## Dataset
### The dataset is available on this link

https://drive.google.com/file/d/1Hbzyq4iii0NPLgvwK-S6vzl2FRon415s/view?usp=drive_link, 
https://drive.google.com/file/d/1JIPdsmGiYU-enprCQ2shjQULut2EWdii/view?usp=drive_link,
https://drive.google.com/file/d/18SMaCdUK5al7l-8cZy0Ws5_QjdI-WCdU/view?usp=drive_link,
https://drive.google.com/file/d/1CE6JYkoCbPurHXiAuWAxTZIZFxUpFYDb/view?usp=drive_link,
https://drive.google.com/file/d/1rqBhFryqF4mWyGvNEorJLDc7h30alFtH/view?usp=drive_link,
https://drive.google.com/file/d/1mGH22o4M1zqvy_9s6nXW2YWHOgUt-VRk/view?usp=drive_link

The dataset used for our classification process was used from the JAVA Lucene project hosted on Atlassian. We used JIRA Issue tracking System for downloading our Bug Reports in a Csv Format
The dataset originally had many rows out of which many are useless so I've discarded them and in the end we are left with 13 rows, namely:-
* Issue Key
* Issue ID
* Summary
* Status
* Description
* Priority
* Resolution
* Assignee
* Created 
* Updated
* Last Viewed
* Resolved
* Issue Type        

Since we would be performing our classification process on text data viz the columns of summary and description we would be requiring the help of NLP techniques.We extract the title and summary of for each issue report. Now, we apply the basic pre-processing techniques to clean the data. We then form the corpus of each issue category. Now, we apply the tf-idf function on each corpus. The tf-idf function is a popular method that is useful in extracting important terms present in a given corpus. 

Mean Time to Repair (MTTR) indicates how much time it takes to fix a particular issues, i.e., difference between the date when the issues is fixed and the date to which the issue is filed. MTTR can throw light on which issue category requires maximum time to fix. This can be beneficial in prioritizing the issues.

Brief description of the solution approach
* Initially we have got 13 columns which play a significant role in detecting issue type. Here feature selection plays a major role in extracting the relevant features being used. Applying feature selection will help to eliminate features which are less significant.
* Two of the features namely ‘Summary’ and ‘Description’ were found to be the most useful. They were merged and loaded into a single variable. 
* We took the corpus to model ‘Bag of Words Model’. We create a dictionary of words and their occurrence calculated for each document in the corpus. Then using term frequency and inverse document frequency formulas,we represented our corpus of words in document vectors.
* Initially for model development, the machine learning algorithms we used and compared were Bernoulli and Multinomial Naive Bayes. As each feature variable has short length, and size of dictionary created is very small, the Naive Bayes algorithm doesn’t perform so well on the dataset.
* Then we used Random Forests and SVM on the same, which provide us better results. All these algorithms are compared on different metrics like accuracy, F1-Score, training and testing time.
* These learning algorithms perform the task of searching through a hypothesis space to find a suitable hypothesis that will make good predictions with aparticular problem. But individually all the learning algorithms do not produce good results.
* So we use Ensemble to combine multiple hypotheses to form a (hopefully) better hypothesis. Ensemble methods we have used –
  * Majority Voting (Hard Voting)
  *	Average Voting (Soft Voting)
  *	Bagging of Decision Trees
  * AdaBoost
  * Stochastic Gradient Descent Boosting

Upon working out of all the solution approaches, we come to a conclusion that Majority voting and Random forest perform the best.
### In the Screenshots folder I've put the full control flow diagram and also put up the relative performance comparison of all the approaches. So you can refer to them too, moreover everything used is provided in the ipynb file containing the code.

### For a detailed solution approach and understanding please refer to the code and the report uploaded.
