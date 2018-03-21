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
<link href="https://fonts.googleapis.com/css?family=Oswald" rel="stylesheet">


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 4: Data visualization with R (2)</h3>  
2018-04-04  
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




========================================================
type:section
<img src="../images/caution.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://commons.wikimedia.org/wiki/File:DIN_4844-2_Warnung_vor_einer_Gefahrenstelle_D-W000.svg">Wikimedia Commons</a>
</p>


Maps
========================================================
type:section
<img src="module4_slides2-figure/unnamed-chunk-3-1.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" style="display: block; margin: auto; box-shadow: none;" />


Prerequisites
========================================================
* Shapefile
* `rgdal` pacakge
* Spatial objects in R


Shapefile
========================================================
* what
* is
* shapefile


Importing a shapefile
========================================================

```r
library(rgdal)
spatial_object <- readORG(dsn, layer)

# example:
# il_counties <- read(dsn = "shapefiles", layer = "il_counties")
```
* the `readORG` function imports a shapefile into R environment
    * `dsn` is the path to the directory with a shapefile to import
    * `layer` is the name of a shapefile to import 
* the output is a spatial vector object


Spatial (vector) objects in R
========================================================
* There are multiple spatial vector object types:
  * Without attributes: `Spatial*` classes
      * <small>`Points`, `MultiPoints`, `Pixels`, `Grid`, ``Lines`, `Polygons`</small>
  * With attributes: `Spatial*DataFrame` classes
      * The attributes `data.frame` table can be accessed using standard methods.


Example
========================================================

```r
class(counties)
```

```
[1] "SpatialPolygonsDataFrame"
attr(,"package")
[1] "sp"
```
* `icjiar` package provides a spatial object `counties` for countes in Illinois
    * it is of the `SpatialPolygonsDataFrame` class


Packages for maps
========================================================
* `ggmap` package for plotting maps using the `ggplot2` framework
* `tmap` package for thematic maps
* `leaftlet` package for interactive maps
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


========================================================
**Base `tmap` drawing layers**

|Drawing layer |Description     |Aesthetics       |
|:-------------|:---------------|:----------------|
|`tm_polygons` |Draws polygons  |col              |
|`tm_symbols`  |Draws symbols   |size, col, shape |
|`tm_lines`    |Draws lines     |col, lwd         |
|`tm_raster`   |Draws a raster  |col              |
|`tm_text`     |Add text labels |text, size, col  |
<p style="font-size:0.5em">The table is duplicated from a `tmap` <a href="https://cran.r-project.org/web/packages/tmap/vignettes/tmap-nutshell.html">vignette page</a></p>


========================================================
**Derived `tmap` drawing layers**

|Drawing layer |Description             |Aesthetics                     |
|:-------------|:-----------------------|:------------------------------|
|`tm_fill`     |Fills the polygons      |see `tm_polygons`              |
|`tm_borders`  |Draws polygon borders   |none                           |
|`tm_bubbles`  |Draws bubbles           |see `tm_symbols`               |
|`tm_squares`  |Draws squares           |see `tm_symbols`               |
|`tm_dots`     |Draws dots              |see `tm_symbols`               |
|`tm_markders` |Draws markers           |see `tm_symbols` and `tm_text` |
|`tm_iso`      |Draws iso/contour lines |see `tm_lines` and `tm_text`   |
<p style="font-size:0.5em">The table is duplicated from a `tmap` <a href="https://cran.r-project.org/web/packages/tmap/vignettes/tmap-nutshell.html">vignette page</a></p>


========================================================
**`tmap` attribute layers**

|Attribute layer |Description               |
|:---------------|:-------------------------|
|`tm_grid`       |Add coordinate grid lines |
|`tm_credits`    |Add credits text label    |
|`tm_compass`    |Add map compass           |
|`tm_scale_bar`  |Add scale bar             |
<p style="font-size:0.5em">The table is duplicated from a `tmap` <a href="https://cran.r-project.org/web/packages/tmap/vignettes/tmap-nutshell.html">vignette page</a></p>


========================================================
**`tm_` example**


Styles
========================================================

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
<img src="../images/leaflet.png" title="plot of chunk unnamed-chunk-13" alt="plot of chunk unnamed-chunk-13" width="60%" style="display: block; margin: auto; margin-top: 15%; box-shadow: none;" />
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
<img src="../images/icjia-x-r.png" title="plot of chunk unnamed-chunk-14" alt="plot of chunk unnamed-chunk-14" width="60%" style="display: block; margin: auto; box-shadow: none;" />


Packages for interactive plots
========================================================
* `ggiraph`: an `htmlwidget` package for interactive `ggplot2` graphics
* `plotly`: R API for the plotly.js library
* `highcharter`: R API for the highchart.js library
* `googleVis`: R API for Google Charts
* And more


========================================================
type: section
<img src="../images/ggiraph.gif" title="plot of chunk unnamed-chunk-15" alt="plot of chunk unnamed-chunk-15" width="30%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://davidgohel.github.io/ggiraph/">ggiraph documentation page</a>
</p>


ggiraph
========================================================
> "ggiraph is an htmlwidget and a ggplot2 extension. It allows ggplot graphics to be animated."<br>- Gohel, D. (package author)


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
<img src="../images/plotly.png" title="plot of chunk unnamed-chunk-18" alt="plot of chunk unnamed-chunk-18" width="35%" style="display: block; margin: auto; box-shadow: none;" />
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

```r
data <- ispcrime %>% filter(county != "Cook") %>% left_join(regions)
p <- ggplot(data, aes(violentCrime, propertyCrime, colour = region)) +
  geom_point()
