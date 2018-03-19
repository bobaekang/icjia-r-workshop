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
<a href="../notes/module4_notes1.html">
  <button type="button">Notes</button>
</a>
</div>
<link href="https://fonts.googleapis.com/css?family=Oswald" rel="stylesheet">





# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 4: Data visualization with R (1)</h3>  
2018-04-04  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
<ul style="list-style: none">
<li style="color: #00061a; font-size: 1.1em; font-weight:700">
  Part 1: The Grammar of Graphics</li>
<li>
  Part 2: Maps and Interactive Plots</li>
</div>


The Grammar of Graphics 
========================================================
type: section
<img src="../images/grammar-of-graphics1.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: Wickham, Hadley. 2010. "A Layered Grammar of Graphics." Journal of Computational and Graphical Statistics 19(1):3-28.
</p>


Graphical grammars
========================================================
type: section


"The Grammar of Graphics"
========================================================
* Wilkinson, Anand and Grossman (2005)

> some quote 


Wilkinson's "grammar"
========================================================
* Data
* Transformation
* Element
* Scale
* Guide
* Coordinate system


ggplot2 package
========================================================
type: section
<img src="../images/ggplot2.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="20%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: <a href="https://d33wubrfki0l68.cloudfront.net/0ab849ed51b0b866ef6895c253d3899f4926d397/dbf0f/images/hex-ggplot2.png">tidyverse.com</a>
</p>


Motivation
========================================================
* Hadly Wickham (2010)

> some quote


Comparison
========================================================
<img src="../images/grammar-of-graphics2.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: Wickham, Hadley. 2010. "A Layered Grammar of Graphics." Journal of Computational and Graphical Statistics 19(1):3-28.
</p>


Basic components
========================================================
* Data and aesthetic mappings
* Geometic objects
* Labels


Data and aesthetic mappings
========================================================

```r
# data and aesthetics
ggplot(data, aes(x, y, ...))
```
* `data` is a data frame object (or its variant)
* `aes()` defines aesthetic mappings
    * `x` and `y` are columns in `data` input to be mapped to the x-axis and y-axis
    
    
========================================================
**`aes` components**

|`aes` component |Description        |Input                                                  |
|:---------------|:------------------|:------------------------------------------------------|
|`colour`        |Border color       |Name (`"red"`), rgb specification (`#FF0000`), or `NA` |
|`fill`          |Fill color         |Name (`"red"`), rgb specification (`#FF0000`), or `NA` |
|`shape`         |Shape of a point   |An integer value 0 to 24, or `NA`                      |
|`linetype`      |Linetype           |An integer value 0 to 6                                |
|`size`          |Size of line/point |A non-negative numeric value                           |
|`alpha`         |Transparency       |A numeric value 0 to 1                                 |


========================================================
<br>
**`shape` values**
<br>
<img src="../images/ggplot2_shapes.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: Tidyverse. (n.d.). <a href="http://ggplot2.tidyverse.org/articles/ggplot2-specs.html">"Aesthetic specifications"</a>. <span style="font-style:italic">ggplot2.tidyverse.org</span>.
</p>


========================================================
<br>
**`linetype` values**
<br>
<img src="../images/ggplot2_linetypes.png" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: Tidyverse. (n.d.). <a href="http://ggplot2.tidyverse.org/articles/ggplot2-specs.html">"Aesthetic specifications"</a>. <span style="font-style:italic">ggplot2.tidyverse.org</span>.
</p>


Geometric objects
========================================================

```r
# adding one or more geometric objects
ggplot(data, aes(x, y, ...)) +
  geom_object()

# with geom_specific `aes`
ggplot(data) +
  geom_object(aes(x, y, ...))
```
* There are many "geom" objects for different graph types:
* A `geom` object can take its own `aes` input
    * All `aes` specifications can be directly provided for each geometric object


========================================================
**Basic `geom` objects**

|geom                       |Description              |Input                           |
|:--------------------------|:------------------------|:-------------------------------|
|`geom_histogram`           |Histograms               |Continous `x`                   |
|`geom_bar`                 |Bar plot with frequncies |Discrete `x`                    |
|`geom_col`                 |Bar plot with values     |Discrete x and continuous `y`   |
|`geom_point`               |Points/scattorplots      |Discrete/continuous `x` and `y` |
|`geom_jitter`              |Jittered points          |Discrete/continuous `x` and `y` |
|`geom_line`                |Line plots               |Discrete/continuous x and y     |
|`geom_abline`              |Reference line           |`intercept` and `slope` value   |
|`geom_hline`, `geom_vline` |Reference lines          |`xintercept` or `yintercept`    |


========================================================

```r
# geom histogram example
data <- ispcrime %>% filter(year == 2015, county != "Cook")
ggplot(data, aes(violentCrime)) +
  geom_histogram()
```

