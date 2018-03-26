# template elements
<div class="header"></div>
<div class="footer"></div>
<img src="../images/icjia.png" class="logo"></img>
<img src="../images/il_seal.gif" class="seal"></img>
<div class="buttons">
<a href="../index.html">
  <button type="button">Home</button>
</a>
<a href="../modules.html">
  <button type="button">Modules</button>
</a>
<a href="../notes/module5_notes1.html">
  <button type="button">Notes</button>
</a>
</div>
<link href="https://fonts.googleapis.com/css?family=Oswald" rel="stylesheet">





# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 5: Statistical modeling with R (1)</h3>  
2018-04-11  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
<ul style="list-style: none">
<li style="color: #00061a; font-size: 1.1em; font-weight:700">
  Part 1: Basics of statistical modeling</li>
<li>
  Part 2: Options for advanced modeling</li>
</div>


Basic Descriptive Statistics
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Quick summary stats
========================================================

```r
summary(data)
```
* Base R's `summary()` function is a quick way to get descriptive statistics on each columan of a tabular data object.
    * For numerical columns, we get minimum, 1st quartile, median, mean, 3rd quartie and maximum values, as well as the count of missing value (`NA`).
    * For categorical variables (e.g. `factor`), we can frequencies for each level as well as the count of missing value (`NA`). 
* `summary()` is also used to get the "summary" of a fitted model object (e.g. `lm`) as well, as we will see shortly.


========================================================

```r
summary(ispcrime)
```

```
      year            county     violentCrime       murder       
 Min.   :2011   Adams    :  5   Min.   :    0   Min.   :  0.000  
 1st Qu.:2012   Alexander:  5   1st Qu.:   19   1st Qu.:  0.000  
 Median :2013   Bond     :  5   Median :   42   Median :  0.000  
 Mean   :2013   Boone    :  5   Mean   :  501   Mean   :  7.026  
 3rd Qu.:2014   Brown    :  5   3rd Qu.:  133   3rd Qu.:  1.000  
 Max.   :2015   Bureau   :  5   Max.   :33348   Max.   :566.000  
                (Other)  :480   NA's   :7       NA's   :7        
      rape            robbery          aggAssault      propertyCrime   
 Min.   :   0.00   Min.   :    0.0   Min.   :    0.0   Min.   :     0  
 1st Qu.:   1.00   1st Qu.:    0.0   1st Qu.:   15.0   1st Qu.:   133  
 Median :   6.00   Median :    2.0   Median :   33.0   Median :   349  
 Mean   :  41.29   Mean   :  172.3   Mean   :  280.4   Mean   :  2913  
 3rd Qu.:  22.00   3rd Qu.:   13.0   3rd Qu.:  102.0   3rd Qu.:  1190  
 Max.   :1986.00   Max.   :16095.0   Max.   :15129.0   Max.   :178902  
 NA's   :7         NA's   :7         NA's   :7         NA's   :7       
    burglary         larcenyTft           MVTft             arson        
 Min.   :    0.0   Min.   :     0.0   Min.   :    0.0   Min.   :   0.00  
 1st Qu.:   35.5   1st Qu.:    85.5   1st Qu.:    3.0   1st Qu.:   1.00  
 Median :   79.0   Median :   258.0   Median :   10.0   Median :   2.00  
 Mean   :  589.3   Mean   :  2084.9   Mean   :  215.2   Mean   :  23.45  
 3rd Qu.:  268.0   3rd Qu.:   852.0   3rd Qu.:   30.0   3rd Qu.:   8.50  
 Max.   :38485.0   Max.   :116145.0   Max.   :22879.0   Max.   :1418.00  
 NA's   :7         NA's   :7          NA's   :7         NA's   :7        
```


Numerical variables
========================================================
* Central tendency
* Variability
* Shape
* Outliers


Central tendency
========================================================
* In statistics, central tendency is concerned with the "center" of a distribution. The following three are the common measures of central tendency:
  * "mean" for the arithmetic mean
  * "median" for the 50th percentile
  * "mode" for the most frequent value
* R has built-in functions for the first two: `mean()` and `median()`
  

========================================================

```r
mean(ispcrime$violentCrime)
```

```
[1] NA
```

