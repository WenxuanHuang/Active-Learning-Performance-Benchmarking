# ML-for-COVID-19-dataset
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
![alt text](https://github.com/[username]/[reponame]/blob/[branch]/image.jpg?raw=true)
