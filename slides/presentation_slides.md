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
<a href="../notes/presentation_notes.html">
  <button type="button">Notes</button>
</a>
</div>


# presentation
ICJIA R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789; font-size:1.5em; font-weight:300;">R&A Meeting Presentation</h3>
2018-02-13  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>


========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="70%" style="display: block; margin: auto; box-shadow: none;" />


Agenda
========================================================
<div style="text-align:left; margin-top:10%;">
<ul style="list-style: none">
<li>1. What is R and what can it do?</li>
<li>2. Workshop objectives and structure</li>
</div>


========================================================
<img src="../images/survey.jpg" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://pixabay.com/en/george-etienne-cartier-montreal-1720651/">pixabay.com</a>
</p>


A brief intro to ...
========================================================
type:section
<img src="../images/Rlogo.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.r-project.org/logo/">r-project.org</a>
</p>


What is R?
========================================================
> "R is a language and environment for statistical computing and graphics." - The R Foundation

* *Built for* data analysis and visualization
* One of the the most popular choices of programming language among academic researchers and data scientists


========================================================
**Benefits of using R**
* Open source (free!)
* Built for statistical analysis
* Reproducible and transparent
* Extensible through powerful third-party packages
* Enabling researchers to tackle a variety of tasks using a *single* platform


========================================================
With some practice ...

<img src="../images/dataviz_example1.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="33%" style="margin: auto; box-shadow: none;" /><img src="../images/dataviz_example2.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="33%" style="margin: auto; box-shadow: none;" /><img src="../images/dataviz_example3.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="33%" style="margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="http://www.r-graph-gallery.com/102-text-mining-and-wordcloud/">The R Graph Gallery</a>, <a href="https://cran.r-project.org/web/packages/ggCompNet/vignettes/examples-from-paper.html">The Comprehensive R Archive Network</a>
</div>

========================================================
<img src="../images/jean_cocteau.jpg" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="55%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://timedotcom.files.wordpress.com/2013/10/13051149.jpg">Time Magazine</a>
</p>


Data manipulation
========================================================
type: section
<img src="../images/tools.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org/">Wikimedia.org</a>
</div>


========================================================
**ISP UCR data (2011-2015)**



```r
# peak at the first rows of the data
head(ispcrime_tbl)
```

```
# A tibble: 6 x 12
   year county  violentCrime murder  rape robbery aggAssault propertyCrime
  <int> <fct>          <int>  <int> <int>   <int>      <int>         <int>
1  2011 Adams            218      0    37      15        166          1555
2  2011 Alexan~          119      0    14       4        101           290
3  2011 Bond               6      1     0       0          5           211
4  2011 Boone             59      0    24       8         27           733
5  2011 Brown              7      0     1       0          6            38
6  2011 Bureau            42      0     4       3         35           505
# ... with 4 more variables: burglary <int>, larcenyTft <int>,
#   MVTft <int>, arson <int>
```


========================================================

```r
# get a quick summary of violent crime and property crime
ispcrime_tbl %>%
  select(violentCrime, propertyCrime) %>%
  summary()
```

```
  violentCrime   propertyCrime   
 Min.   :    0   Min.   :     0  
 1st Qu.:   19   1st Qu.:   133  
 Median :   42   Median :   349  
 Mean   :  501   Mean   :  2913  
 3rd Qu.:  133   3rd Qu.:  1190  
 Max.   :33348   Max.   :178902  
 NA's   :7       NA's   :7       
```


========================================================

```r
# filter to keep only counties starting with C for 2013
#   while creating and showing a new variable for total crime count
ispcrime_tbl %>%
  filter(substr(county, 1, 1) == "C", year == 2013) %>%
  mutate(totalCrime = violentCrime + propertyCrime) %>%
  select(year, county, totalCrime)
```

```
# A tibble: 12 x 3
    year county     totalCrime
   <int> <fct>           <int>
 1  2013 Calhoun            NA
 2  2013 Carroll           231
 3  2013 Cass               63
 4  2013 Champaign        6567
 5  2013 Christian         428
 6  2013 Clark             131
 7  2013 Clay              226
 8  2013 Clinton           475
 9  2013 Coles             761
10  2013 Cook           181917
11  2013 Crawford          234
12  2013 Cumberland        115
```


