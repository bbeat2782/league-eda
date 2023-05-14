# league-eda
This is a project for DSC80 at UCSD

## Introduction and Question Identification

Introduction: 

Question: I personally have harder time playing on the Red side (Upper right) than on the Blue side (Lower left) because of the difference in the spot on a minotor you should focus on. Will this be true for others? To test this statistically, does the side have an effect on difference in golds of each side at 10 minutes and 15 minutes since a game starts?

Why should care about the dataset and the question?:

Num of rows: 149400 rows

names of the columns that are relevant: gameid, result, side, golddiffat10, golddiffat15, csdiffat10, csdiffat15

descriptions of the relevant columns:
- gameid: unique id for each game
- result: whether a team win or not, 0 for lose and 1 for win
- side: blue or red, blue for lower left and red for upper right
- golddiffat10: goldat10 - opp_goldat10, self - opponent goldat10, 10 minutes since game start
- golddiffat15: same as above but 15 minutes
- csdiffat10: csat10 - opp_csat10, same idea as above but with cs (number of minions killed)
- csdiffat15: same as above


## Data Cleaning

(Describe, in detail, the data cleaning steps you took and how they affected your analyses. The steps should be explained in reference to the data generating process. Show the head of your cleaned DataFrame)

There are bunch of columns that we don't need --> select only a few of them that are necessary for our analysis --> result column is consisted of 0 and 1 --> turn this into False and True

we aren't comparing specific position. thus, only need to look at team (raw data has rows for all 10 players and 2 teams per each game) --> only selected position == 'team'

## Univariate Analysis

Embed at least one plotly plot you created in your notebook that displays the distribution of a single column (see Part 2: Report for instructions). Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present.

<iframe src="assets/golddiffat10_univariate_dist.html" width=800 height=600 frameBorder=0></iframe>

## Bivariate Analysis

Embed at least one plotly plot that displays the relationship between two columns. Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present.

## Interesting Aggregates

Embed at least one grouped table or pivot table in your website and explain its significance.

## NMAR Analysis

State whether you believe there is a column in your dataset that is NMAR. Explain your reasoning and any additional data you might want to obtain that could explain the missingness (thereby making it MAR). Make sure to explicitly use the term “NMAR.”

## Missingness Dependency

Present and interpret the results of your missingness permutation tests with respect to your data and question. Embed a plotly plot related to your missingness exploration; ideas include:
• The distribution of column Y when column X is missing and the distribution of column Y when column X is not missing, as was done in Lecture 12.
• The empirical distribution of the test statistic used in one of your permutation tests, along with the observed statistic.

## Hypothesis Testing

Clearly state your null and alternative hypotheses, your choice of test statistic and significance level, the resulting p-value, and your conclusion. Justify why these choices are good choices for answering the question you are trying to answer.

Tip: When making writing your conclusions to the statistical tests in this project, never use language that implies an absolute conclusion; since we are performing statistical tests and not randomized controlled trials, we cannot prove that either hypothesis is 100% true or false.
