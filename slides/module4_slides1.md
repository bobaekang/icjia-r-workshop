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
Source: Wickham, H. (2010). "A Layered Grammar of Graphics."
</p>



"The Grammar of Graphics"
========================================================
> "The grammar of graphics takes us beyond a limited set of charts (words) to an almost unlimited world of graphical forms (statements). <br>-Wilkinson, L. (2005), p.1"


Wilkinson's "grammar"
========================================================
Wilkinson's idea is implemented in the Graphics Production Language (GPL) and has the following components:

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
> This article proposes an alternative parameterization of the [graphical] grammar, based around the idea of building up a graphic from multiple layers of data. The grammar differs from Wilkinson's in its arrangement of the components, the development of a hierarchy of defaults, and in that it is embedded inside another programming language.<br>-Wickham, H. (2010), p.4


Comparison
========================================================
<img src="../images/grammar-of-graphics2.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="60%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align: center; color: #777;">
Source: Wickham, H. (2010). "A Layered Grammar of Graphics."
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

```r
# limit x axis to 2000; this removes points with violentCrime > 2000
plot + xlim(0, 2000)
```

![plot of chunk unnamed-chunk-21](module4_slides1-figure/unnamed-chunk-21-1.png)


========================================================
**Position scales (discrete)**

```r
# replace * with x or y
scale_*_discrete(name, breaks, labels, limits, ...)
```

**Common scale_* arguments**

|Argument |Description                                                                            |
|:--------|:--------------------------------------------------------------------------------------|
|`name`   |a name of the scale, used as the axis label or the legend title                        |
|`breaks` |controls the breaks in the guide, which can be a character vector                      |
|`labels` |controls the lable for each break; its input must be the same length as `breaks` input |
|`limits` |a character vector specifying the data range for the scale                             |


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

```r
# apply the log 10 scale to the y-axis 
plot + scale_y_log10()
```

![plot of chunk unnamed-chunk-26](module4_slides1-figure/unnamed-chunk-26-1.png)


========================================================
**Custom scale "manuals"**

```r
scale_*_manual(name, breaks, labels, limits, ..., values)
```
* Scale manuals is used to create my own discrete scale
* "Manual" is available for:
    * `colour`
    * `fill`
    * `size`
    * `shape`
    * `linetype`
    * `alpha`


========================================================

```r
plot + scale_color_manual(
  name = "",
  breaks = c("Central", "Northern", "Southern"),
  labels = c("Central region", "Northern region", "Southern region"),
  values = c("#00ffff", "#ffff00", "#ff00ff")
)
```

![plot of chunk unnamed-chunk-28](module4_slides1-figure/unnamed-chunk-28-1.png)

========================================================
**Other custom scales**

`ggplot2` offers many more functions to customize scales.

