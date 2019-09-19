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

+ last experiments in LSTM_EXPERIMENTS folder

There are two files in the dataset
* training data which gives the values of particular metrics (AKA series) for a given country for the years 1972-2007 (many have years missing)
* submission data which gives us the row IDs we need to predict one year (2008) and five years (2012) into the future

## Update 18/9/2019

### Changes from last session:
showcase from Tiri on his work based on https://machinelearningmastery.com/how-to-develop-lstm-models-for-time-series-forecasting/ and further discussions
preprocessing + built LSTM model with multivariate forecasting 

### Next steps

- run tutorial together from https://machinelearningmastery.com/multivariate-time-series-forecasting-lstms-keras/
- carry on applying after better understanding how it all works


### Homework

run 2 notebooks from LSTM_EXPERIMENTS folder to prepare the data and train the model
pick a topic for improvement below, have a go, showcase next time in 10min max
Compare results before after improvement by checking against last 5 years during training + submitting to united nations website (edited) 

#### Topics for improvement:
improve cleaning/filtering of the data
- try on everything
- Feature selection not based on correlations

Improve the preparation of the data:
- features engineering
- use polynomial features in the interpolation of the data
- find a way to use continents/countries
- features reduction: PCA

improve model training:
- add dropout
- change architecture
- predict 1 year from 5 years instead of 5 from 5 (and predict 1 year at a time 2002 to 2007, using predictions)



### What we have learned so far
* We can problem frame this as a regression problem. Given N years of data for a metric, predict next year

* The series name and series code are perfectly correlated, we can drop the series name with no loss of data
* The series codes show a hierarchy and we can use sub codes to filter series by common goal

* The first column in the training and submission sets is a row ID that we can use to join the two datasets
* If we consider only the joined dataset then we have a much higher proportion of year data for series than the dataset as a whole. We also only need to predict values for 737 series/country combinations out of the 195402 present in the training set.

* by applying linear regression to our series, we can already get some reasonable results for some indicators. 