ggplotly(p)
```
<iframe src="../interactive/ggplotly.html" style="display: block; margin: auto; min-height:500px; width:60%;"></iframe>


The plot_ly() interface
========================================================

```r
plot_ly(data, x, y, color, alpha, symbol, size, ...)

 # equivalent to add_type()
add_trace(p, ..., type = "type", inheret = TRUE)
```
* `plot_ly` takes a data frame and defines the aesthetic mappings
* "trace" is the "geom" equivalent in `plot_ly` interface, which adds a layer to the plot output
    * While `plot_ly` can define traces, using `add_trace()` and its variants make it possible to use a `dplyr`-style workflow with pipe operators
    * By default, each trace inherits the mappings from `p`
    * `plotly` supports ~20 traces


plotly add functions
========================================================

|Function          |Description             |Equivalent to `add_trace(...)`   |
|:-----------------|:-----------------------|:--------------------------------|
|`add_trace()`     |add traces with options |`NA`                             |
|`add_markers()`   |adds a scattorplot      |`type="scatter", mode="markers"` |
|`add_lines()`     |adds a line plot        |`type="", mode=""`               |
|`add_bars()`      |adds a bar plot         |`type="", mode=""`               |
|`add_histogram()` |adds a histogram        |`type="", mode=""`               |
|`add_boxplot()`   |adds a box plot         |`type="", mode=""`               |
|`add_pie()`       |adds a pie chart        |`type="", mode=""`               |
|`add_text()`      |adds texts              |                                 |
|`add_polygons()`  |adds polygons           |`type="", mode=""`               |


========================================================
**`plot_ly` example**


========================================================
type: section
<img src="../images/highcharter.png" title="plot of chunk unnamed-chunk-23" alt="plot of chunk unnamed-chunk-23" width="100%" style="display: block; margin: auto; margin-top: 15%; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://github.com/jbkunst/highcharter">highcharter github repo (jbkunst/highcharter)</a>
</p>


highcharter
========================================================
> "Highcharter is a R wrapper for Highcharts javascript libray and its modules. Highcharts is very mature and flexible javascript charting library and it has a great and powerful API."<br>-Kunst, J. (package author)

* We have already seen `Highcharts` plots in ICJIA R&A Unit's online articles (e.g. Figure 1 and Figure 2 in [this article](http://www.icjia.state.il.us/articles/evaluation-of-illinois-multi-jurisdictional-drug-task-forces)).


The hchart() function
========================================================

```r
hchart(data, type, hcaes(x, y, ...))
```
* Quickly generates a hichchart plot
    * Comparable to `qplot()` in `ggplot2`
* `hcaes()` works like `aes()` in `ggplot2`


========================================================

```r
# using the same data
hchart(data, type = "scatter", hcaes(x = violentCrime, y = propertyCrime, group = region))
```

<iframe src="../interactive/hchart.html" style="display: block; margin: auto; min-height:500px; width:60%;"></iframe>


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


More on interactive plotting
========================================================
* `rAmCharts` is an R interface to the [`amCharts`](https://www.amcharts.com/products/) JavaScript library that offers interactive options for many common plot types and more. See `rAmCharts` [online documentation](https://datastorm-open.github.io/introduction_ramcharts/amBoxplot.html) for more.
* `chartjs` is an R interface to the [`Chart.js`](http://www.chartjs.org/) JavaScript library and offers six chart types (bar, line, pie, doughnut, radar, and polar area) for interactive plots. See `chartjs` [website](http://tutuchan.github.io/chartjs/) for mare.
* `dygraphs` is an R interface to the [dygraphs](http://rstudio.github.io/dygraphs/index.html) JavaScript library for interactive time-series plots. See `dygraph` [online documentation](http://rstudio.github.io/dygraphs/index.html) for more.


Other visualizations
========================================================
* [`visNetwork`](http://datastorm-open.github.io/visNetwork/) (wrapper for `vis.js`) and [`networkD3`](http://visjs.org/) are two popular packages for interactive visualization of network/graph data in R. Start with [`igraph`](http://igraph.org/r/) or [`tidygraph`](https://github.com/thomasp85/tidygraph) package to learn how to work with network objects in R
* [`wordcloud2`](https://cran.r-project.org/web/packages/wordcloud2/vignettes/wordcloud.html) (wrapper for `worldcloud2.js`) is a package for creating word clouds, a popular way to visualize text data.
* [`data.tree`](https://cran.r-project.org/web/packages/data.tree/vignettes/data.tree.html) is an R package for managing hierarchical data and tree structures. The pacakge also offers data visualization options for trees.


Questions?
========================================================
type: section
<img src="" title="plot of chunk unnamed-chunk-27" alt="plot of chunk unnamed-chunk-27" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href=""></a>
</p>


========================================================
References
<ul style="font-size: 0.6em; list-style-type:none">
  <li>Gohel, D. (n.d.). <a href="https://davidgohel.github.io/ggiraph/index.html"><span style="font-style:italic">ggiraph</span></a></li>
  <li>Kunst, J. (2017). <a href="http://jkunst.com/highcharter/index.html"><span style="font-style:italic">HIGHCHARTER</span></a></li>
  <li>Tennekes, M. (n.d.). <a href="https://cran.r-project.org/web/packages/tmap/vignettes/tmap-nutshell.html">"tmap in a nutshell"</a></li>
  <li>Tennekes, M. (n.d.). <a href="https://cran.r-project.org/web/packages/tmap/vignettes/tmap-modes.html">"tmap modes: plot and interactive view"</a></li>
</ul>