========================================================

```r
# how about "D" counties in 2014 and 2015?
ispcrime_tbl %>%
  filter(substr(county, 1, 1) == "D", year %in% c(2014:2015)) %>%
  mutate(totalCrime = violentCrime + propertyCrime) %>%
  select(year, county, totalCrime)
```

```
# A tibble: 8 x 3
   year county  totalCrime
  <int> <fct>        <int>
1  2014 De Kalb       2218
2  2014 De Witt        182
3  2014 Douglas        116
4  2014 Du Page      12576
5  2015 De Kalb       2173
6  2015 De Witt        140
7  2015 Douglas        173
8  2015 Du Page      12538
```


========================================================

```r
# get annual average count of violent crime by county
ispcrime_tbl %>%
  group_by(county) %>%
  summarise(annualAvgCrime = sum(violentCrime, propertyCrime, na.rm = TRUE) / 5)
```

```
# A tibble: 102 x 2
   county    annualAvgCrime
   <fct>              <dbl>
 1 Adams             1724  
 2 Alexander          385  
 3 Bond               190  
 4 Boone              426  
 5 Brown               39.0
 6 Bureau             480  
 7 Calhoun             13.8
 8 Carroll            196  
 9 Cass               109  
10 Champaign         6567  
# ... with 92 more rows
```


========================================================

```r
# sort by average crime count? 
ispcrime_tbl %>%
  group_by(county) %>%
  summarise(annualAvgCrime = sum(violentCrime, propertyCrime, na.rm = TRUE) / 5) %>%
  arrange(desc(annualAvgCrime))
```

```
# A tibble: 102 x 2
   county    annualAvgCrime
   <fct>              <dbl>
 1 Cook              182818
 2 Du Page            14316
 3 Lake               12779
 4 Winnebago          12275
 5 Will               11078
 6 St. Clair           9262
 7 Sangamon            8876
 8 Kane                8332
 9 Peoria              7229
10 Champaign           6567
# ... with 92 more rows
```

========================================================

```r
# merging regions data and count the number of counties by region
ispcrime_tbl %>%
  left_join(regions) %>%
  group_by(region) %>%
  count()
```

```
# A tibble: 4 x 2
# Groups:   region [4]
  region       n
  <fct>    <int>
1 Central    230
2 Cook         5
3 Northern    85
4 Southern   190
```


========================================================

```r
# no duplicates!
ispcrime_tbl %>%
  select(county) %>%
  unique() %>%
  left_join(regions) %>%
  group_by(region) %>%
  count()
```

```
# A tibble: 4 x 2
# Groups:   region [4]
  region       n
  <fct>    <int>
1 Central     46
2 Cook         1
3 Northern    17
4 Southern    38
```


Data visualization
========================================================
type: section
<img src="../images/chart.png" title="plot of chunk unnamed-chunk-16" alt="plot of chunk unnamed-chunk-16" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org/">Wikimedia.org</a>
</div>


========================================================
**Example (1): Word cloud**
<img src="../images/dataviz_example1.png" title="plot of chunk unnamed-chunk-17" alt="plot of chunk unnamed-chunk-17" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="http://www.r-graph-gallery.com/102-text-mining-and-wordcloud/">The R Graph Gallery</a>
</div>


========================================================
**Example (2): Dendrogram**
<img src="../images/dataviz_example2.png" title="plot of chunk unnamed-chunk-18" alt="plot of chunk unnamed-chunk-18" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cran.r-project.org/web/packages/dendextend/vignettes/FAQ.html">The Comprehensive R Archive Network</a>
</div>


========================================================
**Example (3): Network graph**
<img src="../images/dataviz_example3.png" title="plot of chunk unnamed-chunk-19" alt="plot of chunk unnamed-chunk-19" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cran.r-project.org/web/packages/ggCompNet/vignettes/examples-from-paper.html">The Comprehensive R Archive Network</a>
</div>


========================================================
**Example (4): Line graph**
<img src="../images/dataviz_example4.png" title="plot of chunk unnamed-chunk-20" alt="plot of chunk unnamed-chunk-20" width="75%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
**Example (5): Choropleth map**
<img src="../images/dataviz_example5.png" title="plot of chunk unnamed-chunk-21" alt="plot of chunk unnamed-chunk-21" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Quick demonstration
========================================================
* Bar plot
* Histogram




