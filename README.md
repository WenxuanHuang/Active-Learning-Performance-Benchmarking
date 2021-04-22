# Active-Learning-Performance-Benchmarking
In this work, the performance of active-learning (based on logistic regression, random forest, gradient boost classifier, nearest neighbours and SVM) is benchmarked and compared. Employing multiple classifiers in a modularised manner help investigate the difference in performance when active learning is used in combination with these five classifiers. 
## Active learning methods and strategy
### Basic model classifier
Logistic regression and SVM is chosen for its wide use on active learning-powered applications. Nearest neighbours classifiers is used in order to investigate how the quality of data scale and dispersion could affect active learning performance. Random forest and GDBC is included to account for their superior performance in non-active learning based machine learning scenario. 
### Sampling methods for active learning
This project, additionally, compares the performance with multiple AL sampling strategies (e.g. random sampling, sampling based on entropy, sampling based on minimised standard deviation and margin sampling. Furthermore, the number of sampled data per iteration from validation set to the training set for labelling is also trialed from 10 to 250 to investigate its effect on AL performance. 
## Experiment motivation
The motivation of benchmarking AL with these variations is due to the fact that AL is a semi-supervised learning algorithm. The optimisation of learning model and the appropriate decision on hyper parameters i.e. resource management decision could effectively improve AL performance, which the latter is often criticised of being performance-insufficient (e.g. classification rate).
## Building baseline
It is known that AL performance has its ceiling - the classification rate of AL based on a classifier will always be slightly/significantly lower than the same classifier’s performance without applying to the AL algorithm. Therefore, the stand-alone performance of each ML algorithm is measured in terms of the classification rate. 

![alt text](https://github.com/WenxuanHuang/ML-for-COVID-19-dataset/blob/a8b9a8a95e08022f73a8ee4f41fd8fa4fc890d64/Graphs/ML_result.jpeg?raw=true)
Figure 1. Performance comparison on the Area under the Learning Curve for each stand-alone classifier

At current stage, only one dataset has been used to evaluate the performance. It is a real-world dataset that measure the COVID19 swab tests against the routine blood test of 1736 entries. It has 31 regular blood test features that can be potentially trained to predict COVID19 outcomes. Each data entries has been imputed by deep-learning based imputer to prevent negative impact of results by missing feature values. Before training, feature reduction is concluded with a custom RFE (recursive feature elimination) process. 

The Area under the curve (AUC) of ROC curve for each classifier indicates their classification rates respectively. Therefore, higher AUC suggests higher classifier performance. Without employing Active Learning algorithm, random forest have the best performance, reaching an accuracy of 0.88 based on the probability for correctly predicting the COVID19 outcome. 

## Results
Now, a AL module is employed on top of the standalone ML classifiers. The module features a renewed normalisation function that enables repeated normalisation (and the inver of it) for each different hyper-parameter changes. There is also a function that use different sampling method to select k entires for iterative training in AL algorithm. The result is obtained as below.

![alt text](https://github.com/WenxuanHuang/ML-for-COVID-19-dataset/blob/5e0ca3ba53f07d9d0def71860c0c2fda1876c03f/Graphs/AL_result.png?raw=true)
Figure 2. Performance comparison on the Area under the Learning Curve for active learning with each classifier, sampling algorithm and number of ‘k’s

This result indicates, however, that logistic regression with AL has the best performance (over 0.82 in terms of AUC score, given an optimal sampling algorithm and number of ‘k’) compared to all other ML classifiers.

## What's next
The next step is to investigate how logistic regression can contribute to a better AL result, comparing to the benchmark of other ML classifiers. 

- Immediacy on outputting posterior probability estimation with binary-class target?
- Loss function AL is robust on top of logistic regression?
- Data agnostic nature of logistic regression?

Additionally, I want to explore how to further improve the performance of Logia-based AL algorithm (could be in discussion). 

- Evaluation of starting objects (initially labeled objects)
- When maximum likelihood is not reliable (unbalanced datasets, sparse datasets), exchange the inference method to Monte Carlo based alternative?
- Maybe add more manual guidance to the AL algorithm? (e.g. If an entry is falsely labeled and being selected by AL for training, it will be rejected and return to the unlabelled sample pool) 

Lastly, I want to explore whether there are better sampling method that is suitable towards this dataset alone, and datas that rely on binary class for prediction. 
