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

## Update 3/7/2019

### Changes from last session:
currently working on 4-improve-results.ipynb
looked  at work from https://github.com/MichiganDataScienceTeam/undevgoals on the project
learnings: 
- they replace missing values with mean (or other)
- they drop years only if they cannot be filled (rather than drop the 20 years like we do)
- used pycountry to get continent for each series
- did little preprocessing and focused on comparing statut quo (previous value) vs ARIMA vs VAR with different configurations

started looking at other forecasting models: ARIMA, VAR
https://www.datascience.com/blog/time-series-forecasting-machine-learning-differences
https://en.m.wikipedia.org/wiki/Vector_autoregression
https://www.statsmodels.org/dev/vector_ar.html#var

We discovered that VAR helps with multivariate analysis (analyse the lagging within series and between themselves).

We tried fitting the VAR model but ran out of time


### Next steps

- fit VAR model on submission data. Run predictions with similar preprocessing from before. Evaluate and compare with linear regression using polynomial features
- apply learnings above

### What we have learned so far
* We can problem frame this as a regression problem. Given N years of data for a metric, predict next year

* The series name and series code are perfectly correlated, we can drop the series name with no loss of data
* The series codes show a hierarchy and we can use sub codes to filter series by common goal

* The first column in the training and submission sets is a row ID that we can use to join the two datasets
* If we consider only the joined dataset then we have a much higher proportion of year data for series than the dataset as a whole. We also only need to predict values for 737 series/country combinations out of the 195402 present in the training set.

* by applying linear regression to our series, we can already get some reasonable results for some indicators. 
