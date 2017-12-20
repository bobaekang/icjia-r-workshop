# template elements
<div class="header"></div>
<div class="footer"></div>
<img src="http://www.icjia.state.il.us/_themes/icjia/img/logo-icjia-small-blue-3.png" class="logo"></img>
<img src="https://www2.illinois.gov/PublishingImages/seal.gif" class="seal"></img>


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style.css
<h3 style="color: #789">Module 1: Introduction to R</h3>  
2018-01-01  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  


Introducing ... R!
========================================================
type:section

```
[1] "Hellow World!"
```

<img src="https://www.r-project.org/logo/Rlogo.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.r-project.org/logo/">r-project.org</a>
</p>


What is R?
========================================================
> "R is a language and environment for statistical computing and graphics." - The R Foundation

* *Built for* data analysis and visualization
* One of the the most popular choices of programming language among academic researchers and data scientists


========================================================
<img src="https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/10/plot_tags_time-1-675x675.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: David Robinson, 2017, <a href="https://stackoverflow.blog/2017/10/10/impressive-growth-r/">"The Impresseive Growth of R"</a>
</p>


Why R?
========================================================
<img src="https://c1.staticflickr.com/4/3903/14750882233_cf43e135b9_b.jpg" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.flickr.com/">flickr.com</a>
</p>

========================================================
<p style="text-align:center">(Because ... DUH!)</p>
<img src="http://www.reactiongifs.com/r/2013/09/duh.gif" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="60%" style="display: block; margin: auto;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.reactiongifs.com/">Reaction GIFs</a>
</p>

And more reasons
========================================================
* Open source (free!)
* Built for statistical analysis
* Reproducible and transparent
* Extensible through powerful third-party libraries
* Enabling researchers to tackle a variety of tasks using a *single* platform


Comparisons
========================================================
type:section


R vs Excel
========================================================
* License cost
* Speed
* Scalability
* Complex and advanced analysis
* Visualization


R vs SPSS
========================================================
* License cost (again)
* Syntax
* Visualization
* Presentation


R vs Tableau
========================================================
* License cost (DUH!)
* Cleaning data
* Complex and advanced analysis


========================================================
type:section
<img src="https://www.rstudio.com/wp-content/uploads/2016/09/RStudio-Logo-Blue-Gray-250.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="30%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.rstudio.com//">RStudio</a>
</p>


What is RStudio? Why use it?
========================================================
* Best Integrated Development Environment (IDE) for R
* Powerful and convenient features
* Interactive workflow
* Open source (again!)
* ... and many more!


========================================================
<img src="https://upload.wikimedia.org/wikipedia/commons/3/39/Structure_of_Rstudio.jpeg" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="100%" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.wikimedia.org//">Wikimedia.org</a>
</p>


Basic Setup
========================================================
type:section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Simpleicons_Interface_gears-couple.svg/2000px-Simpleicons_Interface_gears-couple.svg.png" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.wikimedia.org//">Wikimedia.org</a>
</p>


Installing R
========================================================
* Visit https://cran.r-project.org/
* Or simply google "download R" to find the link to download page.
* *Installation requires the Administrator account*; talk to DoIT!


========================================================
<img src="../images/installing_r1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/installing_r2.png" title="plot of chunk unnamed-chunk-9" alt="plot of chunk unnamed-chunk-9" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/installing_r3.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/installing_r4.png" title="plot of chunk unnamed-chunk-11" alt="plot of chunk unnamed-chunk-11" width="85%" style="display: block; margin: auto; box-shadow: none;" />


Installing RStudio
========================================================
* Visit https://www.rstudio.com/products/rstudio/download/
* Or simply google "download Rstudio" to find the link to download page.
* Agin, *installation requires the Administrator account*; talk to DoIT!


========================================================
<img src="../images/install_rstudio1.png" title="plot of chunk unnamed-chunk-12" alt="plot of chunk unnamed-chunk-12" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/install_rstudio2.png" title="plot of chunk unnamed-chunk-13" alt="plot of chunk unnamed-chunk-13" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/install_rstudio3.png" title="plot of chunk unnamed-chunk-14" alt="plot of chunk unnamed-chunk-14" width="85%" style="display: block; margin: auto; box-shadow: none;" />


Workshop Overview
========================================================
type:section
<img src="https://upload.wikimedia.org/wikipedia/commons/c/c4/Cartoon-313457_640.jpg" title="plot of chunk unnamed-chunk-15" alt="plot of chunk unnamed-chunk-15" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.wikimedia.org//">Wikimedia.org</a>
</p>


Module 2
========================================================
<h2>R basics</h2>
* Fundamental building blocks of R programming.
* Libraries and packages
* `tidyverse` framework
* Recommended R style guide


Module 3
========================================================
<h2>Data manipulation</h2>
* Importing/exporting data
* Essential `dpylr` and `tidyr` commends
* Working with character strings
* Working with `Date` objects


Module 4
========================================================
<h2>Data visualization</h2>
* Base R plots
* `ggplot2` package
* Plotting maps
* Interactive plots


Module 5
========================================================
<h2>Statistical analysis</h2>


Module 6
========================================================
<h2>Presentations and beyond</h2>
* R Markdown and R Notebook
* R Presentation and `ioslides`
* Shiny applications
* ... and more!


Questions?
========================================================
type: section
<img src="https://media1.tenor.com/images/cfd1535c06cfdd626472663659f84e22/tenor.gif" title="plot of chunk unnamed-chunk-16" alt="plot of chunk unnamed-chunk-16" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://tenor.com/view/beyonce-question-gif-5966034">tenor.com</a>
</p>

