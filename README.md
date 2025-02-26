# STAT 5255 (Introduction to Data Science)
Author: Tong Shen

### Repository Overview
This repository documents my responses to the assignments for the STAT 5255 class (Introduction to Data Science). 

The first two excercies focused on GitHub setup and thus do not contain recorded responses.

Exercises 5, 6, and 7 used the NYC motor vehicle collisions dataset from NYC Open Data. 

The mid-term team project utilized the 311 Service Requests dataset from NYC Open Data. In this project, my teammate answered the first two questions (cleaning the data and describing the duration distribution), while I handled the last two: building models to predict a variable and exploring the data to answer the research question of interest—how to find a neighbor-friendly house in NYC.

The final project used data I collected independently and aimed to answer two key research questions:

Research Question 1: How accurately and effectively can a comprehensive set of predictors (demographic information, relationship specific predictors, and family of origin experiences) predict adult attachment security?

Research Question 2: What are the key predictors of adult attachment security?

### Prompts 

1. Pick up Git basics and set up an account at GitHub if you don't have
   one. Please practice the tips on Git in the notes. Make sure you have at
   least 10 commits in the repo, each with informative message. Keep checking
   the status of your repo with `git status`. My grader will grade the repo.
    1. Clone the `ids-s23` repo to your own computer.
    1. Add your name and wishes to the Wishlist; commit with an informative message.
	1. Remove the `Last, First` entry from the list; commit.
	1. Create a new file called `add.qmd` containing a few lines of texts; commit.
	1. Remove `add.qmd` (pretending that this is by accident; commit.
    1. Recover the accidently removed file `add.qmd`; add a long line (a
       paragraph without a hard break); add a short line (under 80 characters);
       commit.
    1. Change one word in the long line and one word in the short line; use
	`git diff` to see the difference from the last commit; commit.
	1. Put the repo into the GitHub Classroom homework repo with `git remote add` and `git push`.

1. Get ready for contributing to the classnotes.
    1. Create a fork of the `ids-s23` repo into your own GitHub account. 
	1. Clone it to your local computer. 
	1. Make a new branch to experiment with your changes.
	1. Checkout your branch and add your wishes to the wish list; push to your
       GitHub account.
    1. Make a pull request to my `ids-s23` repo from your fork at GitHub. Make
       sure you have clear messages to document the changes.

1. Write a function to demonstrate the Monty Hall problem through
   simulation. The function takes two arguments `ndoors` and
   `ntrials`, representing the number of doors in the experiment and
   the number of trails in a simulation, respectively. The function
   should return the proportion of wins for both the switch and
   no-switch strategy. Apply your function with 3 doors and 5 doors,
   both with 1000 trials. Include sufficient text around the code to explain
   your them.

1. Write a function to do a Monte Carlo approximation of $\pi$. The
   function takes a Monte Carlo sample size `n` as input, and returns
   a point estimate of $\pi$ and a 95% confidence interval. Apply your
   function with sample size 1000, 2000, 4000, and 8000. Repeat the experiment 
   1000 times for each sample size and check the empirical probability that the
   confidence intervals cover the true value of $\pi$. Comment on
   the results.

1. The NYC motor vehicle collisions data with documentation is available from
   [NYC Open
   Data](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95).
   The raw data needs some cleaning. (JY: Add variable name cleaning next year.)
    1. Use the filter from the website to download the crash data of January
       2023; save it under a directory `data` with an informative name
	   (e.g., `nyc_crashes_202301.csv`).
	1. Get basic summaries of each variable: missing percentage; descriptive
       statistics for continuous variables; frequency tables for discrete
       variables.
	1. Are the `LATITUDE` and `LONGITIDE` values all look legitimate? If not
       (e.g., zeroes), code them as missing values.
	1. If `OFF STREET NAME` is not missing, are there any missing `LATITUDE` and
	   `LONGITUDE`? If so, geocode the addresses.
	1. (Optional) Are the missing patterns of `ON STREET NAME` and `LATITUDE` the same?
       Summarize the missing patterns by a cross table. If `ON STREET NAME` and
       `CROSS STREET NAME` are available, use geocoding by intersection to fill
	   the `LATITUDE` and `LONGITUDE`.
	1. Are `ZIP CODE` and `BOROUGH` always missing together? If `LATITUDE` and
       `LONGITUDE` are available, use reverse geocoding to fill the `ZIP CODE`
       and `BOROUGH`.
	1. Print the whole frequency table of
		`CONTRIBUTING FACTOR VEHICLE 1`. 
	   Convert lower cases to uppercases and check the frequencies again.
	1. Provided an opportunity to meet the data provider, what suggestions do
       you have to make the data better based on your data exploration
       experience?

1. Except the first problem, use the cleaned data set with missing geocode
   imputed (`data/nyc_crashes_202301_cleaned.csv`).
    1. Construct a contigency table for missing in geocode (latitude and
       longitude) by borough. Is the missing pattern the same across borough?
       Formulate a hypothesis and test it. 
	1. Construct a `hour` variable with integer values from 0 to 23. Plot the
       histogram of the number of crashes by `hour`. Plot it by borough.
	1. Overlay the locations of the crashes on a map of NYC. The map could be a
       static map or Google map.
	1. Create a new variable `injury` which is one if the number of persons
       injured is 1 or more; and zero otherwise. Construct a cross table for
       `injury` versus borough. Test the null hypothesis that the two variables are
       not associated.
	1. Merge the crash data with the zip code database.
	1. Fit a logistic model with `injury` as the outcome variable and covariates
       that are available in the data or can be engineered from the data. For
       example, zip code level covariates can be obtained by merging with the
       zip code database.
	   
1. Using the cleaned NYC crash data, perform classification of `injury` with
   support vector machine and compare the results with the benchmark from
   regularized logistic regression. Use the last week's data as testing data.
    1. Explain the parameters you used in your fitting for each method.
	2. Explain the confusion matrix retult from each fit.
	3. Compare the performance of the two approaches in terms of accuracy,
       precision, recall, F1-score, and AUC.


1. Mid-term team project: The NYC Open Data of 311 Service Requests contains
   all requests from 2010 to present. We consider a subset of it with request
   time between 00:00:00 01/15/2023 and 24:00:00 01/21/2023. The subset is
   available in CSV format as `data/nyc311_011523-012123_by022023.csv`. Read the
   data dictionary to understand the meaning of the variables,
    1. Clean the data: fill missing fields as much as possible; check for
       obvious data entry errors (e.g., can `Closed Date` be earlier than
       `Created Date`?); summarize your suggestions to the data curator in
       several bullet points.
    1. Remove requests that are not made to NYPD and create a new variable
       `duration`, which represents the time period from the `Crated Date` to
       `Closed Date`. Note that `duration` may be censored for some
       requests. Visualize the distribution of uncensored `duration` by
       weekdays/weekend and by borough, and test whether the distributions are
       the same across weekdays/weekends and across borough.
    1. Build a model to predict the `duration` for 311 requests to get
       closed. If your model has tuning parameters, justify their choices. Apply
       this model to the 311 requests of NYPD in the week of 01/22/2023. Assess
       the performance of your model.
    1. Now you know the data quite well. Come up with a research question of
       interest that can be answered by the data, which could be analytics or
       visualizations. Perform the needed analyses and answer your question.
1. Final Project: The topic will be of your choice. It should show the whole cycle of a real data science project. Consider projects at data science competition sites (e.g.,
https://kaggle.com).

