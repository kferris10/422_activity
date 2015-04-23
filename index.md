---
title       : Homework 8
subtitle    : Problem 2
author      : Stat 422
today       : "Monday, April 20"
framework   : bootstrap3
highlighter : highlight.js 
hitheme     : github      
widgets     : [mathjax, quiz, bootstrap]
layout      : deck3
mode        : selfcontained 
knit        : slidify::knit2slides
assets      : 
  css       : 
    - "libraries/frameworks/bootstrap3/css/custom.css"
    - "libraries/frameworks/bootstrap3/css/moving_sidebar.css"
    - "http://fonts.googleapis.com/css?family=Vollkorn"
    - "http://fonts.googleapis.com/css?family=Droid%20Sans%20Mono"
github:
  website: "https://github.com/kferris10/422_activity"
---



# Introduction

This is designed to help with problem 2 of Homework 8.  To start, you'll need to know that the MLE of a Gamma distribution is $\hat{\beta} = \frac{\bar{X}}{\alpha}$ (you'll have to show this when you write up the homework).

--- &radio
# Likelihood Under the Null

What is the likelihood under the null hypothesis?  (Minor note, the submit button doesn't work for this problem, but you should get the second answer).

1. \( \frac{1}{\Gamma(\alpha)^n \beta_0^{n\alpha}} \prod_{i = 1}^{n} x_i^{\alpha-1} exp(- \sum_{i = 1}^{n} x_i / \hat{\beta}) \)
2. \( \frac{1}{\Gamma(\alpha)^n \hat{\beta}^{n\alpha}} \prod_{i = 1}^{n} x_i^{\alpha-1} exp(- \sum_{i = 1}^{n} x_i / \hat{\beta}) \)
3. \( \frac{1}{\Gamma(\alpha)^n \beta_0^{n\alpha}} \prod_{i = 1}^{n} x_i^{\alpha-1} exp(- \sum_{i = 1}^{n} x_i / \beta_0) \)

*** .hint
Recall that there is only one possible value of $\beta$ under the null.

*** .explanation
Under the null, you just plug in $\beta_0$ for $\beta$ in the likelihood.

--- &submitcompare1
# Maximized Likelihood Under the Alternative

What is the likelihood under the alternative

*** .explanation
Here, we just plug in $\hat{\beta}$ for $\beta$ in the likelihood.  So...

\(sup(all \, \beta) L(\beta | \textbf{x}, \alpha) =  \frac{1}{\Gamma(\alpha)^n \hat{\beta}^{n\alpha}} \prod_{i = 1}^{n} x_i^{\alpha-1} exp(\sum_{i = 1}^{n} x_i / \hat{\beta}) \)

---
# Likelihood Ratio Test

Find the ratio of these two, showing that it is equal to 

\( \lambda(x) = (\frac{\hat{\beta}}{\beta_0})^{n\alpha} \times exp(-\sum_{i=1}^{n} x_i * (\frac{1}{\beta_0} - \frac{1}{\hat{\beta}})) \)

This will be our test statistic.

--- &submitcompare1
# Large Sample Results

If we take a certain transformation of this test statistic, there is a very useful large sample result that we can appeal.  In words, what is the appropriate transformation?

*** .explanation
Multiply the natural log of the test statistic by -2.

--- &radio
# LRT Distribution

For a large sample, what distribution does this test statistic follow?

1. Normal
2. _Chi-Squared_
3. t
4. F

*** .hint
What happens to LRTs as $n \rightarrow \inf$?

*** .explanation
See Theorem (whatever Theorem it is)

--- &multitext
# LRT Distribution for Part (b)

1. How many degrees of freedom does this distribution have?

*** .hint
How many constraints are there in your hypotheses?

*** .explanation
1. <span class = "answer">1</span>
There is one additional constraint in the null.

--- &radio
# Part (b) Null Hypothesis

What is the appropriate null hypothesis?

1. $\beta = 5$
2. $\alpha = 5$
3. $\beta = 44$
4. _$\beta = 12.2$_

*** .hint
Um...

*** .explanation
They assumed that $\beta = 12.2$ 

--- &multitext
# The test statistic

1. What is $\bar{X}$?
2. What is $\hat{\beta}$?
3. What is the value of $\lambda (X)$?  Round to four decimal places
4. What is the value of the test statistic (i.e. $-2 * log(\lambda (X))$)?  Round to two decimal places.

*** .hint
Now, we are just plugging in values from the problem into the statistics that we have derived.

*** .explanation
1. <span class = "answer">44</span>
$\bar{x}$ is the average rainfall
2. <span class = "answer">8.8</span>
$\hat{\beta} = \bar{x} / \alpha$
3. <span class = "answer">0.0133</span>
Plug in $\hat{\beta}$, $\beta_0$, and $\alpha$ into the formula for $\lambda (X)$ from before.
4. <span class = "answer">8.64</span>
$-2 * log(0.013)$

--- &submitcompare1
# Obtaining a p-value

A $\chi^2(1)$ distribution is plotted below.  Explain how you would find a p-value.


```r
library(ggplot2)
test_stats <- seq(.01, 10, by = .01)
densities <- dchisq(test_stats, 1)
qplot(x = test_stats, ymax = densities, ymin = 0, geom = "ribbon") + 
  geom_ribbon(fill = "lightgrey", colour = "darkgreen") + 
  theme_bw() + 
  labs(x = "Test Statistic", y = "Density")
```

<img src="assets/fig/chisq1-1.png" title="plot of chunk chisq1" alt="plot of chunk chisq1" style="display: block; margin: auto;" />

*** .explanation
Find the probability of observing a value of the $chi^2(1)$ distribution greater than 0.202 (our observed test statistic).











