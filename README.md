
# tweetstats

<!-- badges: start -->
<!-- badges: end -->

The goal of tweetstats is to improve accessibility of Twitter analyses for the 
average R user through two functions; keystats and userstats. The former analyzes 
user-specified keywords and hashtags, returning an HTML ouput with various 
summary graphics while the latter analyzes the pages of user-specified Twitter 
users, returning an HTML output with account summary information as well as 
the user-specified number of most recent tweets.

## Installation

You can install the released version of tweetstats from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("tweetstats")
```

## Example

This is a basic example which shows you how to use each of the functions:

``` r
library(tweetstats)
## keystats("data science", n=1000, top_num = 20)
## userstats(c("taylorswift13","katyperry"), 1000, year = 2019, x=5)
```

