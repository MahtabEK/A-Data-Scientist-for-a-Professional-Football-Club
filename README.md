# A-Data-Scientist-for-a-Professional-Football-Club-Part1
In this project, you work as a Data Scientist for a professional football club. The owner of the team is very interested in seeing how the use of data can help improve the team's peformance, and perhaps win them a championship!  The draft is coming up soon (thats when you get to pick new players for your team), and the owner wants you to create a model to help score potential draftees. The model will look at attributes about the player and predict what their "rating" will be once they start playing professionally.  The football club's data team has provided the data for 17,993 footballers from the league. Our job is to build a model or models, perform model selection, and make predictions on players you we have not yet seen.

The Dataset
The data is stored in a csv file called footballer_data.csv. The data contain 52 columns, including some information about the player, their skills, and their overall measure as an effective footballer.

Most features relate to the player's abilities in football related skills, such as passing, shooting, dribbling, etc. Some features are rated on a 1-5 scale (5 being the best), others are rated on 0-100 (100 being the best), and others still are categorical (e.g. work rate is coded as low, medium, or high).

The target variable (or  𝑦  variable, if you will) is overall. This is an overall measure of the footballer's skill and is rated from 0 to 100. The most amazingly skilled footballer would be rated 100. The model(s) will use the other features to predict overall.


**Part 1**

Here, I just read in the data and take a look at the dataframe.There are 52 columns. The outcome of interest is called overall which gives an overall measure of player performance. Not all of the other columns are particularly useful for modelling though (for instance, ID is just a unique identifier for the player. This is essentially an arbitrary number and has no bearing on the player's rating).

To clean the data, first, I remove these columns:

ID
club
club_logo
birth_date
flag
nationality
photo
potential


And then I convert these columns into dummy variables:

work_rate_att
work_rate_def
preferred_foot


**Part 2:**

The data is all numerical now. Before I begin modelling, it is important to obtain a baseline for the accuracy of my predictive models. I compute the absolute errors resulting if I use the median of the overall variable to make predictions. This will serve as my baseline performance. Here, I plot the distribution of the errors and print their mean and standard deviation.


**Part 3:**

To prepare the data for modelling, I use sklearn.model_selection.train_test_split to seperate the data into a training set and a test set. I would like to estimate the performance of the final selected model to within +/- 0.25 units using mean absolute error as the loss function of choice. So the appropriate size for the test set is 1163.

**Part 4:**

I fit a linear regression to the data as a first model. I used sklearn to build a model pipeline which fits a linear regression to the data. (This is a simple, one-step pipeline that I will expand later).

**Part 5:**

I use 5 fold cross validation to estimate the out of sample performance for this model. To do it, I used sklearn's cross_val_score.

**Part 6:**

As we can see, my model seems to be pretty accurate, but lets make it more accurate. Scouts have shared with us that players hit their prime in their late 20s, and as they age they become worse overall.

So we want to add a quadratic term for age to the model. Here, I repeat the steps above (creating a pipeline, validating the model, etc) for a model which includes a quadratic term for age.

**Part 7:**

The quadratic term didn't improve the fit of the model much so we want to try to include quadratic and interaction term for every feature (That's a total of 1080 features!!!!)

Here, I add sklearn's PolynomialFeatures to the pipeline from Part 3. The cross validation score is reported.

**Part 8:**

Here is a question. Do you think adding third order interactions (that is adding cubic terms to the model) is a good idea?
You can check out the answer in my java notebook provided: "A Data Scientist for a Professional Football Club.ipynb"

**Part 9:**

Based on the cross validation scores, which model do you think is better to choose? In this section, I estimate the performance of my chosen model on the test data and then I do the following:

- I compute a point estimate for the generalization error.
- I compute a confidence interval for the generalization error.
- I plot the distribution of the absolute errors.

Here is a question for you:
Is the test error close to the cross validation error of the model I chose? Why?

You can check out the answer to this question in in my java notebook: "A Data Scientist for a Professional Football Club.ipynb"