========================================================

```r
# bar plot of crime count in 2015 by region
barplot <- ggplot(filter(ispcrime_tbl2, year == 2015), aes(x = region, y = violentCrime, fill = region, group = region)) +
  stat_summary(geom = "bar", fun.y = "sum")

barplot
```

![plot of chunk unnamed-chunk-23](presentation_slides-figure/unnamed-chunk-23-1.png)


========================================================

```r
# change labels and appearance
barplot2 <- barplot +
  labs(title = "Violent crime count in 2015 by region", x = "", y = "") +
  theme_classic(base_size = 15)

barplot2
```

![plot of chunk unnamed-chunk-24](presentation_slides-figure/unnamed-chunk-24-1.png)


========================================================

```r
# remove the legends and change colors
barplot2 +
  theme(legend.position = "None") +
  scale_fill_brewer(palette="Spectral")
```

![plot of chunk unnamed-chunk-25](presentation_slides-figure/unnamed-chunk-25-1.png)


========================================================

```r
# histogram of violent crime count by county
ggplot(ispcrime_tbl2, aes(x = violentCrime)) +
  geom_histogram(binwidth = 100) +
  facet_wrap(~ year) +
  labs(x = "Violent crime count", y = "Count") +
  theme_minimal(base_size = 15)
```

![plot of chunk unnamed-chunk-26](presentation_slides-figure/unnamed-chunk-26-1.png)


========================================================

```r
# exclude Cook county data from the histogram and add colors
ggplot(filter(ispcrime_tbl2, county != "Cook"), aes(x = violentCrime, fill = Year)) +
  geom_histogram(binwidth = 100) + facet_wrap(~ Year) +
  labs(x = "Violent crime count", y = "Count") +
  theme_minimal(base_size = 15)
```

![plot of chunk unnamed-chunk-27](presentation_slides-figure/unnamed-chunk-27-1.png)


Statistical modeling
========================================================
type: section
<img src="../images/dice.png" title="plot of chunk unnamed-chunk-28" alt="plot of chunk unnamed-chunk-28" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://pixabay.com/en/white-background-design-game-icon-2398914/">pixabay</a>
</div>


========================================================
**Example - Simple linear model**

```r
lm_fit <- lm(violentCrime ~ propertyCrime, ispcrime)
summary(lm_fit)
```

```

Call:
lm(formula = violentCrime ~ propertyCrime, data = ispcrime)

Residuals:
    Min      1Q  Median      3Q     Max 
-2239.5    -2.2    57.0    78.3  3992.9 

Coefficients:
                Estimate Std. Error t value Pr(>|t|)    
(Intercept)   -79.768287  16.496961  -4.835 1.77e-06 ***
propertyCrime   0.199367   0.001059 188.303  < 2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 363.5 on 501 degrees of freedom
  (7 observations deleted due to missingness)
Multiple R-squared:  0.9861,	Adjusted R-squared:  0.986 
F-statistic: 3.546e+04 on 1 and 501 DF,  p-value: < 2.2e-16
```


========================================================



```r
# put model fit results in a data frame format
tidy(lm_fit)
```

```
           term    estimate   std.error  statistic      p.value
1   (Intercept) -79.7682868 16.49696109  -4.835332 1.771126e-06
2 propertyCrime   0.1993675  0.00105876 188.302852 0.000000e+00
```


========================================================

```r
# get predictions and residuals for each data point
ispcrime %>%
  select(year, county, propertyCrime, violentCrime) %>%
  add_predictions(lm_fit) %>%
  add_residuals(lm_fit) %>%
  head()
```

```
  year    county propertyCrime violentCrime      pred      resid
1 2011     Adams          1555          218 230.24816 -12.248156
2 2011 Alexander           290          119 -21.95172 140.951715
3 2011      Bond           211            6 -37.70175  43.701747
4 2011     Boone           733           59  66.36808  -7.368081
5 2011     Brown            38            7 -72.19232  79.192322
6 2011    Bureau           505           42  20.91229  21.087706
```


========================================================

```r
# plot the model fit
plot(violentCrime ~ propertyCrime, ispcrime)
abline(lm_fit)
```