![plot of chunk unnamed-chunk-10](module4_slides1-figure/unnamed-chunk-10-1.png)


========================================================

```r
# geom col example
data <- ispcrime %>% filter(county == "Cook") %>% gather("type", "count", murder:aggAssault)
ggplot(data, aes(type, count, fill = type)) +
  geom_col(width = 0.8)
```

![plot of chunk unnamed-chunk-11](module4_slides1-figure/unnamed-chunk-11-1.png)


========================================================

```r
# geom point example
data <- ispcrime %>% filter(county != "Cook") %>% left_join(regions)
ggplot(data, aes(violentCrime, propertyCrime, color = region)) +
  geom_point(aes(size = violentCrime + propertyCrime), alpha = .5)
```

![plot of chunk unnamed-chunk-12](module4_slides1-figure/unnamed-chunk-12-1.png)


========================================================

```r
# geom line example
data <- ispcrime %>% filter(county == "Cook")
ggplot(data, aes(year, violentCrime)) +
  geom_line(color = "maroon", size = 1.5) +
  geom_hline(yintercept = mean(data$violentCrime), linetype = "longdash")
```

![plot of chunk unnamed-chunk-13](module4_slides1-figure/unnamed-chunk-13-1.png)


========================================================
**Other `geom` objects**

|geom                      |Description                         |Input                   |
|:-------------------------|:-----------------------------------|:-----------------------|
|`geom_density`            |Smoothed density estimates          |Continous `x`           |
|`geom_density2d`          |Contours of a 2-d density estimates |Continous `x`           |
|`geom_boxplot`            |Box plots                           |Disc. `x` and cont. `y` |
|`geom_smooth`             |Smoothed conditional means          |                        |
|`geom_text`, `geom_label` |Text                                |                        |
|`geom_polygon`            |Polygons                            |                        |

