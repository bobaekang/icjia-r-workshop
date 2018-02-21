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


ggmap: Plotting maps with ggplot2
========================================================
type: section


ggmap
========================================================
* what
* is
* ggmap


The get_map() function
========================================================

```r
get_map(location, zoom, scale, maptype, source, ...)
```
* Quickly graps a map from various sources:
    * Google Maps, OpenStreetMap, Staman Map, or Naver Map
* Returns a `ggmap` object, which can be plotted with the `ggmap()` function


========================================================
**`ggmap` example**


tmap: Thematic maps in R
========================================================
type: section


tmap
========================================================
* what
* is
* tmap


The qtm() function
========================================================

```r
qtm(shape_object, ...)
```
* Generates a "quicke thematic map"
    * comparable to `qplot()` in `ggplot2`
* Offers the same level of flexibility as the main plotting interface
    * The main interface is stil recommended for complex plots 


========================================================
**`qtm` example**


The tm_*() interface
========================================================

```r
tm_shape(shape_object) +
  tm_*() # add tmap elements as layers
```
* `tm_shape` takes a spatial "shape object"
* Add layers using tmap elements
    * two types of "drawing" layers: base and derived
    * "attribute" layers


tmap drawing layers 1
========================================================

| Sepal.Length| Sepal.Width| Petal.Length| Petal.Width|Species |
|------------:|-----------:|------------:|-----------:|:-------|
|          5.1|         3.5|          1.4|         0.2|setosa  |
|          4.9|         3.0|          1.4|         0.2|setosa  |
|          4.7|         3.2|          1.3|         0.2|setosa  |
|          4.6|         3.1|          1.5|         0.2|setosa  |
|          5.0|         3.6|          1.4|         0.2|setosa  |
|          5.4|         3.9|          1.7|         0.4|setosa  |


tmap drawing layers 2
========================================================



tmap attribute layers
========================================================




========================================================
**`tm_` example**


Static vs interactive modes
========================================================

```r
tmap_mode("plot") # set to static "plot" mode
tmap_mode("view") # set to interactive "view" mode

ttmp() # toggle between modes
```


========================================================
**`view` example**


========================================================
type: section
<img src="../images/leaflet.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" width="60%" style="display: block; margin: auto; margin-top: 15%; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="http://leafletjs.com/">leafletjs.com</a>
</p>


leaflet
========================================================
* what
* is
* leaflet


========================================================
**`leaflet` example**


Resources
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
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-11" alt="plot of chunk unnamed-chunk-11" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Packages for interactive plots
========================================================
* `ggiraph`: an `htmlwidget` package for interactive `ggplot2` graphics
* `plotly`: R API for the plotly.js library
* `highcharter`: R API for the highchart.js library
* `googleVis`: R API for Google Charts
* And more


========================================================
type: section
<img src="../images/ggiraph.gif" title="plot of chunk unnamed-chunk-12" alt="plot of chunk unnamed-chunk-12" width="30%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://davidgohel.github.io/ggiraph/">ggiraph documentation page</a>
</p>


ggiraph
========================================================
* what
* is
* ggiraph


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


========================================================
type: section
<img src="../images/plotly.png" title="plot of chunk unnamed-chunk-15" alt="plot of chunk unnamed-chunk-15" width="35%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://commons.wikimedia.org/wiki/File:Plotly_logo_for_digital_final_(6).png">wikimedia.org</a>
</p>


plotly
========================================================
* what
* is
* plotly


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
    * `plotly` supports about 20 traces
    * By default, each trace inherits the x and y (or even z) mappings from the preceding `plot_ly` object


plotly traces
========================================================



========================================================
**`plot_ly` example**


========================================================
type: section
<img src="../images/highcharter.png" title="plot of chunk unnamed-chunk-19" alt="plot of chunk unnamed-chunk-19" width="100%" style="display: block; margin: auto; margin-top: 15%; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://github.com/jbkunst/highcharter">highcharter github repo (jbkunst/highcharter)</a>
</p>


highcharter
========================================================
* what
* is
* highcharter


The hchart() function
========================================================

```r
hchart(data, type, hcaes(x, y, ...))
```
* Quickly generates a hichchart plot
    * Comparable to `qplot()` in `ggplot2`
* `hcaes()` works like `aes()` in `ggplot2`


========================================================
**`hchart` example**


The highchart() interface
========================================================

```r
highchart() %>%
  hc_xAxis(...) %>% # define x-axis
  hc_yAxis(...) %>% # define y-axis
  hc_add_series(...) %>% # add a "series"
  hc_chart(...) %>% # modify general plot options
  hc_color(...) %>% # control colors
  hc_title(...) %>% # add the main title
  hc_*(...) # and more...
```
* Closely follows the original Javascript API

========================================================
**`highcharter` example**


Resources
========================================================
* `ggiraph` [official documentation page](https://davidgohel.github.io/ggiraph/articles/offcran/using_ggiraph.html)
* `plotly` [official documentation page](https://plot.ly/r/)
* Sievert. *`plotly` for R* [book](https://plotly-book.cpsievert.me/)
* `highcharter` [official documentation page](http://jkunst.com/highcharter/index.html)
* `googleVis` [examples](https://cran.r-project.org/web/packages/googleVis/vignettes/googleVis_examples.html) by CRAN


Other packages
========================================================