![plot of chunk unnamed-chunk-33](presentation_slides-figure/unnamed-chunk-33-1.png)


========================================================

```r
# show diagnostic plots
par(mfrow=c(2, 2))
plot(lm_fit)
```

![plot of chunk unnamed-chunk-34](presentation_slides-figure/unnamed-chunk-34-1.png)


========================================================
**Generalized linear models**

```r
# examples of generalized linear models with glm()
logistic_reg <- glm(binary ~ x1 + x2, data = mydata, family = binomial())
poisson_reg <- glm(count ~ x1 + x2, data = mydata, family = poisson())
gamma_reg <- glm(y ~ x1 + x2, data = mydata, family = Gamma())
```

**Other advanced models**
<small>
* time series models (e.g. `stats` and `forecast` packages)
* spatial regression models (e.g. `spdep` and `spgwr` packages)
* survival analysis (e.g. `survival` package)
* network analysis (e.g. `network` and `igraph` packages)
* text analysis (e.g. `tm` and `tidytext` packages)
* machine learning (e.g. `caret` and `mlr` packages)
</small>


And more!
========================================================
type: section
<img src="../images/cat_meme.gif" title="plot of chunk unnamed-chunk-36" alt="plot of chunk unnamed-chunk-36" width="45%" style="display: block; margin: auto; box-shadow: none;" />


Reports
========================================================
* HTML documents for web publishing
    * create interactive workflow using R Notebook
    * add interactive elements using `htmlwidgets` and/or `shiny`
* PDF documents for printing
* MS Word documents


========================================================
**Example - R Notebook**

<img src="../images/report.png" title="plot of chunk unnamed-chunk-37" alt="plot of chunk unnamed-chunk-37" width="75%" style="display: block; margin: auto; box-shadow: none;" />


Slideshow
========================================================
<img src="../images/slideshow.png" title="plot of chunk unnamed-chunk-38" alt="plot of chunk unnamed-chunk-38" width="75%" style="display: block; margin: auto; box-shadow: none;" />


Dashboard
========================================================
<a href="https://bobaekang.shinyapps.io/crime_data_profile_demo/">
<img src="../images/dashboard_demo.png" title="plot of chunk unnamed-chunk-39" alt="plot of chunk unnamed-chunk-39" width="75%" style="display: block; margin: auto; box-shadow: none;" />
</a>


Website
========================================================
<a href="../index.html">
<img src="../images/website.png" title="plot of chunk unnamed-chunk-40" alt="plot of chunk unnamed-chunk-40" width="75%" style="display: block; margin: auto; box-shadow: none;" />
</a>


Objectives
========================================================
type: section
<img src="../images/wanderer_above_the_sea_of_fog.jpg" title="plot of chunk unnamed-chunk-41" alt="plot of chunk unnamed-chunk-41" width="55%" style="display: block; margin: auto; box-shadow: none;" />


Technical objectives
========================================================
* Import and manipulate tabular data files using R;
* Create simple data visualizations to extract insight from data using R;
* Perform basic statistical analysis using R;
* Generate a report on a simple data analysis task using R


Fundamental objectives
========================================================
* Understand the basic elements of the R programming language;
* Employ the programmatic approach to research and data analysis projects; and
* Leverage online resources to find solutions to specific questions on using R for a given task.


Structure
========================================================
type: section
<img src="../images/module.jpg" title="plot of chunk unnamed-chunk-42" alt="plot of chunk unnamed-chunk-42" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Overall setup
========================================================
* Six modules
* One module per week
* Each module consists of two parts
    * except the first module on introduction
* All workshop materials (slides and notes) will be available
* I will be available, too,  for answering questions


Modules
========================================================
1. Introduction to R
2. R basics
3. Data analysis in R
4. Data visualization in R
5. Statistical modeling in R
6. Sharing your analysis and more


Questions?
========================================================
type: section
<img src="../images/psyduck_question.gif" title="plot of chunk unnamed-chunk-43" alt="plot of chunk unnamed-chunk-43" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="http://gph.is/1Q50iOW">Giphy.com</a>
</div>


========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-44" alt="plot of chunk unnamed-chunk-44" width="70%" style="display: block; margin: auto; box-shadow: none;" />

