# time-series-millenium-goals
Analyse a dataset showing progress towards the United Nations development goals and predict 1 year and 5 years into the future

There are five notebooks corresponding to the stages described in https://machinelearningmastery.com/process-for-working-through-machine-learning-problems/

* 1-define-the-problem.ipynb
* 2-prepare-data.ipynb
* 3-spot-check-algorithms.ipynb
* 4-improve-results.ipynb
* 5-present-results.ipynb

## Update 24/4/2019
There are two files in the dataset

* training data which gives the values of particular metrics (AKA series) for a given country for the years 1972-2007 (many have years missing)
* submission data which gives us the row IDs we need to predict one year (2008) and five years (2012) into the future

What we have learned so far
* The series name and series code are perfectly correlated, we can drop the series name with no loss of data
* The series codes may not be consistent. Some may include a country code and others not. The names of the series also appear to vary between countries. It's likely we'll need to do some work to come up with a consistent set of series code across the dataset.
* The first column in the training and submission sets is a row ID that we can use to join the two datasets
* If we consider only the joined dataset then we have a much higher proportion of year data for series than the dataset as a whole. We also only need to predict values for 737 series/country combinations out of the 195402 present in the training set.
* The 737 desired values may not be enough to train a model so we can't necessarily discard 194665 (195402-737) rows
* We can problem frame this as a regression problem. Given N years of data for a metric, predict next year

Next steps
* Convert year values from columns to rows: Convert 2D table to 3D dataset. This will make it easier to drop empty values
* Prove correlation between series name and series code
* Separate series code and determine whether that correlates with country or is orthogonal
* Work out what data can be dropped
* Try framing as regression problem: how many years do we need?
* Are metrics independent can we train on a metric/country basis or do we need some method for training per metric (aggregate across countries)?