```r
median(ispcrime$violentCrime)
```

```
[1] NA
```
<p style="text-align:center">... wait, what?</p>

========================================================

```r
mean(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1] 500.9702
```

```r
median(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1] 42
```
* `NA` is known to be "contagious" in R, making any operation with missing values return `NA`
* `na.rm` is an argument with a boolean input to control whether `NA` values are removed/excluded in calculation

Variability
========================================================
* Variability (or dispersion) in statistics is concerned with the extent to which a distribution is spreaded out.
* There exist various measures for variability and R has built-in functions for many of them:
  * range: `min()`, `max()`, `range()`
  * percentiles: `fivenum()`, `IQR()`, `quantile()`
  * variance: `var()`, `sd()`


========================================================
**Range**

```r
min(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1] 0
```

```r
max(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1] 33348
```

```r
range(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1]     0 33348
```
* Range is the interval between the minium nad maximum values.


========================================================
**Percentiles**

```r
fivenum(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1]     0    19    42   133 33348
```

```r
IQR(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1] 114
```
* `fivenum()` returns what is called Tukey's five number summary (minumum, 1st quartile, median, 3rd qurtile, maximum) for the input data
* `IQR()` returns the inter-quartile range, which is the difference between the 1st quartile (25%) and 3rd quartile (75%)


========================================================

```r
# default: equal to fivenum()
quantile(ispcrime$violentCrime, probs = seq(0, 1, 0.25), na.rm = TRUE)
```

```
   0%   25%   50%   75%  100% 
    0    19    42   133 33348 
```

```r
quantile(ispcrime$violentCrime, probs = seq(0, 1, 0.1), na.rm = TRUE)
```

```
     0%     10%     20%     30%     40%     50%     60%     70%     80% 
    0.0     5.0    13.0    24.0    32.0    42.0    57.0    90.0   246.2 
    90%    100% 
  668.4 33348.0 
```
* The default setting output of `quantile()` is equal to `fivenum()` output
* However, `quantile()` can use `probs` arugment to get more flexible output

========================================================
**Variance**

```r
var(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1] 9463013
```

```r
sd(ispcrime$violentCrime, na.rm = TRUE)
```

```
[1] 3076.201
```
* `var()` returns the sample variance of the given data:
    * $s^2 = (\sum{x - \bar{x}}^2)/(n-1)$
* `sd()` returns the standard deviation of the given data:
    * $s = \sqrt{(\sum{x - \bar{x}}^2)/(n-1)}$

========================================================

```r
variables <- ispcrime %>% select(violentCrime, propertyCrime)
var(variables, na.rm = TRUE)
```

```
              violentCrime propertyCrime
violentCrime       9463013      46803865
propertyCrime     46803865     234761775
```
* When multiple variables are given as its input, `var()` returns a covariance matrix
    * In such cases, `cov()`can be used instead; however, `cov()` has no `na.rm` argument to remove missing values


