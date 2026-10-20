# DSCI 552 — Homework 4

Name : Mohammad Ayaan Khan

USC ID: 4147952900

Email ID : [mkhan736@usc.edu](mailto:mkhan736@usc.edu)

Time series classification on the AReM dataset (feature creation and extraction, binary and multiclass classification), plus ISLR exercises 4.8.3 and 4.8.7.

## Contents

`Homework4.ipynb` — The solution involves the entire process of feature creation from Homework 3, followed by binary and multiclass classification. It involves downloading the AReM dataset, applying the prescribed training/testing split, extracting seven respective time-domain features (minimum, maximum, mean, median, standard deviation, first quartile, third quartile) from each of the six sensor series, determining the standard deviation for each of the features with a 90% bootstrapping confidence interval, and choosing three features. It then breaks each time series into l pieces and classifies bending vs. other activities using logistic regression with recursive feature elimination, case-control sampling, and L1-penalized logistic regression, and classifies all seven activities using L1-penalized multinomial logistic regression, Gaussian Naive Bayes, and Multinomial Naive Bayes, together with the answers to questions ISLR 4.8.3 and 4.8.7.

## How to run

1. Install the dependencies: `pip install -r requirements.txt`
2. Open the notebook and run cells: `jupyter notebook Homework4.ipynb`

The notebook downloads the AReM dataset from the UCI repository automatically. Therefore there is no need to download any data files, but it is necessary to have an Internet connection.

Running all cells takes about 8 minutes, most of which is spent on the cross-validation searches over l.

## Notes

- The prescribed data split implies that datasets 1-2 are stored in `bending1` / `bending2` and datasets 1-3 are retained in other folders as test data, and thus, we get 19 as test data and 69 as training instances out of 88.
- The notebook stops in case it does not load precisely 88 data instances, and it flags any data file that does not have 480 valid sensor rows.
- All model choices (l, p, and C) are made using stratified 5-fold cross-validation on the training data only. The test data is used once, to evaluate the final models.
