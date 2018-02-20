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
<a href="../notes/module4_notes2.html">
  <button type="button">Notes</button>
</a>
</div>


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 4: Data visualization with R (2)</h3>  
2018-01-01  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
<ul style="list-style: none">
<li>
  Part 1: The Grammar of Graphics</li>
<li style="color: #00061a; font-size: 1.1em; font-weight:700">
  Part 2: Maps and Interactive Plots</li>
</div>


Maps and Interactive Plots
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Maps
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Basics of spatial objects in R
========================================================


Packages for maps
========================================================
* `ggmap` for plotting maps using the `ggplot2` framework
* `tmap`
* `leaftlet` for interactive maps
* And more


ggmap package
========================================================
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="60%" style="display: block; margin: auto; box-shadow: none;" />


tmap package
========================================================
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="60%" style="display: block; margin: auto; box-shadow: none;" />


leaftlet package
========================================================
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="60%" style="display: block; margin: auto; box-shadow: none;" />


More on maps
========================================================
* `ggmap` [github repository](https://github.com/dkahle/ggmap)
* Kahle and Wickham. 2013. "ggmap: Spatial Visualization with ggplot2" [article](https://journal.r-project.org/archive/2013-1/kahle-wickham.pdf)
* Lovelace, et al. 2017. "Introduction to visualising spatial data in R
" [article](https://cran.r-project.org/doc/contrib/intro-spatial-rl.pdf)
* `tmap` [github repository](https://github.com/mtennekes/tmap)
    * [Links to vignettes and examples](https://github.com/mtennekes/tmap#vignettes-and-examples)
* `leaftlet` [official documentation page](https://rstudio.github.io/leaflet/)


Interactive Plots
========================================================
type:section
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Packages for interactive plots
========================================================
* `ggiraph`: an `htmlwidget` package for interactive `ggplot2` graphics
* `plotly`: R API for the plotly.js library
* `highcharter`: R API for the highchart.js library
* `googleVis`: R API for Google Charts
* And more


ggiraph package
========================================================
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Interactive geom layers
========================================================

```r
plot + geom_*_interactive(...)
```
* 12 interactive `geom` layers that can be integrated into a `ggplot` object:
    * bar, boxplot, histogram, line, map, path, point, polygon, rect, segment, text, tile


Interactive aesthetic mappings
========================================================

```r
aes(tooltip, onclick, data_id)
```
* `tooltip`
* `onclick`
* `data_id`


========================================================
**`ggiraph` example**


plotly package
========================================================
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" width="60%" style="display: block; margin: auto; box-shadow: none;" />


The ggplotly() function
========================================================

```r
ggplotly(p)
```
* Converts the `ggplot` object into an interactive plotly object
    * `p` is a `ggplot2::ggplot()` object
    

========================================================
**`ggplotly` example**


The plot_ly() interface
========================================================

```r
plot_ly(data, x, y, color, alpha, symbol, size, ...) %>%
  add_*(...) # equivalently, add_trace(type = "*")
```
* `plot_ly` takes a data frame and defines
* a "trace", the "geom" equivalent in `plot_ly` interface adds a layer to the plot output
    * `plotly` supports about 20 traces, including:
        * markers, text, lines, polygons, area, pie, bars, histogram, heatmap, and more
    * By default, each trace inherits the x and y (or even z) mappings from the preceding `plot_ly` object


========================================================
**`plot_ly` example**


highcharter package
========================================================
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-13" alt="plot of chunk unnamed-chunk-13" width="60%" style="display: block; margin: auto; box-shadow: none;" />


The hchart() function
========================================================




========================================================
**`hchart` example**



The highchart() interface
========================================================



========================================================
**`highcharter` example**


googleVis package
========================================================
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-16" alt="plot of chunk unnamed-chunk-16" width="60%" style="display: block; margin: auto; box-shadow: none;" />


========================================================
ddd


More on interactive plots
========================================================
* `ggiraph` [official documentation page](https://davidgohel.github.io/ggiraph/articles/offcran/using_ggiraph.html)
* `plotly` [official documentation page](https://plot.ly/r/)
* Sievert. *`plotly` for R* [book](https://plotly-book.cpsievert.me/)
* `highcharter` [official documentation page](http://jkunst.com/highcharter/index.html)
* `googleVis` [examples](https://cran.r-project.org/web/packages/googleVis/vignettes/googleVis_examples.html) by CRAN
