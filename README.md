# time-series-millenium-goals
Analyse a dataset showing progress towards the United Nations development goals and predict 1 year and 5 years into the future

Project details:
https://www.drivendata.org/competitions/1/united-nations-millennium-development-goals

There are five notebooks corresponding to the stages described in https://machinelearningmastery.com/process-for-working-through-machine-learning-problems/

* 1-define-the-problem.ipynb
* 2-prepare-data.ipynb 
* 3-spot-check-algorithms.ipynb
* 4-improve-results.ipynb
* 5-present-results.ipynb

There are two files in the dataset
* training data which gives the values of particular metrics (AKA series) for a given country for the years 1972-2007 (many have years missing)
* submission data which gives us the row IDs we need to predict one year (2008) and five years (2012) into the future

## Update 4/9/2019

### Changes from last session:
currently working on 4-improve-results.ipynb
looked  at work from https://machinelearningmastery.com/multivariate-time-series-forecasting-lstms-keras/
- started applying to our project but got lost :).

### Next steps

- run tutorial together from https://machinelearningmastery.com/multivariate-time-series-forecasting-lstms-keras/
- carry on applying after better understanding how it all works

### Homework

- go through https://machinelearningmastery.com/convert-time-series-supervised-learning-problem-python/ to understand how the data are prepared


### What we have learned so far
* We can problem frame this as a regression problem. Given N years of data for a metric, predict next year

* The series name and series code are perfectly correlated, we can drop the series name with no loss of data
* The series codes show a hierarchy and we can use sub codes to filter series by common goal

* The first column in the training and submission sets is a row ID that we can use to join the two datasets
* If we consider only the joined dataset then we have a much higher proportion of year data for series than the dataset as a whole. We also only need to predict values for 737 series/country combinations out of the 195402 present in the training set.

* by applying linear regression to our series, we can already get some reasonable results for some indicators. 
