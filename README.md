# time-series-millenium-goals
Analyse a dataset showing progress towards the United Nations development goals and predict 1 year and 5 years into the future

Project details:
https://www.drivendata.org/competitions/1/united-nations-millennium-development-goals

There are two files in the dataset
* training data which gives the values of particular metrics (AKA series) for a given country for the years 1972-2007 (many have years missing)
* submission data which gives us the row IDs we need to predict one year (2008) and five years (2012) into the future

### Retrieve data
The data directory is ignored by git and you need to retrieve manually the resources:

- Extract the contents of this zip file into the data/ subdirectory: 
https://s3.amazonaws.com/drivendata/data/1/public/cd238763-ed29-4a46-8584-f9334d57ec94.zip you should have data/TrainingSet.csv

- download this file and put it in data/ folder: 
https://s3.amazonaws.com/drivendata/data/1/public/SubmissionRows.csv

- You will need as well to put this file in the data/ folder: 
https://gist.githubusercontent.com/pamelafox/986163/raw/f5f9db4f1b287804fd07ffb3296ed0036292bc7a/countryinfo.py


## Update 9/10/2019

### Changes from last session:
work on Linear_Regression_Model notebook
used work on linear regression with polynomial features from Tiri as baseline
evaluate and plot correlated indicators using tutorial from http://drivendata.co/blog/world-bank-getting-started/

### Next session
retrain our linear model using correlated indicators


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
