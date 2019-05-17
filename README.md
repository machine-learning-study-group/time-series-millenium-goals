# time-series-millenium-goals
Analyse a dataset showing progress towards the United Nations development goals and predict 1 year and 5 years into the future

There are five notebooks corresponding to the stages described in https://machinelearningmastery.com/process-for-working-through-machine-learning-problems/

* 1-define-the-problem.ipynb
* 2-prepare-data.ipynb
* 3-spot-check-algorithms.ipynb
* 4-improve-results.ipynb
* 5-present-results.ipynb

There are two files in the dataset
* training data which gives the values of particular metrics (AKA series) for a given country for the years 1972-2007 (many have years missing)
* submission data which gives us the row IDs we need to predict one year (2008) and five years (2012) into the future

## Update 15/5/2019

### Changes from last session:
currently working on 2-prepare-data.ipynb
we have been working on finding correlations between 1 target indicator for a country and other indicators in that same country.
* Plotting one target indicator [Environmental Sustainability (7.8)] for Afghanistan
* Plotting all indicators except Environmental Sustainability (7.8) for Afghanistan
* Plotting all indicators except Environmental Sustainability (7.8) for Afghanistan for 2001 to 2007
* Enlisting top correlated features against target feature [Environmental Sustainability (7.8)]
* Plotting the top correlated indicators for Afghanisthan between 2000 to 2007

### Next steps

* To predict one indicator, we can maybe use indicators on the similar goal, or the indicators from close countries (can use our continent column that we added). To be confirmed
* Improve our model training, by testing it on the training data and evaluating the accuracy of the model
* Rerun predictions using correlations explored above and see if they improve our results
* We could use a more sophisticated model than linear regression to improve the accuracy of our model (try polynomial for a start ?)

* find out what to do with missing data. drop them ? fill them ?

### What we have learned so far
* We can problem frame this as a regression problem. Given N years of data for a metric, predict next year

* The series name and series code are perfectly correlated, we can drop the series name with no loss of data
* The series codes show a hierarchy and we can use sub codes to filter series by common goal

* The first column in the training and submission sets is a row ID that we can use to join the two datasets
* If we consider only the joined dataset then we have a much higher proportion of year data for series than the dataset as a whole. We also only need to predict values for 737 series/country combinations out of the 195402 present in the training set.

* by applying linear regression to our series, we can already get some reasonable results for some indicators. 