See the full documentation on scales [here](http://ggplot2.tidyverse.org/reference/#section-scales).


Guides
========================================================

```r
guides(...)
guide_legend(...)
```
* `guides` can be used to set (or remove) guides for each scale
* `guide_legend()` can be used to specify the legend components for each visual properties (e.g. `colour`, `size`, `alpha`, etc.)
    * `guide_legned()` is used as an input for each scale argument in `guide()`


========================================================

```r
plot + guides(
  colour = guide_legend(title = "Region", title.position = "bottom"),
  size = FALSE
)
```

![plot of chunk unnamed-chunk-30](module4_slides1-figure/unnamed-chunk-30-1.png)



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
# default plot
plot
```

![plot of chunk unnamed-chunk-33](module4_slides1-figure/unnamed-chunk-33-1.png)


========================================================

```r
# with coord_flip()
plot + coord_flip()
```

![plot of chunk unnamed-chunk-34](module4_slides1-figure/unnamed-chunk-34-1.png)


========================================================

```r
# pie chart with coord_polar()
ggplot(ispcrime %>% filter(county == "Cook") %>% gather("type", "count", murder:aggAssault), aes("", count, fill = type)) +
  geom_col(width = 1) +
  coord_polar("y")
```

![plot of chunk unnamed-chunk-35](module4_slides1-figure/unnamed-chunk-35-1.png)


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
**facet formulas**

|Type |Formula               |Description                          |
|:----|:---------------------|:------------------------------------|
|Grid |`facet_grid(. ~ x)`   |Facet horizontally across `x` values |
|Grid |`facet_grid(y ~ .)`   |Facet vertically across `y` values   |
|Grid |`facet_grid(y ~ x)`   |Facet 2-dimensionally                |
|Wrap |`facet_wrap(~ x)`     |Facet across `x` values              |
|Wrap |`facet_wrap(~ x + y)` |Facet across `x` and `y` values      |


========================================================




```r
# facet_grid horizontal
plot + facet_grid(. ~ region)
```

![plot of chunk unnamed-chunk-39](module4_slides1-figure/unnamed-chunk-39-1.png)


========================================================

```r
# facet_grid horizontal with free scales
plot + facet_grid(. ~ region, scales = "free")
```

![plot of chunk unnamed-chunk-40](module4_slides1-figure/unnamed-chunk-40-1.png)


========================================================

```r
# facet_grid vertical
plot + facet_grid(year ~ .)
```

![plot of chunk unnamed-chunk-41](module4_slides1-figure/unnamed-chunk-41-1.png)


========================================================

```r
# facet_grid two-dimensional
plot + facet_grid(year ~ region)
```

![plot of chunk unnamed-chunk-42](module4_slides1-figure/unnamed-chunk-42-1.png)


========================================================

```r
# facet wrap
plot + facet_wrap(~ year)
```

![plot of chunk unnamed-chunk-43](module4_slides1-figure/unnamed-chunk-43-1.png)


========================================================

```r
# facet wrap with specified nrow/ncol
plot + facet_wrap(~ year, ncol = 3)
```

![plot of chunk unnamed-chunk-44](module4_slides1-figure/unnamed-chunk-44-1.png)


========================================================

```r
# facet wrap with multiple variables
plot + facet_wrap(~ year + region, ncol = 3)
```

![plot of chunk unnamed-chunk-45](module4_slides1-figure/unnamed-chunk-45-1.png)


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
* `ggthemes` pacakge offers additional predefined themes


========================================================


```r
plot + theme_gray() # this is the default
```

![plot of chunk unnamed-chunk-48](module4_slides1-figure/unnamed-chunk-48-1.png)


========================================================

```r
plot + theme_bw()
```

![plot of chunk unnamed-chunk-49](module4_slides1-figure/unnamed-chunk-49-1.png)


========================================================

```r
plot + theme_linedraw()
```

![plot of chunk unnamed-chunk-50](module4_slides1-figure/unnamed-chunk-50-1.png)


========================================================

```r
plot + theme_light()
```

![plot of chunk unnamed-chunk-51](module4_slides1-figure/unnamed-chunk-51-1.png)


========================================================

```r
plot + theme_dark()
```

![plot of chunk unnamed-chunk-52](module4_slides1-figure/unnamed-chunk-52-1.png)


========================================================

```r
plot + theme_minimal()
```

![plot of chunk unnamed-chunk-53](module4_slides1-figure/unnamed-chunk-53-1.png)


========================================================

```r
plot + theme_classic()
```

![plot of chunk unnamed-chunk-54](module4_slides1-figure/unnamed-chunk-54-1.png)


========================================================

```r
plot + theme_void()
```

![plot of chunk unnamed-chunk-55](module4_slides1-figure/unnamed-chunk-55-1.png)


========================================================

```r
plot + ggthemes::theme_economist()
```

![plot of chunk unnamed-chunk-56](module4_slides1-figure/unnamed-chunk-56-1.png)


========================================================

```r
plot + ggthemes::theme_fivethirtyeight()
```

![plot of chunk unnamed-chunk-57](module4_slides1-figure/unnamed-chunk-57-1.png)


========================================================

```r
plot + ggthemes::theme_hc()
```

![plot of chunk unnamed-chunk-58](module4_slides1-figure/unnamed-chunk-58-1.png)


========================================================

```r
plot + ggthemes::theme_wsj()
```

![plot of chunk unnamed-chunk-59](module4_slides1-figure/unnamed-chunk-59-1.png)


========================================================

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
* Read the full documentation [here](http://ggplot2.tidyverse.org/reference/theme.html)


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
<img src="https://media.tenor.com/images/4ea52aade3c0ee8cdf2ec81f0dae34ff/tenor.gif" title="plot of chunk unnamed-chunk-61" alt="plot of chunk unnamed-chunk-61" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://tenor.com/view/mario-question-block-super-mario-gif-7732885">tenor.com</a>
</p>


========================================================
References
<ul style="font-size: 0.6em; list-style-type:none">
  <li>Grolemund, G. & Wickham, H. (2017).<a href="http://r4ds.had.co.nz/data-visualisation.html">"Data visualization"</a>. <span style="font-style:italic">R for Data Science</span></li>
  <li>Tidyverse. (n.d.). <a href="http://ggplot2.tidyverse.org/reference">"References"</a>. <span style="font-style:italic">ggplot2.tidyverse.org</span></li>
  <li>Wickham, H. (2010). "A Layered Grammar of Graphics". <span style="font-style:italic">Journal of Computational and Graphical Statistics 19(1)</span>:3-28.</li>
  <li>Wilkinson, L. (2005). <span style="font-style:italic">The Grammar of Graphics</span>.</li>
  <li>Wilkinson, L., Rope, D., Carr, D. * Rubin, M. (2000). "The Language of Graphics". <span style="font-style:italic">Journal of Computational and Graphical Statistics 9(3)</span>:530-543.</li>
</ul>


========================================================
type: section
<img src="../images/pause.png" title="plot of chunk unnamed-chunk-62" alt="plot of chunk unnamed-chunk-62" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>