* See [the official reference page](http://ggplot2.tidyverse.org/reference/index.html#section-layer-geoms) for the full list of `geom`s.


Labels
========================================================

```r
# adding labels
plot + labs(title, subtitle, caption, x, y, ...)
```
* Each argument of `labs()` take a character vector of length 1
    * `title` and `subtitle` appear at the top-left.
    * `caption` appears at the bottom-right
    * `x` and `y` are for x-axis and y-axis names
* Adjusting the position and style of labels is handled via `theme()`


========================================================
**alternatively ...**

```r
plot +
  xlab(label) +
  ylab(label) +
  ggtitle(label, subtitle = NULL)
```
* Each argument of the `labs()` can be added with a separate function.
    * `xlab()` is for x-axis name
    * `ylab()` is for y-axis name
    * `ggtitle()` is for plot title and subtitle


========================================================



```r
# a generic example with title, subtitle, and axes names
plot +
  labs(
    title = "This is plot title", subtitle = "This is plot subtitle",
    x = "x-axis here", y = "y-axis here",
    caption = "(and caption...)"
  )
```

![plot of chunk unnamed-chunk-18](module4_slides1-figure/unnamed-chunk-18-1.png)


========================================================

```r
# a title with mathematical expressions
plot +
  ggtitle(label = expression(paste("Another plot title with math expressions like ", pi, " and ", sigma^{2})))
```

![plot of chunk unnamed-chunk-19](module4_slides1-figure/unnamed-chunk-19-1.png)


Additional components
========================================================
* Scales
* Guides
* Facets
* Coordinate systems
* Themes


Scales
========================================================
* Scales control "the details of how data values are translated to visual properties"
* Scale limits
* Position scales (discrete, continuous, datetime)
* Others


========================================================
**Scale limits**

```r
plot +
  xlim(...) +
  ylim(...) +
  lims(...)
```
* `xlim()` changes x-axis limits
* `ylim()` changes y-axis limits
* `lims()` is a general function to change limits
* `...` in all three functions is a name-value pair, where the name is an aesthetic and the value is either a length-2 numeric, a character, a factor, or a datetime 

========================================================
**Position scales (discrete)**

```r
# replace * with x or y
scale_*_discrete(name, breaks, labels, limits, ...)
```
* `name`
* `breaks`
* `labels`
* `limits`


========================================================
**Position scales (continuous)**

```r
# replace * with x or y
scale_*_continuous(name, breaks, labels, limits, ...)

scale_*_log10(...)

scale_*_sqrt(...)

scale_*_reverse(...)
```


========================================================
**Position scales (datetime)**

```r
# replace * with x or y
scale_*_date(name, breaks, labels, limits, ...)

scale_*_datetime(...)

scale_*_time(...)
```


========================================================
**Custom scale "manuals"**

```r
scale_*_manual(name, breaks, labels, limits, ...)
```
* "Manual" is available for:
    * `colour`
    * `fill`
    * `size`
    * `shape`
    * `linetype`
    * `alpha`


Guides
========================================================



========================================================
some examples here



Coordinate systems
========================================================

```r
plot + coord_cartesian()
```

* The default system is `coord_cartesian`
  * Can be tweatked with: `coord_fixed`, `coord_flip`, `coord_map` and `coord_trans`
* An alternative, polar coordiante system can be used with `coord_polar`
  * Most commonly used for creating a pie chart


========================================================

```r
# coord flip example
```


========================================================

```r
# pie chart example using coord polar
```


Facets
========================================================

```r
plot + facet_grid(facets, scales, ...)
plot + facet_wrap(facets, nrow, ncol, scales, ...)
```
* A great way to visualize multi-dimensional data as a series of 2D graphes
* `facets` input takes a "formula" according to which the faceting is applied

========================================================
**facet_grid vs facet_wrap**

* `facet_grid()` and `facet_wrap()` are mostly similar to each other
* However, they differs where:
    * `facet_grid()` facets the plot with a variable in a single direction (horizontal or vertical)
    * `facet_wrap()` simply places the facets next to each other and wraps them accoridng to the provided number of columns and/or rows.


========================================================

```r
# facet_grid horizontal
```


========================================================

```r
# facet_grid horizontal 2 with free scales
```


========================================================

```r
# facet_grid vertical
```


========================================================

```r
# facet_grid two-dimensional
```


========================================================

```r
# facet wrap
```


========================================================

```r
# facet wrap 2 with specified nrow/ncol 
```


Themes
========================================================

```r
# themes
plot + theme_gray(base_size = 11, base_family = "")
```
* `ggplot2` offers several predefined themes
    * the default theme is `theme_gray()` (or `theme_grey()`)
    * `base_size` controls the base font size
    * `base_family` controls the base font family ("serif", "sans", "mono")
* `ggthemes` pacakge offers more predefined themes


========================================================



```r
plot + theme_bw()
```

![plot of chunk unnamed-chunk-38](module4_slides1-figure/unnamed-chunk-38-1.png)


========================================================

```r
plot + theme_linedraw()
```

![plot of chunk unnamed-chunk-39](module4_slides1-figure/unnamed-chunk-39-1.png)


========================================================

```r
plot + theme_light()
```

![plot of chunk unnamed-chunk-40](module4_slides1-figure/unnamed-chunk-40-1.png)


========================================================

```r
plot + theme_dark()
```

![plot of chunk unnamed-chunk-41](module4_slides1-figure/unnamed-chunk-41-1.png)


========================================================

```r
plot + theme_minimal()
```

![plot of chunk unnamed-chunk-42](module4_slides1-figure/unnamed-chunk-42-1.png)


========================================================

```r
plot + theme_classic()
```

![plot of chunk unnamed-chunk-43](module4_slides1-figure/unnamed-chunk-43-1.png)


========================================================

```r
plot + theme_void()
```

![plot of chunk unnamed-chunk-44](module4_slides1-figure/unnamed-chunk-44-1.png)


========================================================
**Fine-tuning the plot with `theme`**

```r
plot + theme(...)
```
* `theme` has arguments to control and motify individual components of a plot theme:
    * all line, rectangular, text and title elements
    * aspect ratio of the panel
    * axis title, text, ticks, and lines
    * legend background, margin, text, title, position, and more
    * panel aspect ratio, border, and grid lines
    * and more


========================================================

```r
# with an elaborate theme with guide
```


ggplot2 resources
========================================================
* `ggplot2` official [reference](http://ggplot2.tidyverse.org/reference/index.html)
* ["Data Visualization Cheat Sheet"](https://github.com/rstudio/cheatsheets/raw/master/data-visualization-2.1.pdf) by RStudio
* [*R Graphics Cookbook*](http://www.cookbook-r.com/Graphs/) by Winston Chang
* [`ggplot2` tutorials in *r-statistics.co*](http://r-statistics.co/ggplot2-Tutorial-With-R.html) by Selva Prabhakaran
* Extending `ggplot2`:
    * [*`ggplot2` extentions*](http://www.ggplot2-exts.org/index.html) website by Daniel Emaasit


Questions?
========================================================
type: section
<img src="https://media.tenor.com/images/4ea52aade3c0ee8cdf2ec81f0dae34ff/tenor.gif" title="plot of chunk unnamed-chunk-47" alt="plot of chunk unnamed-chunk-47" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://tenor.com/view/mario-question-block-super-mario-gif-7732885">tenor.com</a>
</p>


========================================================
References
<ul style="font-size: 0.6em; list-style-type:none">
  <li><a href="#">1</a></li>
  <li><a href="#">2</a></li>
  <li><a href="#">3</a></li>
  <li><a href="#"></a></li>
</ul>


========================================================
type: section
<img src="../images/pause.png" title="plot of chunk unnamed-chunk-48" alt="plot of chunk unnamed-chunk-48" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>

