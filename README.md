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

## Update 22/5/2019

### Changes from last session:
currently working on 2-prepare-data.ipynb
* normalize the data
* Plotting again the top correlated indicators for Afghanisthan between 2000 to 2007
* rework the training and visualisation of the data (to be moved in spot check algos notebook) so that we train on all data until 2002 and then test on 2002 - 2007. Then compare visually true values vs predictions

### Homework
- learn about evaluating accuracy in regression problems. Which metrics should we use ?
- learn about applying polynomial models

### Next steps

* evaluate the accuracy of the model
* We could use a more sophisticated model than linear regression to improve the accuracy of our model (try polynomial for a start ?)
* To predict one indicator, we can maybe use indicators on the similar goal, or the indicators from close countries (can use our continent column that we added). To be confirmed
* Rerun predictions using correlations explored above and see if they improve our results

* find out what to do with missing data. drop them ? fill them ?

### What we have learned so far
* We can problem frame this as a regression problem. Given N years of data for a metric, predict next year

* The series name and series code are perfectly correlated, we can drop the series name with no loss of data
* The series codes show a hierarchy and we can use sub codes to filter series by common goal

* The first column in the training and submission sets is a row ID that we can use to join the two datasets
* If we consider only the joined dataset then we have a much higher proportion of year data for series than the dataset as a whole. We also only need to predict values for 737 series/country combinations out of the 195402 present in the training set.

* by applying linear regression to our series, we can already get some reasonable results for some indicators. 
