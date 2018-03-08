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
<a href="../notes/module1_notes.html">
  <button type="button">Notes</button>
</a>
</div>
<link href="https://fonts.googleapis.com/css?family=Oswald" rel="stylesheet">


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 1: Introduction to R</h3>  
2018-03-14  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  


Introduction to the Workshop
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Instructor (me!)
========================================================
<img src="../images/smily-face.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="35%" style="display: block; margin: auto; box-shadow: none;" />


Workshop objectives
========================================================
> This workshop will help you **to get started** and provide you with the basic skills and techniques in using R for research and data analysis. 

> Ultimately, this workshop seeks to help you **to gain the knowledge and confidence necesary to learn** what they need to know for you own research projects.


========================================================
* Import and manipulate tabular data files using R;
* Create simple data visualizations (scatterplot, histogram, bar chart, line chart, etc.) to extract insight from data using R;
* Perform basic statistical analysis using R;
* Generate a report on a simple data analysis task using R;
* Understand the basic elements of the R programming language;
* Employ the programmatic approach to research and data analysis projects; and
* Leverage online resources to find solutions to specific questions on using R for a given task.


A programming approach to research
========================================================
<img src="../images/programming-approach.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://pixabay.com/en/code-geek-talk-code-to-me-coffee-cup-2680204/">pixabay.com</a>
</p>


GUI workflow vs. programmatic workflow
========================================================
<div style="margin-top: 30%">
<img src="../images/archer.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="80%" style="display: block; margin: auto; box-shadow: none;" />
</div>

***

<div style="margin-top: 30%">
<img src="../images/lana.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="80%" style="display: block; margin: auto; box-shadow: none;" />
</div>


Benefits of a programming approach
========================================================
* Automation
* Modularity
* Reproducibility
* Version control


Automation
========================================================
* Implementing the research work in programs that will run later to automatically execute the work
* Producing consistent results

