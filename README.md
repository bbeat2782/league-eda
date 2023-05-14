# league-eda
This is a project for DSC80 at UCSD

## Introduction and Question Identification

Introduction: 

Question: I personally have harder time playing on the Red side (Upper right) than on the Blue side (Lower left) because of the difference in the spot on a minotor you should focus on. Will this be true for others? To test this statistically, does the side have an effect on difference in golds of each side at 10 minutes and 15 minutes since a game starts?

Why should care about the dataset and the question?:

Num of rows: 149,400 rows

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

| gameid                | result   | side   |   golddiffat10 |   golddiffat15 |   csdiffat10 |   csdiffat15 |
|:----------------------|:---------|:-------|---------------:|---------------:|-------------:|-------------:|
| ESPORTSTMNT01_2690210 | False    | Blue   |           1523 |            107 |           -8 |          -23 |
| ESPORTSTMNT01_2690210 | True     | Red    |          -1523 |           -107 |            8 |           23 |
| ESPORTSTMNT01_2690219 | False    | Blue   |          -1619 |          -1763 |          -27 |          -22 |
| ESPORTSTMNT01_2690219 | True     | Red    |           1619 |           1763 |           27 |           22 |
| 8401-8401_game_1      | True     | Blue   |            nan |            nan |          nan |          nan |

(Describe, in detail, the data cleaning steps you took and how they affected your analyses. The steps should be explained in reference to the data generating process. Show the head of your cleaned DataFrame)

There are bunch of columns that we don't need --> select only a few of them that are necessary for our analysis --> result column is consisted of 0 and 1 --> turn this into False and True

we aren't comparing specific position. thus, only need to look at team (raw data has rows for all 10 players and 2 teams per each game) --> only selected position == 'team'

## Univariate Analysis

<iframe src="assets/golddiffat10_univariate_dist.html" width=800 height=600 frameBorder=0></iframe>

1-2 sentence explanation about the plot (describe and interpret any trends): normally distributed centered at 0, goes as high as about 9000 and low as about -9000

## Bivariate Analysis

<iframe src="assets/golddiffat10_side_bivariate_dist.html" width=800 height=600 frameBorder=0></iframe>

1-2 sentence explanation about the plot (describe and interpret any trends): both Blue and Red are centered around 0 but Blue's median is slightly right of 0 and Red's median is slightly left of 0. Several outliers exist in both Blue and Red. 50% of data points is within -1,000, and 1,000

<iframe src="assets/golddiffat15_dist_by_hist.html" width=800 height=600 frameBorder=0></iframe>

## Interesting Aggregates

| result   |     Blue |      Red |
|:---------|---------:|---------:|
| Lose     | -632.109 | -743.577 |
| Win      |  743.716 |  632.499 |

explain its significance: 

## NMAR Analysis

State whether you believe there is a column in your dataset that is NMAR. Explain your reasoning and any additional data you might want to obtain that could explain the missingness (thereby making it MAR). Make sure to explicitly use the term “NMAR.”

## Missingness Dependency

Present and interpret the results of your missingness permutation tests with respect to your data and question. Embed a plotly plot related to your missingness exploration; ideas include:
• The distribution of column Y when column X is missing and the distribution of column Y when column X is not missing, as was done in Lecture 12.
• The empirical distribution of the test statistic used in one of your permutation tests, along with the observed statistic.

<iframe src="assets/TVD_height0.14.html" width=800 height=600 frameBorder=0></iframe>

<iframe src="assets/TVD_height0.2.html" width=800 height=600 frameBorder=0></iframe>

## Hypothesis Testing

Null hypothesis : Two sides (Blue and Red) should have about the same gold at 10 minutes since a game starts --> golddiffat10 (goldat10 - opp_goldat10) should have a mean of 0.

Alternative hypothesis : Blue side has more goldat10 --> golddiffat10's mean is larger than 0.

test statistic : mean

significance level : 0.01

<iframe src="assets/Mean_height0.08.html" width=800 height=600 frameBorder=0></iframe>

resulting p-value : 0.0

conclusion : Since p-value (0.0) is less than <0.05, we reject the null hypothesis --> this suggests that the Blue side has more goldat10 than the Red side

Justify why these choices are good choices for answering the question you are trying to answer:

