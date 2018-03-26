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
<a href="../notes/module6_notes1.html">
  <button type="button">Notes</button>
</a>
</div>
<link href="https://fonts.googleapis.com/css?family=Oswald" rel="stylesheet">


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 6: "To Infinity and Beyond" (1)</h3>  
2018-04-18  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  




Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
<ul style="list-style: none">
<li style="color: #00061a; font-size: 1.1em; font-weight:700">
  Part 1: Sharing your work</li>
<li>
  Part 2: Leveraging online resources</li>
</div>


R Markdown
========================================================
type:section
<img src="../images/rmarkdown.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://rmarkdown.rstudio.com/authoring_quick_tour.html">R Markdown</a>
</p>


What is R Markdown?
========================================================
> "R Markdown is a file format for making dynamic documents with R. An R Markdown document is written in markdown (an easy-to-write plain text format) and contains chunks of embedded R code."<br><br> - Garret Grolemund from R Studio


Why use R Markdown?
========================================================
* Reproducible
* Multiple document formats
* Embedding R code chunks (and the outputs)


Getting started
========================================================
* Install `rmarkdown`
    * not necessary if using R Studio IDE
* Create a R markdown document
    * File > New File > R Markdown
* "Knit" the R markdown document into a file in the desired format


========================================================
<img src="../images/rmarkdown1.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="80%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/rmarkdown2.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="80%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
<img src="../images/rmarkdown3.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="80%" style="display: block; margin: auto; box-shadow: none;" />

========================================================
<img src="../images/rmarkdown4.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="80%" style="display: block; margin: auto; box-shadow: none;" />


Basics
========================================================
* YAML header
* knit and preview outputs
* markdown
* code chucks


========================================================
**yaml header**
<br><br>
<img src="../images/rmarkdown5.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="80%" style="display: block; margin: auto; box-shadow: none;" />


YAML header options
========================================================
* Title, author, date
* output
  * output format
  * output options 
  * different output format has different options


========================================================
**knit and prevew**
<br><br>
<img src="../images/rmarkdown6.png" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" width="80%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
**knit options**
<br><br>
<img src="../images/rmarkdown6-1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" width="80%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
**preview options**
<br><br>
<img src="../images/rmarkdown6-2.png" title="plot of chunk unnamed-chunk-9" alt="plot of chunk unnamed-chunk-9" width="80%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
**markdown**
<br><br>
<img src="../images/rmarkdown7.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" width="80%" style="display: block; margin: auto; box-shadow: none;" />


Markdown basics
========================================================
* Headers
* Font types (italic, bold, strikethrough, superscript)
* Lists (ordered, unordered)
* Hyperlinks
* Images
* Blackquotes
* Horizontal line/page break
* Math equations (using LaTeX)
* Code/R code (chunk, in-line)


========================================================
**Headers**
```
# Header 1

## Header 2

### Header 3
```
**Font types**
```
_italic_  __bold__

*italic*  **bold**


~~strikethrough~~


superscript^2^
```

========================================================
**Lists**
```
Unordered list  |  Ordered list
                | 
* Item 1        |  1. Item 1
    * Item 1a   |      1. Item 1a
* Item 2        |  2. Item 2
    + Item 2a   |      1. Item 2a
    - Item 2b   |      2. Item 2b
```
```
Mixed list

1. Item 1
    * Item 1a
* Item 2
    1. Item 2a
    + Item 2b
```

========================================================
**Hyperlinks**
```
[text with hyperlink](http://link.path)
```
**Images**
```
![](http://image.path/example.png)

![optional caption text](image/example.png)
```


========================================================
**Blockquotes**
```
> A line of text following the "> " is a blockquote.
```
> A line of text following the "> " is a blockquote.

**Horizontal line/page break**
```
More then three asteriks or dashs

***

******

------
```

========================================================
**Math equations**
```
Inline math equations look like: $y = (x + 1)^2$
```
<div style="font-size:.8em;">
Inline math equations look like: $y = (x + 1)^2$
</div>
<br>

```
A block of math equations look like:

$$y = x^2 + 2x + 1$$
```
<div style="font-size:.8em;">
A block of math equations look like: $$y = x^2 + 2x + 1$$
</div>


========================================================
**R code chunk**
<br><br>
<img src="../images/rmarkdown8.png" title="plot of chunk unnamed-chunk-11" alt="plot of chunk unnamed-chunk-11" width="80%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
**Insert a new code chunk**
<br><br>
<img src="../images/rmarkdown9.png" title="plot of chunk unnamed-chunk-12" alt="plot of chunk unnamed-chunk-12" width="80%" style="display: block; margin: auto; box-shadow: none;" />

* <small>keyboard shortcut: `Ctrl + Alt + i`</small>


========================================================
**Run code chunks**
<br><br>
<img src="../images/rmarkdown10.png" title="plot of chunk unnamed-chunk-13" alt="plot of chunk unnamed-chunk-13" width="80%" style="display: block; margin: auto; box-shadow: none;" />

* <small>keyboard shortcut: `Ctrl + Enter`</small>


knitr options
========================================================

```r
# use the following to control global options
knitr::opts_chunk$set(eval = TRUE, echo = TRUE, ...)
```
* Global options
    * Act as the default settings for the whole document

```r
_```{r eval = FALSE, echo = FALSE, ...}
```
* Local options (per code chunk)
    * Only applied to the specific code chunck
    * Overide the global options if relevant
* See [here](https://yihui.name/knitr/options/) for full documentation of `knitr` chunk options


========================================================
**Commonly used options**

|Option                          |Description                                                                                    |
|:-------------------------------|:----------------------------------------------------------------------------------------------|
|`eval` (`TRUE`)                 |Evaluate code in chunk? If FALSE, only code is shown                                           |
|`echo` (`TRUE`)                 |Show code in chunk? If FALSe, only output is shown                                             |
|`error` (`FALSE`)               |Preserve the error? If TRUE, knitting continues in case of errors                              |
|`message` (`TRUE`)              |Display code messages?                                                                         |
|`warning` (`TRUE`)              |Display code warnings?                                                                         |
|`include` (`TRUE`)              |Include the code chunk? If FALSE, neither code nor output is shown but code is still evaluated |
|`fig.show` (`asis`)             |How to show/arrange plots? (`"asis"`, `"hold"`, `"animate"`, `"hide"`)                         |
|`fig.width`, `fig.height` (`7`) |Plot width and height in inches.                                                               |


Tables
========================================================
* Printing basic data frame object
* Proper (HTML) tables with `knitr::kable()`
* Interactive tables with `DT::datatable()`


========================================================
**default print example**



```r
my_table
```

```
   my_fruits my_animals   my_flavors my_colors   my_cities
1      apple       dogs    chocolate       red     Chicago
2     banana       cats       vanila     green    New Work
3 clementine     llamas cookie dough    orange Los Angeles
```


========================================================
**kable example**

```r
knitr::kable(my_table)
```



|my_fruits  |my_animals |my_flavors   |my_colors |my_cities   |
|:----------|:----------|:------------|:---------|:-----------|
|apple      |dogs       |chocolate    |red       |Chicago     |
|banana     |cats       |vanila       |green     |New Work    |
|clementine |llamas     |cookie dough |orange    |Los Angeles |


========================================================
**datatable example**

```r
DT::datatable(my_table)
```
<iframe src="../interactive/datatable.html" style="display: block; margin: auto; min-height:500px; width:100%;"></iframe>


Documents
========================================================
type:section
<img src="../images/document_icon.png" title="plot of chunk unnamed-chunk-21" alt="plot of chunk unnamed-chunk-21" width="33%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia Commons</a>
</p>


R Markdown output formats
========================================================
* R Markdown supports various output formats
* Output format can be specified using `output` in the YAML header
    * The same document can be rendered in multiple formats
* Different output format has different YAML render options
    * Refer the page 2 of R Markdown cheat sheet on RStudio's [Cheat Sheets page](https://www.rstudio.com/resources/cheatsheets/) for a full list


========================================================
**Common output formats**

|`output` value    |Creates                         |
|:-----------------|:-------------------------------|
|`html_document`   |HTML file                       |
|`html_notebook`   |R Notebook HTML file            |
|`pdf_document`    |PDF (requires Tex) file         |
|`word_document`   |Microsoft Word file             |
|`md_document`     |Markdown file                   |
|`github_document` |GitHub compatible markdown file |


========================================================
**Commonly used YAML render options**

|Option            |Description                         |Available for               |
|:-----------------|:-----------------------------------|:---------------------------|
|`css`             |CSS file to use to style document   |html                        |
|`highlight`       |Syntax highlighting                 |html, pdf, word             |
|`number_sections` |Add section numbering to headers    |html, pdf                   |
|`theme`           |Bootswatch theme to use for page    |html                        |
|`toc`             |Add a table of contents             |html, pdf, word, md, github |
|`toc_depth`       |The lowest level of headings in toc |html, pdf, word, md, github |
|`toc_float`       |Float the toc on the left           |html                        |


========================================================
**Output appearances**

* Available highlights: `"default"`, `"tango"`, `"pygments"`,  `"kate"`, `"monochrome"`, `"espresso"`, `"zenburn"`, `"haddock"`, and `"textmate"`
* Available themes: `"default"`, `"cerulean"`, `"journal"`, `"flatly"`, `"readable"`, `"spacelab"`, `"united"`, `"cosmo"`,  `"lumen"`, `"paper"`, `"sandstone"`, `"simplex"`, and `"yeti"`
    * R Markdown themes are drawn from ["Bootswatch"](https://bootswatch.com/) themes


R Notebooks
========================================================
> "An R Notebook is an R Markdown document with chunks that can be executed independently and interactively, with output visible immediately beneath the input."<br>- "R Notebooks", RStudio

* While all other R Markdown formats requires "knitting" to see the final output, an R notebook document is automatically re-rendered each time the source file (`.Rmd`) is saved
* Offers a more interactive workflow


htmlwidgets for R
========================================================
* Thera are many R packages (90+) for taking full advantage of the interactivity that web can offer.
* With these packages, we can easily incorporate interactive widgets into HTML documents generated using R Markdown
* Examples of `htmlwidgets` include:
    * `plotly` and `highcharter` for interactive visualizations
    * `leaflet` for interactive maps
    * `DT` for interactive data tables
* Visit *`htmlwidgets` for R* [website](http://www.htmlwidgets.org/) to find out more


RPubs
========================================================
> "RPubs is a quick and easy way to disseminate data analysis and R code and do ad-hoc collaboration with peers."<br>- RStudio Team

* Publishing an R Markdown output on RPubs is as easy as clicking the "publish" button on RStudio
* Comparable to Tableau Public's Gallery website(?)


========================================================
<a href="https://rpubs.com/">
<img src="../images/rpubs_page.png" title="plot of chunk unnamed-chunk-24" alt="plot of chunk unnamed-chunk-24" width="80%" style="display: block; margin: auto; box-shadow: none;" />
</a>


Presentations
========================================================
type:section
<img src="../images/presentation_icon.png" title="plot of chunk unnamed-chunk-25" alt="plot of chunk unnamed-chunk-25" width="33%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia Commons</a>
</p>


Creating presentation slides
========================================================
* RStudio supports many ways to create presentation slides that are both modern-looking and highly customizable
* Popular ways to create slides using R include:
    * R Markdown formats:
        * `ioslides_presentation` (HTML)
        * `revealjs::revealjs_presentation` (HTML)
        * `slidy_presentation` (HTML)
        * `beamer_presentation` (PDF)
    * R Presentation (HTML)


ioslides
========================================================
```
---
title: "My first ioslide presentation"
output: ioslides_presentation
---
```

* `ioslides` output format is built into RStudio
* Fully integrates R Markdown syntax
    * Creating new slides is as easy as using `#` and `##` headings
* To learn more about `ioslides`, read the "Presentations with ioslides" [article](https://rmarkdown.rstudio.com/ioslides_presentation_format.html) on RStudio


========================================================
**Slides example**
```
---
title: "My first ioslide presentation"
author: Bobae Kang
date: April 18, 2018
output: ioslides_presentation
---
  
# First section


## Normal slide

- Item one
- Item two

## Another slide | With a subtitle

This slide has a two-column layout

----

![picture saying hello](images/hello.png)

```


========================================================
<iframe src="../interactive/slides_ioslides.html" style="display: block; margin: auto; min-height:650px; width:90%;"></iframe>


revealjs
========================================================
```
---
title: "My first revealjs presentation"
output: revealjs::revealjs_presentation
---
```

* With `revealjs` R package, it is possible to use R Markdown (and its syntax) to generate slides using reveal.js, a JavaScript library for interactive slides in HTML
    * Try [this demo slides](https://revealjs.com/) generated using reveal.js
* To learn more about `revealjs`, read the "Presentations with reveal.js" [article](https://rmarkdown.rstudio.com/revealjs_presentation_format.html) on RStudio


========================================================
<iframe src="../interactive/slides_revealjs.html" style="display: block; margin: auto; min-height:650px; width:100%;"></iframe>


Other formats
========================================================
* HTML presentations with `slidy`
    * Use `output: slidy_presentation` in the YAML header
    * See the "Presentations with Slidy" [article](https://rmarkdown.rstudio.com/slidy_presentation_format.html) on RStudio
* PDF presentations with `beamer`
    * Use `output: beamer_presentation`
    * See the "Presentations with Beamer" [article](https://rmarkdown.rstudio.com/beamer_presentation_format.html) on RStudio
* HTML presentations with `xaringan`
    * Use `output: xaringan::moom_reader`
    * Visit the package [GitHub repository](https://github.com/yihui/xaringan) for more 


R Presentation
========================================================
* R Presentation is not a R Markdown document
* Similar to R Notebook, R Presentation offers an interactive "Preview" which gets automatically re-rendered each time the source file (`.RPres`) is saved
* R Presentation slides are built on reveal.js
* All Workshop slides are generated using R Presentation
* Unfortunately, it is no longer in active development 
* To learn more about R Presentation, visit [relevant pages](https://support.rstudio.com/hc/en-us/sections/200130218-R-Presentations) on RStudio Support website


Shiny
========================================================
type:section
<img src="../images/shiny_logo.png" title="plot of chunk unnamed-chunk-26" alt="plot of chunk unnamed-chunk-26" width="25%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.rstudio.com/">R Studio</a>
</p>


What is Shiny?
========================================================
> "Shiny is an open source R package that provides an elegant and powerful web framework for building web applications using R. Shiny helps you turn your analyses into interactive web applications without requiring HTML, CSS, or JavaScript knowledge."<br>- RStudio.com

* Try my ICJIA Uniform Crime Report Data dashboard app [here](https://bobaekang.shinyapps.io/crime_data_profile_demo/)
* Check out more examples on RStudio's ["Shiny User Showcase" page](https://www.rstudio.com/products/shiny/shiny-user-showcase/) 


Dashboards
========================================================
* A data dashboard is a visual interface to data to allow its viewers for gain key insights
* It is often an interactive application that provides viewers with options to explore data from multiple angles interactively
* A Shiny application can make a great dashboard


Interactive documents
========================================================
* Shiny can be used to generate interactive documents with Shiny app widgets
* An interactive document is an R Markdown file with the YAML head including `runtime: shiny` and `output: html_document` or `output: ioslids_presentation`
* Embedded Shiny R code will render a mini application


========================================================
**Structure of an interactive document**
<br><br>
<img src="../images/shiny_interactive_doc.png" title="plot of chunk unnamed-chunk-27" alt="plot of chunk unnamed-chunk-27" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://shiny.rstudio.com/articles/interactive-docs.html">"Introduction to interactive documents"</a>. Shiny from R Studio
</p>


Getting started
========================================================

```r
install.pacakges("shiny")
library(shiny)

runExample("01_hello")
```
* Shiny is a package: install and import it
* Try a simple built-in example for Shiny application!


Shiny application
========================================================
* A Shiny app consists of two parts, `server` and `ui` 
* They can be separated into two files, `server.R` and `ui.R`
    * Both files must be located in the same directory
* Alternatively, both parts can live in a single file, `app.R`


server.R
========================================================

```r
function(input, output, session) {
  ## R code for server logic
}
```
* `server.R` contains the server-side logic of the application
* `input` object is an environment for storing user inputs modified by user's interaction with the application UI
* `output` object is an environment for storing elements (plots, tables, texts, etc) to be rendered and shown in the UI
* `session` object is an environment that can be used to access information relating to the session
    * `session` is optional


ui.R
========================================================

```r
fluidPage(
  ## R code for user interface
)
```
* `ui.R` defines the user interface elements:
    * layouts, panels, inputs and outputs
* Available layouts include: the sidebar layout and grid layout
* Available panels include: the title panel, sidebar panel, main panel, tabset panel, navigation list panel, and more
* `shiny` offers many functions to take user inputs
* `shiny` offers many functions to render outputs (as defined in `server.R`)


app.R
========================================================

```r
library(shiny)

server <- function(input, output) {
  # server-side logic
}

ui <- fluidPage(
  # user interface
)

shinyApp(ui, server)
```
* `app.R` must include `shinyApp(ui, server)` at the end
* `server` is an object containing code for server-side logic
* `ui` is an object containing user interface elements


More on Shiny development
========================================================
* Developing a Shiny app takes much practice, planning and <span style="text-decoration:line-through">pain</span> experiment
    * However, the reward is YUGE!
* Start with [these tutorials](https://shiny.rstudio.com/tutorial/) by RStudio
* Follow along [these articles](https://shiny.rstudio.com/articles/) by RStudio
* Refer to Shiny [Gallery](https://shiny.rstudio.com/gallery/widget-gallery.html) for examples and inspirations


Deploying Shiny apps
========================================================
* Shiny applications, including the interactive documents, can be deployed for use in the following ways:
    * Via [shinyapps.io](http://www.shinyapps.io/)
    * Via [Shiny Server](https://www.rstudio.com/products/shiny/shiny-server/)
    * Via [ShinyProxy](https://www.shinyproxy.io)


Deploying via shinyapps.io
========================================================
* The easiest way to deploy/publish a Shiny application
    * Takes only a few clicks on the RStudio IDE
* Requires signing up to [shinyapps.io](http://www.shinyapps.io/)
    * Can log in with Google or GitHub account
* See the pricing for hosting Shiny apps on the website
    * Free hosting is available but limited to 5 applications and 25 active hours per month


Websites
========================================================
type: section
<img src="../images/globe_icon.png" title="plot of chunk unnamed-chunk-32" alt="plot of chunk unnamed-chunk-32" width="33%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia Commons</a>
</p>


Static websites
========================================================
* A collection R Markdown documents in HTML format can be made into a website
    * To do so, we need a `_site.yml` file in the same folder as individual documents to be put together
    * `_site.yml` specifies the name and the routing structure of the resulting website
    * With `_site.yml` and all HTML documents ready, run `rstudio::render_site()` to generate the website
* For details, see the "R Markdown Websites" [article](https://rmarkdown.rstudio.com/rmarkdown_websites.html) on RStudio website



========================================================
**_site.yml format example (Workshop website)**
```
name: ICJIA R Workshop
output_dir: '.'
navbar:
  title: ICJIA R WORKSHOP
  right:
  - text: Home
    href: index.html
  - text: Modules
    href: modules.html
  - text: About
    href: about.html
output:
  html_document:
    includes:
      after_body: include_footer.html
    css: css/style.css
    lib_dir: site_libs
    self_contained: no
```

Hosting websites on Github Pages
========================================================
> "GitHub Pages is a static site hosting service designed to host your personal, organization, or project pages directly from a GitHub repository."<br>-"What is GitHub Pages?", GitHub Help

* [GitHub](https://github.com/) is a free and commercial online repository service for storing and sharing projects using [Git](https://git-scm.com/)
* The ICJIA R Workshop website is hosted on GitHub Pages
* Read more about GitHub Pages and hosting static sites on GitHub Pages on *GitHub Help* [here](https://help.github.com/categories/github-pages-basics/) 


Books with blogdown
========================================================
* `bookdown` package, built on R Markdown, facilitates writing books and long articles/reports.
    * A `bookdown` publication is made downloadable in PDF, EPUB and MOBI formats
* Check out `bookdown` package [website](https://bookdown.org/) to find out more
* Also, read Xie, Y. (2018). [*`bookdown`: Authoring Books and Technical Documents with R Markdown*](https://bookdown.org/yihui/bookdown/) for a comprehensive guide for `bookdown`
    * The book itself is generated using `bookdown`


========================================================
<a href="https://bookdown.org/yihui/bookdown/">
<img src="../images/bookdown_example.png" title="plot of chunk unnamed-chunk-33" alt="plot of chunk unnamed-chunk-33" width="80%" style="display: block; margin: auto; box-shadow: none;" />
</a>


Blogs with blogdown
========================================================
* `blogdown` is a package to generate static websites using R Markdown and the [Hugo]() open-source framework for building websites
* Visit *Awesome Blogdown* [website](http://awesome-blogdown.com/) for a curated list of `blogdown` examples
* Also, read Xie, Y. et al. (2018). [*`blogdown`: Creating Websites with R Markdown*](https://bookdown.org/yihui/blogdown/) for a comprehensive guide for `blogdown`


========================================================
<a href="http://roelandtn.frama.io/post/">
<img src="../images/blogdown_example1.png" title="plot of chunk unnamed-chunk-34" alt="plot of chunk unnamed-chunk-34" width="80%" style="display: block; margin: auto; box-shadow: none;" />
</a>


========================================================
<a href="http://www.visibledata.co.uk/">
<img src="../images/blogdown_example2.png" title="plot of chunk unnamed-chunk-35" alt="plot of chunk unnamed-chunk-35" width="80%" style="display: block; margin: auto; box-shadow: none;" />
</a>


========================================================
<a href="https://aurora-mareviv.github.io/talesofr/">
<img src="../images/blogdown_example3.png" title="plot of chunk unnamed-chunk-36" alt="plot of chunk unnamed-chunk-36" width="80%" style="display: block; margin: auto; box-shadow: none;" />
</a>


Questions?
========================================================
type: section
<img src="https://media1.giphy.com/media/Z1Exz24FbX3Ko/giphy.gif" title="plot of chunk unnamed-chunk-37" alt="plot of chunk unnamed-chunk-37" width="30%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://giphy.com/gifs/2013-question-disney-animation-Z1Exz24FbX3Ko">Giphy</a>
</p>


========================================================
References
<ul style="font-size: 0.6em; list-style-type:none">
  <li>Sellors, M. <a href="http://awesome-blogdown.com/"><i>Awesome Blogdown</i></a></li>
  <li>Chang, W. (2017). <a href="https://shiny.rstudio.com/articles/app-formats.html">"App formats and launching apps"</a>. <i>Shiny from RStudio</i></li>
  <li>Grolemund, G. (2014). <a href="http://shiny.rstudio.com/articles/interactive-docs.html">"Introduction to interactive documents"</a>. <i>Shiny from RStudio</i>.</li>
  <li>Grolemund, G. (2014). <a href="https://rmarkdown.rstudio.com/articles_intro.html">"Introduction to R Studio"</a>. <i>R Markdown from RStudio</i>.</li>
  <li>RStudio. (2016). <a href="https://www.rstudio.com/resources/cheatsheets/">R Markdown Cheat Sheet"</a>.</li>
  <li>Xi, Y. (2018). <a href="https://yihui.name/knitr/options/">"Options: Chunk options and package options"</a>. <i>knitr: Elegant, flexible, and fast dynamic report generation with R</i>.</li>
</ul>


========================================================
type: section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Ic_pause_circle_outline_48px.svg/2000px-Ic_pause_circle_outline_48px.svg.png" title="plot of chunk unnamed-chunk-38" alt="plot of chunk unnamed-chunk-38" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>
