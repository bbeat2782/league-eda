# league-eda
This is a project for DSC80 at UCSD


## Introduction and Question Identification

Provide an introduction to your dataset, and clearly state the one question your analysis is centered around. Why should readers of your website care about the dataset and your question specifically? Report the number of rows in the dataset, the names of the columns that are relevant to your question, and descriptions of those relevant columns.


## Data Cleaning

Describe, in detail, the data cleaning steps you took and how they affected your analyses. The steps should be explained in reference to the data generating process. Show the head of your cleaned DataFrame


## Univariate Analysis

Embed at least one plotly plot you created in your notebook that displays the distribution of a single column (see Part 2: Report for instructions). Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present.


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