Modularity
========================================================
> In software design, modularity refers to a logical partitioning of the "software design" that allows complex software to be manageable for the purpose of implementation and maintenance.<br> - ["Modularity", Wikipedia](https://en.wikipedia.org/wiki/Modularity)

* Breaking down different stages or steps of research work into smaller but meaningful parts
* Separate programms for separate tasks
* Writing custom functions


Reproducibility
========================================================
> Reproducibility refers to the ability of a researcher to duplicate the results of a prior study using the same materials and procedures as were used by the original investigator. [...] Reproducibility is a minimum necessary condition for a finding to be believable and informative.<br> - [U.S. NSF Subcommittee on Replicability in Science](https://www.nsf.gov/sbe/AC_Materials/SBE_Robust_and_Reliable_Research_Report.pdf)

* Greater productivity in a collaborative project

Version control
========================================================
* The practice of managing changes in a document or a program in a systematic fashion
* Protecting the work from (unintentional) corruptions
* An example of version control system: Git


Introducing ... R!
========================================================
type:section

```
[1] "Hellow World!"
```

<img src="../images/Rlogo.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.r-project.org/logo/">r-project.org</a>
</p>



What is R?
========================================================
> "R is a language and environment for statistical computing and graphics." - The R Foundation

* *Built for* data analysis and visualization
* One of the the most popular choices of programming language among academic researchers and data scientists


========================================================
<img src="https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/10/plot_tags_time-1-675x675.png" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: David Robinson, 2017, <a href="https://stackoverflow.blog/2017/10/10/impressive-growth-r/">"The Impresseive Growth of R"</a>
</p>


Why R?
========================================================
<img src="https://c1.staticflickr.com/4/3903/14750882233_cf43e135b9_b.jpg" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.flickr.com/">flickr.com</a>
</p>

========================================================
<p style="text-align:center">(Because ... DUH!)</p>
<img src="http://www.reactiongifs.com/r/2013/09/duh.gif" title="plot of chunk unnamed-chunk-9" alt="plot of chunk unnamed-chunk-9" width="60%" style="display: block; margin: auto;" />
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
<img src="https://www.rstudio.com/wp-content/uploads/2016/09/RStudio-Logo-Blue-Gray-250.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" width="30%" style="display: block; margin: auto; box-shadow: none;" />
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
<img src="https://upload.wikimedia.org/wikipedia/commons/3/39/Structure_of_Rstudio.jpeg" title="plot of chunk unnamed-chunk-11" alt="plot of chunk unnamed-chunk-11" width="100%" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.wikimedia.org//">Wikimedia.org</a>
</p>


Basic Setup
========================================================
type:section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Simpleicons_Interface_gears-couple.svg/2000px-Simpleicons_Interface_gears-couple.svg.png" title="plot of chunk unnamed-chunk-12" alt="plot of chunk unnamed-chunk-12" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://www.wikimedia.org//">Wikimedia.org</a>
</p>


Installing R
========================================================
* Visit https://cran.r-project.org/
* Or simply google "download R" to find the link to download page.
* *Installation requires the Administrator account*; talk to DoIT!


========================================================
<img src="../images/installing_r1.png" title="plot of chunk unnamed-chunk-13" alt="plot of chunk unnamed-chunk-13" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/installing_r2.png" title="plot of chunk unnamed-chunk-14" alt="plot of chunk unnamed-chunk-14" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/installing_r3.png" title="plot of chunk unnamed-chunk-15" alt="plot of chunk unnamed-chunk-15" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/installing_r4.png" title="plot of chunk unnamed-chunk-16" alt="plot of chunk unnamed-chunk-16" width="85%" style="display: block; margin: auto; box-shadow: none;" />


Installing RStudio
========================================================
* Visit https://www.rstudio.com/products/rstudio/download/
* Or simply google "download Rstudio" to find the link to download page.
* Agin, *installation requires the Administrator account*; talk to DoIT!


========================================================
<img src="../images/install_rstudio1.png" title="plot of chunk unnamed-chunk-17" alt="plot of chunk unnamed-chunk-17" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/install_rstudio2.png" title="plot of chunk unnamed-chunk-18" alt="plot of chunk unnamed-chunk-18" width="85%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/install_rstudio3.png" title="plot of chunk unnamed-chunk-19" alt="plot of chunk unnamed-chunk-19" width="85%" style="display: block; margin: auto; box-shadow: none;" />


Workshop Overview
========================================================
type:section
<img src="https://upload.wikimedia.org/wikipedia/commons/c/c4/Cartoon-313457_640.jpg" title="plot of chunk unnamed-chunk-20" alt="plot of chunk unnamed-chunk-20" width="50%" style="display: block; margin: auto; box-shadow: none;" />
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
<h2>Data analysis with R</h2>
* Importing/exporting data
* Essential `dpylr` and `tidyr` commends
* Working with character strings
* Working with `Date` objects


Module 4
========================================================
<h2>Data visualization with R</h2>
* `ggplot2` package
* Plotting maps
* Interactive plots


Module 5
========================================================
<h2>Statistical modeling with R</h2>
* Basic statistical modeling
* Advanced modeling options


Module 6
========================================================
<h2>"To Infinity and Beyond"</h2>
* R Markdown and R Notebook
* R Presentation and `ioslides`
* Shiny applications
* Leveraging online resources
* ... and more!


Questions?
========================================================
type: section
<img src="https://media1.tenor.com/images/cfd1535c06cfdd626472663659f84e22/tenor.gif" title="plot of chunk unnamed-chunk-21" alt="plot of chunk unnamed-chunk-21" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://tenor.com/view/beyonce-question-gif-5966034">tenor.com</a>
</p>


References
========================================================
<ul style="font-size: 0.6em; list-style-type:none">
  <li><a href="#">1</a></li>
  <li><a href="#">2</a></li>
  <li><a href="#">3</a></li>
  <li><a href="#"></a></li>
</ul>

