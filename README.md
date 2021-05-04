# lending_club_data_science


**The Goal of Project**

The goal of the project is examining the data exploration and visualization techniques and building a Neural Networks by using Tensorflow-Keras API, to classify loaning status. 

---

**Table of Contents**

* [Directory structure](#directory-structure)
* [Explaination of Project](#explaination-of-project)
* [Discussion of Results](#discussion-of-results)
* [About Author](#about-author)

---

## Directory structure

```
.
├── Data
│   ├── .gitattributes
│   ├── lending_club.csv
│   └── lending_club_info.csv
├── Models
│   └── loan_status_classifier.h5
├── LICENSE
├── Lending_Club_Loan_Classifier.ipynb
├── README.md
└── requirements.txt
```

---

## Explaination of Project


The project consists of 4 main parts:
* Loading Data
* Exploratory Data Analysis and Visualization
* Data Wrangling
* Classification of Loan Status


Although the dataset is provided from [Kaggle All Lending Club Loan Data](https://www.kaggle.com/wordsforthewise/lending-club), there may be differences between the version on the Kaggle and the dataset in the [Data](https://github.com/singultek/lending_club_data_science/blob/main/Data/lending_club.csv) folder.

The dataset always needs for preprocessing operations before to feed the machine learning models with the data. In terms of data wrangling, deleting unnecessary features, dealing with missing values can be done. Some features of dataset may not be useful to accomplish the classification task. In fact, some of them may decrease the model performance without giving any deep insight information of data. In order to prevent this situation, one can drop the emp_title, emp_length, title, revol_util and pub_rec_bankruptcies features. Additionally, missing values of mort_acc is replaced by mean value of total_acc feature. Replacing with mean value of feature total_acc is selected with respect to have the highest correlation between the mort_acc and all other features. 

One of the key tools of the data analysis is of course visualization. By the help of visualization, one can understand better the data, behaviour and distribution of data and relation between features. In this project, one can state the importance of grade and sub_grade features, and their relation between loan status. Addition to that, target feature's encoding is held on this section.

Before getting into the loan status classification, another dramatically effective steps will be performed. These steps are checking the missing data, examining the importance of missing data and finally encoding categorical features, Encoding is necesary for non-integer values. One need to encode the term, sub_grade, verification_status, purpose, initial_list_status, application_type and home_ownership features. Addition to these features, earliest_cr_line and address features are preprocessed to extract useful portion of the information from original information stored in the features. After performing extraction of useful information, the features are encoded as well. 

Then, splitting the dataset is succeeded. Finally, normalization process is performed to the train and test dataset with the input features. The target portion of the train and test datasets won't be normalized. On the other hand, normalizing the target datasets and after predictions getting back to normal scale could be another solution aspect to the problem.

After completing the preprocessing steps, classification of loan status can be computed. Deep neural network model is built with the help of tensorflow and performance of the model is evaluated with binary cross entropy since this classification task is binary classification.




---

### Discussion of Results



|                               |  Precision  |  Recall  |  F1 SCORE  |
|-------------------------------|-------------|----------|------------|
| Class 0 (Charged Off)         |    0.96     |   0.45   |    0.61    |
| Class 1 (Fully Paid)          |    0.88     |   1.00   |    0.94    |
| Accuracy                      |             |          |    0.89    |
| Macro Average                 |    0.92     |   0.72   |    0.78    |
| Weighted Average              |    0.90     |   0.89   |    0.87    |

4 metrics is based on the measuring the goodness of the predictions. Accuracy, precision, recall and F1 score metrics are used to evaluate the model.  

One can see from the results, the overall performances of the model is promising. Roughly, one can state that model represents the data with 89% accuracy, which can be considered as decent. However, one should note that data is highly imbalanced. 80% of the dataset is fully paid, which means if the model always predicts fully paid loan status, model's accuracy will be 80%. Hence, 89% of accuracy should not mislead us, though it is definetely descent enough, but not fantastic. One can consider the F1 scores to have better understanding of model representation of data. Low recall of charged off class indicates that the model is not performing good enough for lower represented data. Lower representation of data has lower F1 score, which is totally expected because F1 score is harmonic average of precision and recall scores.

In a nutshell, the model has better accuracy(89%) than random prediction(50%) and straight prediction of fully paid(80%). 

---


### About Author

I'm Sinan Gültekin, a master student on Computer and Automation Engineering at University of Siena. 

For any suggestions or questions, you can contact me via <singultek@gmail.com>

Distributed under the GPL-3.0 License. _See ``LICENSE`` for more information._