Shape
========================================================
* The skewness and kurtosis (fatness/thinness) of a distribution are called the "shape" of the distribution.
* The `moments` package offers the following functions to meaasure the shape of a distribution:
    * `skewness()`
    * `kurtosis()`
    * See `moments` package [documentation](https://cran.r-project.org/web/packages/moments/moments.pdf)


Outliers
========================================================
* Outliers are observations or data points that are far from most other observations and disproportinately affect key summary statistics
* The `outliers` package offers useful functions to detect and measure outliers in data.
    * See `outliers` package [documentation](https://cran.r-project.org/web/packages/outliers/outliers.pdf)


Categorical variables
========================================================
* Frequency table is one of the most common ways to summarize the distribution of a catagorical variable:
    * In fractions
    * With margins



========================================================

```r
ispcrime2 <- left_join(ispcrime, regions)
```


A dplyr way
========================================================

```r
data %>%
  group_by(variable) %>%
  count()
```



Basic Inferential Statistics
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-13" alt="plot of chunk unnamed-chunk-13" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Comparing means
========================================================
* Student's t-test
* Wilcoxon rank-sum and signed-rank tests
* Analysis of variance (ANOVA)


Student's t-test
========================================================

```r
t.test(x, y = NULL, alternative = c("two.sided", "less", "greater"),
       mu = 0, conf.level = 0.95, ...)
t.test(formula, data, subset, na.action, ...)
```
* The null hypothesis assumes normal distribution
* The tested null hypothesis is no difference in mean and the alternative hypothesis can one of the three options, with the default of "two.sided"
* One sample t-test is conducted with only `x` input is given
    * The mean of `x` is compared against the `mu` value (default 0)
* Two sample t-test can be conducted by either supplying `x` and `y` inputs or using `formula` (`y ~ x`) with `data` input


========================================================

```r
viol_crime_north <- (filter(ispcrime2, region == "Northern"))$violentCrime
viol_crime_south <- (filter(ispcrime2, region == "Southern"))$violentCrime
t.test(viol_crime_north, viol_crime_south)
```

```

	Welch Two Sample t-test

data:  viol_crime_north and viol_crime_south
t = 4.4064, df = 105.49, p-value = 2.534e-05
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 176.7132 465.8398
sample estimates:
mean of x mean of y 
 438.2000  116.9235 
```


Wilcox tests
========================================================

```r
wilcox.test(x, y = NULL, alternative = c("two.sided", "less", "greater"),
            mu = 0, conf.level = 0.95, ...)
wilcox.test(formula, data, subset, na.action, ...)
```
* The null hypothesis does NOT assume normality
* One sample Wilcox test (rank-sum test) is conducted with only `x` input is provided
* Two sample Wilcox test (singed-rank test) can be conducted by either supplying `x` and `y` inputs or using `formula` (`y ~ x`) with `data` input


Analysis of Variance
========================================================

```r
aov(formula, data, qr = TRUE, ...)
```
* `formula` is of the following format: `value ~ subgroup`
* `summary()` has a method for `aov` class that returns a refined print result
* `model.tables()` has a method for `aov` class for reporting table of means or table of effects


========================================================

```r
aov_by_region <- aov(formula = violentCrime ~ region, data = ispcrime2)
print(aov_by_region)
```

```
Call:
   aov(formula = violentCrime ~ region, data = ispcrime2)

Terms:
                    region  Residuals
Sum of Squares  4657351567   93080910
Deg. of Freedom          3        499

Residual standard error: 431.8969
Estimated effects may be unbalanced
7 observations deleted due to missingness
```

```r
summary(aov_by_region)
```

```
             Df    Sum Sq   Mean Sq F value Pr(>F)    
region        3 4.657e+09 1.552e+09    8323 <2e-16 ***
Residuals   499 9.308e+07 1.865e+05                   
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
7 observations deleted due to missingness
```


========================================================

```r
model.tables(aov_by_region, type = "means")
```

```
Tables of means
Grand mean
         
500.9702 

 region 
    Central  Cook Northern Southern
        170 30848    438.2    116.9
rep     230     5     85.0    183.0
```

```r
model.tables(aov_by_region, type = "effects")
```

```
Tables of effects

 region 
    Central  Cook Northern Southern
       -331 30347   -62.77     -384
rep     230     5    85.00      183
```


========================================================
* Test of equal proprtions
* Chi-square test


Two sample Z-test
========================================================

```r
prop.test(x, n, p = NULL, alternative = c("two.sided", "less", "greater"),
          conf.level = 0.95...)
```


Chi-square test
========================================================

```r
chisq.test(x, y = NULL, p = rep(1/length(x), length(x)), B = 2000, ...)
```


Other statistical tests
========================================================

```r
# Shapiro-Wilk test of normality
shapiro.test(x)

# One- or two-sample Kolmogorov-Smirnov test
ks.test(x, y, ..., alternative = "two.sided", exact = NULL)

# F-test to compare variances
var.test(x, y, ratio = 1, alternative = "two.sided",
         conf.level = 0.95, ...)
var.test(formula, data, subset, na.action, ...)

# Test of correlation between paired samples
cor.test(x, y, alternative = "two.sided", conf.level = 0.95,
         method = c("pearson", "kendell", "spearman"), ...)
```


Linear models
========================================================
type:section
<p style="font-size:1.5em">
$$y_i = \beta_0 + \beta_1 x_i + \varepsilon_i$$
<br>
$$\boldsymbol{\text{y}} = \boldsymbol{\text{X}}^{\text{T}}\boldsymbol{\beta} + \boldsymbol{\varepsilon}$$
</p>

The lm() function
========================================================

```r
lm(formula, data, subset, na.action, ...)
```
* `lm()` is used to fit linear models, according to the `formula` input.


R formula
========================================================

```r
formula <- y ~ x1 + x2
```
* simply use `y ~ .` to include all other columns additively as explanatory variables

Model summary
========================================================

```r
lmfit <- lm(formula, data)
summary(lmfit)
```


Extending lm() formula
========================================================
* Transformations
* Interaction terms
* Polynomials
* Polynomial splines


Transformations
========================================================

```r
scale(y) ~ log(x1) + sqrt(x2) + ...
```
* We can transform the terms in either side of `~`


Interactions
========================================================

```r
y ~ x1 + x2 + x1:x2
y ~ x1 * x2
```
* `x1:x2` takes the interactions of all terms in `x1` and `x2`
* `x1*x2` is equivalent to `x1:x2` *and* the original terms `x1` and `x2` 
* It is recommended to use an interaction term with all the original terms


Polynomials
========================================================

```r
y ~ ploy(x, degree = n)
y ~ x + I(x^2) + I(x^3) + ...
```
* `poly()` generates the n-th degree polynimals of the input `x`
* `ploy(x, 3)` is equivalent to using `x + I(x^2) + I(x^3)`
    * `I()` ensures the `^` with a symbol is used as an arithmetic operator


Polynomial splines
========================================================

```r
library(splines)
y ~ ns(x, ...)
```

```
y ~ ns(x, ...)
```

```r
y ~ bs(x, degree = n, ...)
```

```
y ~ bs(x, degree = n, ...)
```
* `splines::ns()` is used for the natural cubic splines
* `splines::bs()` is used for the n-th degree polynomial splines
    * equivalent to `splines::bs(x, degree = 3)`


broom package
========================================================
* `broom` is a `tidyverse` package for "tidying up" statistical model outputs in R, i.e., converting them into tidy data frames.
* Key functions:
  * `glance()`
  * `tidy()`


The glance() function
========================================================

```r
glance(x, ...)
```
* `glance()` takes a model object as `x` input and returns a concise one-row summary of the model.

The tidy() function
========================================================
tidy(x, ...)

* 

modelr package
========================================================
* `modelr` is a `tidyverse` package that provides helper functions for statistical modeling in R
* partitioning and sampling
    * `resample()`, `resample_partition()`, `bootstrap()`
* model quality metrics
    * `rmse()`, `mae()`, `qae()`
* interacting with models
    * `add_predictions()`, `add_residuals()`


Partitioning and sampling
========================================================

```r
resample()
resample_partition()
bootstrap()
```



Model quality metrics
========================================================

```r
rmse(model, data)
mae(model, data)
qae(model, data, probs = c(0.05, 0.25, 0.5, 0.75, 0.95))
rsquare(model, data)
```
* `rmse()` returns the root mean squared error
* `mae()` returns the mean abosolute error
* `qae()` returns quantiles of absolute error
* `rsquare()` returns the $R^2$ value, i.e. the variance of the predictions divided by the variance of the reponse


Interacting with models
========================================================

```r
add_predictions(data, model, var = "pred")
add_residuals(data, model, var = "resid")
```
* `add_predictions()` adds a new column to a data frame for predicted values based on a model
* `add_residuals()` adds a new column to a data frame for residuals based on a model


Generalized linear models
========================================================
type:section
<p style="font-size:1.5em">
$$\text{E}[\boldsymbol{\text{Y}}] = \mu = g^{-1}(\boldsymbol{\text{X}\beta})$$
<br>
$$\text{Var}[\boldsymbol{\text{Y}}] = \text{V}[\mu] = \text{V}[g^{-1}(\boldsymbol{\text{X}}\boldsymbol{\beta})]$$
</p>


GLM basics
========================================================
* GLM is extends the linear model to fit response variables with error distribution other than a gaussian distribution
* Three components of GLM:
    * A probability distribution from the exponential family
    * A linear predictor, $\eta = \boldsymbol{\text{X}\beta}$
    * A link function $g$, such that $\text{E}[\boldsymbol{\text{Y}}] = \mu = g^{-1}(\eta)$

The glm() function
========================================================

```r
glm(formula, family = gaussian, data, ...)
```
* `formula`
* `family` input specifies the link function $g$
    * the default is `gaussian(link = "identity")` for the linear model


========================================================
**`family` objects**

|family                              |Use                                                                     |
|:-----------------------------------|:-----------------------------------------------------------------------|
|`gaussian(link = "identity")`       |Linear model for continous outcome<br>(ordinary linear regression; OLS) |
|`binomial(link = "logit")`          |Logit model for binary outcome<br>(logistic regression)                 |
|`poisson(link = "log"`)             |Poisson model for count outcome                                         |
|`Gamma(link = "inverse")`           |                                                                        |
|`inverse.gaussian(link = "1/mu^2")` |                                                                        |
|`quasi(link = "identitiy")`         |                                                                        |
|`quasibinomial(link = "logit")`     |                                                                        |
|`quasipoisson(link = "log")`        |                                                                        |


Logit model
========================================================

```r
glm(formula, family = binomial, data, ...)
```


Poisson model
========================================================

```r
glm(formula, family = poisson, data, ...)
```


Better ways?
========================================================
There are thrid-party packages to provide additional fuctions and/or different interfaces to existing statistical analysis functions. Although I have little exposure to them, the following two might be worth checking:

* `psych` package
    * See [this package vignette](https://cran.r-project.org/web/packages/psych/vignettes/intro.pdf) by the package author
* `jmv` package
    * See [this package documentation page](https://www.jamovi.org/jmv/)


Resources
========================================================
* Kabacoff, R. ["Statistics"](https://www.statmethods.net/stats/index.html). *Quick-R*.
* Lane D. et al. [*Online Statistics: A Multimedia Course of Study*](http://onlinestatbook.com/2/index.html).
* Prabhakaran, S. [r-statistics.co](http://r-statistics.co/).
* UCLA Institute for Digital Research and Education. ["R"](https://stats.idre.ucla.edu/r/).
* University of Cincinnati. ["Descriptive analytics"](http://uc-r.github.io/descriptive). *UC Business Analytic R Programming Guide*.
* University of Cincinnati. ["Predictive analytics"](http://uc-r.github.io/predictive). *UC Business Analytic R Programming Guide*.
* Wollschlaeger, D. [*RExRepos*](http://dwoll.de/rexrepos/index.html).
* Yau, C. ["Elementary Statistics with R"](http://www.r-tutor.com/elementary-statistics). *R Tutorial*.


Questions?
========================================================
type: section
<img src="https://media0.giphy.com/media/8lPSqcjcNjymIOS4Pm/giphy.gif" title="plot of chunk unnamed-chunk-39" alt="plot of chunk unnamed-chunk-39" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://giphy.com/gifs/kpop-bts-8lPSqcjcNjymIOS4Pm">Giphy</a>
</p>


========================================================
References
<ul style="font-size: 0.6em; list-style-type:none">
  <li>Lane D. et al. (n.d.). <a href="http://onlinestatbook.com/2/index.html"><span style="font-style:italic">Online Statistics: A Multimedia Course of Study</span></a>.</li>
  <li>Prabhakaran, S. (n.d.). <a href="http://r-statistics.co/Statistical-Tests-in-R.html">"Statistic Tests"</a>. <i>r-statistics.co</i>.</li>
  <li><a href="https://github.com/tidyverse/broom">tidyverse/broom Github repository</a></li>
  <li><a href="https://github.com/tidyverse/modelr">tidyverse/modelr Github repository</a></li>
  <li>University of Cincinnati. <i><a href="http://uc-r.github.io/">UC Business Analytics R Programming Guide</a></i></li>
  <li>Wikipedia contributors. (2018). <a href="https://en.wikipedia.org/wiki/Generalized_linear_model">"Generalized linear model"</a>. <i>Wikipedia, The Free Encyclopedia</i>.</li>
</ul>


========================================================
type: section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Ic_pause_circle_outline_48px.svg/2000px-Ic_pause_circle_outline_48px.svg.png" title="plot of chunk unnamed-chunk-40" alt="plot of chunk unnamed-chunk-40" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>
