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



Numerical variables
========================================================
* Central tendency
* Variability
* Shape
* Outliers


Central tendency
========================================================
* `mean()`
* `median()`
* `mode()`


Variability
========================================================
* range:
    * `min()`, `max()`, `range()`
* percentiles:
    * `fivenum()`, `IQR()`, `quantile()`
* variance: `var()`


Shape
========================================================
* `moments` package
    * `skewness()`
    * `kurtosis()`


Outliers
========================================================
* `outliers` package


Categorical variables
========================================================
* Frequency table
    * In fractions
    * With margins


A dplyr way
========================================================



Basic Inferential Statistics
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Comparing means
========================================================
* t-test: t.test()
* anova: aov()
  * Tukey's range test: TukeyHSD()

t-test
========================================================

ANOVA
========================================================


Comparing proportions
========================================================
* two sample Z-test: prop.test()
* chi-square test: chisq.test()

Two sample Z-test
========================================================


Chi-square test
========================================================


Better ways?
========================================================
* `psych` package
    * See [this introduction material](https://cran.r-project.org/web/packages/psych/vignettes/intro.pdf) by the package author
* `jmv` package
    * See [this package documentation webpate](https://www.jamovi.org/jmv/)


Linear models
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="60%" style="display: block; margin: auto; box-shadow: none;" />

The lm() function
========================================================



R formula
========================================================



Model summary
========================================================



broom package
========================================================
* `glance()`
* `tidy()`


The glance() function
========================================================



The tidy() function
========================================================



modelr package
========================================================
* partitioning and sampling
    * `resample()`, `resample_partition()`
* model quality metrics
    * `rmse()`, `mae()`, `qae()`
* interacting with models
    * `add_predictions()`, `add_residuals()`


Partitioning and sampling
========================================================
* `resample()`
* `resample_partition()`


Model quality metrics
========================================================
* `rmse()`
* `mae()`
* `qae()`


Interacting with models
========================================================
* `add_predictions()`
* `add_residuals()`


Transformations
========================================================


Polynomials
========================================================


Interactions
========================================================


Generalized linear models
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-11" alt="plot of chunk unnamed-chunk-11" width="60%" style="display: block; margin: auto; box-shadow: none;" />


The glm() function
========================================================



Families
========================================================


Logit model
========================================================



Poisson model
========================================================



Questions?
========================================================
type: section
<img src="" title="plot of chunk unnamed-chunk-15" alt="plot of chunk unnamed-chunk-15" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href=""></a>
</p>


========================================================
References
<ul style="font-size: 0.6em; list-style-type:none">
  <li><i><a href="http://uc-r.github.io/">UC Business Analytics R Programming Guide</a></i>, University of Cincinnati</li>
  <li><a href="https://github.com/tidyverse/broom">tidyverse/broom Github repository</a></li>
  <li><a href="https://github.com/tidyverse/modelr">tidyverse/modelr Github repository</a></li>
  <li><a href="#"></a></li>
</ul>


========================================================
type: section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Ic_pause_circle_outline_48px.svg/2000px-Ic_pause_circle_outline_48px.svg.png" title="plot of chunk unnamed-chunk-16" alt="plot of chunk unnamed-chunk-16" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>
