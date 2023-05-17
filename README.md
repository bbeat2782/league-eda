# league-eda
This is a project for DSC80 at UCSD

## Introduction and Question Identification

### Introduction :video_game: : 
This dataset contains 2022 professional leagues matches. For each game, there are 10 rows representing 10 players and 2 rows representing 2 teams. And there are various columns for statistic of each game such as goldat10, dragon, assistsat10, etc.

### Question: 
I personally have harder time playing on the Red side (upper right) than on the Blue side (lower left) because of the difference in perspective. Will this be true for professional players? To test this statistically, does the side have an effect on difference in golds of each side at 10 minutes since a game starts?

### Why should you care about the question?
It is because side shouldn't affect fairness of a game by resulting difference in gold amount.

### Num of rows
149,400 rows

### Relevant columns: 
gameid, result, side, golddiffat10, golddiffat15

### Descriptions of each column:
- gameid: unique id for each game
- result: whether a team win or not, 0 for lose and 1 for win
- side: blue or red, blue for lower left and red for upper right
- golddiffat10: goldat10 - opp_goldat10 (=self - opponent goldat10), 10 signifies 10 minutes since game starts
- golddiffat15: same as above but 15 minutes since game starts

## Cleaning and EDA

### Data Cleaning

| gameid                | result   | side   |   golddiffat10 |   golddiffat15 |
|:----------------------|:---------|:-------|---------------:|---------------:|
| ESPORTSTMNT01_2690210 | False    | Blue   |           1523 |            107 |
| ESPORTSTMNT01_2690210 | True     | Red    |          -1523 |           -107 |
| ESPORTSTMNT01_2690219 | False    | Blue   |          -1619 |          -1763 |
| ESPORTSTMNT01_2690219 | True     | Red    |           1619 |           1763 |
| 8401-8401_game_1      | True     | Blue   |            nan |            nan |

1. Since each game is represented with 12 rows (10 players and 2 teams), we dropped players rows to avoid double counting.

2. Since all statistics from each game are recorded but we are only interested in gameid, result, side, golddiffat10, and golddiffat15, we only selected these columns.

3. For result column, entries are either 0 for lose and 1 for win. We turned each 0 and 1 to False and True because ~~

### Univariate Analysis

<iframe src="assets/golddiffat10_univariate_dist.html" width=800 height=600 frameBorder=0></iframe>

It is a histogram of golddiffat10, and it's normally distributed and centered at 0. It goes up to 9000 and low to -9000. 

### Bivariate Analysis

<iframe src="assets/golddiffat10_side_bivariate_dist.html" width=800 height=600 frameBorder=0></iframe>

The plot contains two boxplots of golddiffat10 by Blue and Red team. Both are approximately centered at 0. However, Blue team's median is slightly right of 0, whereas Red team's median is slightly left of 0. Several outliers exist in both Blue and Red team, but Blue team's outliers are skewed more to the right than Red team's. 50% of data points are within -1,000 and 1,000.

### Interesting Aggregates

`team_lol.pivot_table(index='result', columns='side', values=feature, aggfunc='mean')`

| result   |     Blue |      Red |
|:---------|---------:|---------:|
| Lose     | -632.109 | -743.577 |
| Win      |  743.716 |  632.499 |

#### Significance: 
If side does not affect golddiffat10, ith entry of two columns should be similar. But since they are not, it shows there might be a possibility that side affects golddiffat10.

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