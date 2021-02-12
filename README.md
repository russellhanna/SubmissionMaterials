ProjectOneAMLcompute

Optimizing an ML Pipeline in Azure
Overview
This project is part of the Udacity Azure ML Nanodegree. In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model. This model is then compared to an Azure AutoML run.

Summary
In this project, we are given a dataset containing bank customers and the services they buy. The prediction task is to identify which customers buy the target service. We trained two models. The first model used an estimator from the Scikit Learn library (Hyperdrive), while the second model used automated machine learning (AutoML) which in turn runs several prediction methods. We compared the best performing models produced by each method and found that the AutoML trials produced the better model. The Hyperdrive training produced an accuracy of just above 90%, while the AutoML model produced several variations scoring above 91%.

Scikit-learn Pipeline
The Hyperdrive library makes several trials of different sample sizes to find correlation "fit" between the input parameters and the dependent variable, logging the results. The algorithm randomizes sample sizes and selections. By randomizing the parameters of each trial, and using the entire range of inputs, we find the "best fit" predictors, while avoiding the problem of optimizing the model too closely ("overfitting") to the training data and any biases or outliers that might make the available data unlike the "real world" data with which the model will be deployed. To avoid spending money and energy on trials that will not produce a "best" model, each trial that does not converge to the "best" solution is stopped early. This early stopping logic is called "early stopping policy" and we implemented the Bandit policy. This mix of "test everything at random" with "stop underperforming trials" makes a reasonable trade-off between cost of experiments and accuracy of the resulting model.

AutoML
Because the process of correlating inputs to an output is well known, as shown in the scikit learn example above, we can program the computer to attempt any or all of many different modeling approaches, along with randomly selecting input parameters and training data. Thus, in the time it takes to run exhaustive testing of a handful of correlation trials, we can test many different correlation algorithms and choose the best approach, rather than just the best run of a single approach.

Pipeline comparison
Both scikit learn and automl automate the process of computing statistical outcomes (predictions) from sets of inputs. Scikit was developed to run a specific set of computations. More recently, AutoML was designed -- in effect -- to run a large set of algorithms like scikit learn. AutoML automates an additional layer of complexity, when compared with scikit learn. As a result of its wider range of experimental models, AutoML outperformed scikit learn in this project. Given the simplicity of "try it all" with AutoML, and the tendency to overfit any one model by attempting to "refine" its predictions, the cost/benefit ratio for AutoML is clearly better.

Future work
In follow-up modeling efforts, assuming the same prediction targets and levels of automation, we will explore the different divisions within the bank products themselves, as possible areas for correlation. For example, are the customers for each of the different maturities of savings the same, or are longer maturities associated with a different "sub-group" of customers than are short maturities? Does the size of the savings matter, when maturities are sub-grouped? What other products do these customers have? Starting with the bank's most profitable customers, if that analysis has not been done, how are savings products correlated with the profit drivers for the bank? For example, if some customers have investment management accounts, can we see if their cash and "near-cash" saving vehicles are a matched set with their underlying investment strategy? Can we ask their service reps for insight into how their customers make decisions and what "outside services" such customers might move into our bank if the offer was compelling?

Proof of cluster clean up
Please see the screen shot included in this repo. Oddly, I don't see how to paste it into this readme.
