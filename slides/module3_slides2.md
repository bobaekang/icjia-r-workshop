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
<a href="../notes/module3_notes2.html">
  <button type="button">Notes</button>
</a>
</div>
<link href="https://fonts.googleapis.com/css?family=Oswald" rel="stylesheet">


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 3: Data analysis with R (2)</h3>  
2018-03-28  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
<ul style="list-style: none">
<li>
  Part 1: Getting started with tidyverse</li>
<li style="color: #00061a; font-size: 1.1em; font-weight:700">
  Part 2: More on data analysis</li>
</div>


More on Data Analysis
========================================================
type:section
<img src="../images/more_data_analysis.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="35%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cdn4.iconfinder.com/data/icons/basic-dashboard-1/512/Basic_Dashboard_UI_fix_option_machine_tools-512.png">Iconfinder.com</a>
</div>


More on Data Analysis
========================================================
type:section
<div style="text-align: center;">
<ol>
<li>Working with strings</li>
<li>Working with date/datetimes</li>
<li>Importing/exporting data</li>
<ol>
</div>

Working with Strings
========================================================
type:section
<img src="../images/font_case.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="30%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cdn3.iconfinder.com/data/icons/metro-design/512/font_case-512.png">Iconfinder.com</a>
</div>


stringr from tidyverse
========================================================
type:section
<img src="../images/stringr.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.rstudio.com/">RStudio</a>
</div>


Key stringr functions
========================================================
* `str_to_upper()` `str_to_lower()` `str_to_title()`
* `str_trim()` `str_squish()`
* `str_c()`
* `str_detect()`
* `str_subset()`
* `str_sub()`

Note: Many `stringr` functions have base R alternatives


Convert letter case
========================================================

```r
str_to_upper(string, locale = "en")
str_to_lower(string, locale = "en")
str_to_title(string, locale = "en")
```
* `string` input is a character vector
    * Or something that can be coerced into a character vector
* The default `locale` is "en", for English
* `str_to_title()` capitalizes only the first letter of each word


========================================================
**Example**



========================================================
**Base R alternative**

```r
toupper(string) # equivalent to str_to_upper()
tolower(string) # equivalent to str_to_lower()
```


Trim whitespace
========================================================

```r
str_trim(string, side = c("both", "left", "right"))
str_squish(string)
```
* `string` input is a character vector
* `side` input determins which side of a string to trim
    * "both" trims whitespaces on both the beginning and the end
    * "left" trims whitespaces only on the beginning
    * "right" trims whitespaces only on the end


========================================================
**Example**




========================================================
**Base R alternative**

```r
trimws(x, which = c("both", "left", "right"))
```


Concatenate strings into one
========================================================

```r
str_c(..., sep = "", collapse = NULL)
```
* The first argument (`...`) is one more more character vectors
* 


========================================================
**Example**



========================================================
**Base R alternative**

```r
paste (..., sep = " ", collapse = NULL) # equivalent to str_c()
```


Detect a pattern
========================================================

```r
str_detect(string, pattern)
```
* `string` input is a character vector


========================================================
**Example**



========================================================
**Base R alternative**

```r
grepl(pattern, x, ...) # equivalent to str_detect()
```


Get strings/positions matching a pattern
========================================================

```r
str_subset(string, pattern)
str_which(string, pattern)
```
* `string` input is a character vector


========================================================
**Example**



========================================================
**Base R alternative**

```r
grep(pattern, x, value = TRUE, ...) # equivalent to str_subset()
grep(pattern, x, value = FALSE, ...) # equivalent to str_which()
```


Extract and replace substrings
========================================================

```r
str_sub(string, start = 1L, end = -1L)
str_sub(string, start = 1L, end = -1L, omit_na = FALSE) <- value
```
* The first argument is a character vector


========================================================
**Example**



========================================================
**Base R alternative**

```r
substr(x, start, stop)
substr(x, start, stop) <- value
```


More on stringr
========================================================
* `stringr` on [tidyverse.org](http://stringr.tidyverse.org/)
* `stringr` [CRAN documentation](https://cran.r-project.org/web/packages/stringr/stringr.pdf)
* `stringr` [Github repository](https://github.com/tidyverse/stringr)


Regular expression (regex)
========================================================
* What it is
* When to use/why useful


Regular expression in R
========================================================
* Character classes
* Metacharacters
* Groups
* Anchors
* Quantifiers


Character classes
========================================================

|Class                 |Description                                                   |
|:---------------------|:-------------------------------------------------------------|
|`[[:digit:]]` or `\d` |Any digits; i.e. `[0-9]`                                      |
|`\\D`                 |Non-digits; i.e. `[^0-9]`                                     |
|`[[:lower:]]`         |Lower-case letters; i.e. `[a-z]`                              |
|`[[:upper:]]`         |Upper-case letters; i.e. `[A-Z]`                              |
|`[[:alpha:]]`         |Alphabetic characters; `[A-z]`                                |
|`[[:alnum:]]`         |Alphanumeric characters; i.e. `[A-z0-9]`                      |
|`\\w`                 |Any Word characters; i.e. `[A-z0-9_]`                         |
|`\\W`                 |Non-word characters                                           |
|`[[:blank:]]`         |Space and tab                                                 |
|`[[:space:]]` or `\s` |Space, tab, vertical tab, newline, form feed, carriage return |
|`\\S`                 |Not space; i.e. `[^[:space:]]`                                |


Metacharacters
========================================================

|Metacharacter |Description     |
|:-------------|:---------------|
|`\n`          |New line        |
|`\r`          |Carriage return |
|`\t`          |Tab             |
|`\v`          |Vertical tab    |
|`\f`          |Form feed       |


Groups
========================================================

|Group    |Description                                                         |
|:--------|:-------------------------------------------------------------------|
|`.`      |Any character except `\n`                                           |
|&#124;   |Or, e.g. `(a`&#124;`b)`                                             |
|`[...]`  |List permitted characters, e.g. `[abc]`                             |
|`[a-z]`  |Specify character ranges                                            |
|`[^...]` |List excluded characters                                            |
|`(...)`  |Grouping, enables back referencing using `\\N` where `N` is integer |


Anchors
========================================================

|Anchor |Description                           |
|:------|:-------------------------------------|
|`^`    |Start of the string                   |
|`$`    |End of the string                     |
|`\\b`  |Empty string at either edge of a word |
|`\\B`  |NOT the edge of a word                |
|`\\<`  |Beginning of a word                   |
|`\\>`  |End of a word                         |


Quantifiers
========================================================

|Quantifier |Description                             |
|:----------|:---------------------------------------|
|`*`        |Matches at least 0 times                |
|`+`        |Matches at least 1 time                 |
|`?`        |Matches at most 1 time; optional string |
|`{n}`      |Matches extactly `n` times              |
|`{n, }`    |Matches at least `n` times              |
|`{, n}`    |Matches at most `n` times               |
|`{n, m}`   |Matches between `n` and `m` times       |


Examples
========================================================


More on regular expression
========================================================
* resources


Working with Dates/Datetimes
========================================================
type:section
<img src="../images/calendar.png" title="plot of chunk unnamed-chunk-27" alt="plot of chunk unnamed-chunk-27" width="30%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cdn4.iconfinder.com/data/icons/small-n-flat/24/calendar-512.png">Iconfinder.com</a>
</div>


Dates/Datetimes basics
========================================================
* basics


lubridate from tidyverse
========================================================
type:section
<img src="../images/lubridate.png" title="plot of chunk unnamed-chunk-28" alt="plot of chunk unnamed-chunk-28" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.rstudio.com/">RStudio</a>
</div>


Key lubridate functions
========================================================
* `as_date()` `as_datetime()`
* `year()`, `month()`, `day()`, `hour()`, ...
* `parse_date_time()` `fast_strptime()`
* `ymd_hms()`, `ymd()`, ...

Convert to a date or date-time
========================================================

```r
as_date(x, tz = NULL, origin = lubridate::origin)
as_datetime(x, tz = NULL, origin = lubridate::origin)
```
* `x` is a vector of POSIXt, numeric or character objects
* `tz` is a time zone name
* `origin` is a Date object or something that can be coerced into a Date object

========================================================
**Example**



========================================================
**Base R alternative**



Get/set time component
========================================================

```r
year(x)
year(x) <- value
```
* `x` is a date-time object
* `value` is a numeric object


========================================================

|Function   |Description                                |
|:----------|:------------------------------------------|
|`year()`   |Get/set year component of a date-time      |
|`month()`  |Get/set months component of a date-time    |
|`week()`   |Get/set weeks component of a date-time     |
|`day()`    |Get/set days component of a date-time      |
|`hour()`   |Get/set hours component of a date-time     |
|`minute()` |Get/set minutes component of a date-time   |
|`second()` |Get/set seconds component of a date-time   |
|`tz()`     |Get/set time zone component of a date-time |
* a
* b


========================================================
**Example**



Parse date-time
========================================================

```r
parse_date_time(x, orders, tz = "UTC", truncated = 0, locale = Sys.getlocale("LC_TIME"), exact = FALSE, drop = FALSE, ...)
fast_strptime(x, format, tz = "UTC", lt = TRUE, cutoff_2000 = 68L)
```
* `x` is a character or numeric vector of dates


========================================================
**Example**




========================================================
**Base R alternative**



Quickly parse date-time
========================================================

```r
ymd_hms(..., quiet = FALSE, tz = NULL, ...)
ymd(..., quiet = FALSE, tz = "UTC", ...)
```
* The first `...` argument is ...


========================================================
<br>

|Date-time   |Date only |Time only |
|:-----------|:---------|:---------|
|`ymd_hms()` |`ymd()`   |`hms()`   |
|`ymd_hm()`  |`ydm()`   |`hm()`    |
|`ymd_h()`   |`mdy()`   |`ms()`    |
|`mdy_hms()` |`myd()`   |          |
|`mdy_hm()`  |`dmy()`   |          |
|`mdy_h()`   |`dym()`   |          |
|`dmy_hms()` |          |          |
|`dmy_hm()`  |          |          |
|`dmy_h()`   |          |          |

***
<br>
* `y` is year
* first `m` is month
* `d` is date
* `h` is hour
* second `m` is minute
* `s` is second


More on lubridate
========================================================
* `lubridate` on [tidyverse.org](http://lubridate.tidyverse.org/)
* `lubridate` [CRAN documentation](https://cran.r-project.org/web/packages/lubridate/lubridate.pdf)
* `lubridate` [Github repository](https://github.com/tidyverse/lubridate)


Importing/Exporting Data
========================================================
type:section
<img src="../images/data_transfer.png" title="plot of chunk unnamed-chunk-40" alt="plot of chunk unnamed-chunk-40" width="30%" style="box-shadow: none; display: block; margin: auto;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia Commons</a>
</p>


Comma-separated values (.csv)
========================================================
* `readr` package (tidyverse)
    * `read_csv()`
    * `write_csv()`
* `data.table` package
    * `fread()`
    * `fwrite()`


Using readr
========================================================

```r
read_csv(file, col_names = TRUE, col_types = NULL, na = c("", "NA"), trim_ws = TRUE, skip = 0, n_max = Inf, guess_max = min(1000, n_max), ...)
write_csv(x, path, na = "NA", append = FALSE, col_names = !append)
```
* `file` is a path to the excel file to import
* `x` is a data object to export
* `path` is a path to the directory where the exported data will be created 
* The output of`read_csv()` is a `tibble` object
* The output of `write_csv()` is a .csv file


Using data.table
========================================================

```r
fread(input, file, nrows=-1L, header="auto", na.strings="NA", stringsAsFactors=FALSE, skip=0L, colClasses=NULL, col.names,
strip.white=TRUE, fill=FALSE, ...)
fwrite(x, file = "", append = FALSE, quote = "auto", sep = ",", na = "", row.names = FALSE, col.names = TRUE, ...)
```
* The output of `fread` is a `data.table` object
* The output of `fwrite` is a .csv file in a directory


========================================================
**Base R alternative**

```r
read.csv(file,  header = TRUE, sep = ",", quote = "\"", dec = ".", fill = TRUE, ...)
write.csv(x, file = "", append = FALSE, quote = TRUE, sep = ",", row.names = TRUE, col.names = TRUE, ...)
```


Excel spreadsheets (.xlsx/.xls)
========================================================
* `readxl` package (tidyverse)
    * `read_excel()`
    * `read_xls()` `read_xlsx()`


========================================================

```r
read_excel(path, sheet = NULL, range = NULL, col_names = TRUE, col_types = NULL, na = "", trim_ws = TRUE, skip = 0, n_max = Inf, guess_max = min(1000, n_max))
read_xls(path, ...)
read_xlsx(path, ...)
```
* The output is a `tibble` object


More on readxl
========================================================
* `readxl` on [tidyverse.org](http://readxl.tidyverse.org/)
* `readxl` [CRAN documentation](https://cran.r-project.org/web/packages/readxl/readxl.pdf)
* `readxl` [Github repository](https://github.com/tidyverse/readxl)


SPSS data files (.sav)
========================================================
* `haven` package (tidyverse)
    * `read_sav()` `read_spss()`
    * `write_sav()`
* `haven` also has functions to import/export the file formats of other statistical softwares
    * STATA
    * SAS


========================================================

```r
read_sav(file, user_na = FALSE)
read_spss(file, user_na = FALSE)
write_sav(data, path)
```
* The output of `read_sav()` is a `tibble` object
    * `read_spss()` is a simple alias for `read_sav()`
* The output of `write_sav()` is an SPSS data file


More on haven
========================================================
* `haven` on [tidyverse.org](http://haven.tidyverse.org/)
* `haven` [CRAN documentation](https://cran.r-project.org/web/packages/haven/haven.pdf)
* `haven` [Github repository](https://github.com/tidyverse/haven)


A "fast-on-disk" data frame storage (.feather) 
========================================================
* `feather` package (tidyverse)
    * `read_feather()`
    * `write_feather()`
* The .feather format is also supported in Python!


========================================================

```r
read_feather(path, columns = NULL)
write_feather(x, path)
```
* The output of `read_feather()` is a `tibble` object
* The output of `write_feather()` is a feather file


More on feather
========================================================
* Wickham, H. (2016), ["Feather: A Fast On-Disk Format for Data Frames for R and Python, powered by Apache Arrow"](https://blog.rstudio.com/2016/03/29/feather/). *RStudio Blog*.
* `feather` [CRAN documentation](https://cran.r-project.org/web/packages/haven/haven.pdf)


Questions?
========================================================
type: section
<img src="https://cdn.dribbble.com/users/433975/screenshots/1627606/question-mark-dribbble.gif" title="plot of chunk unnamed-chunk-47" alt="plot of chunk unnamed-chunk-47" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://dribbble.com/shots/1627606-question-mark">Joel Ploz</a>
</p>


References
========================================================
<ul style="font-size: 0.6em; list-style-type:none">
  <li>Grolemund, G. & Wickham, H. (2017). <a href="http://r4ds.had.co.nz/"><span style="font-style:italic">R for Data Science</span></a>.</li>
  <li>RStudio. (2017). <a href="https://www.rstudio.com/resources/cheatsheets/">"Dates and Times Cheat Shee"</a>.</li>
  <li>RStudio. (2017). <a href="https://www.rstudio.com/resources/cheatsheets/">"Work with Strings Cheat Sheet"</a>.</li>
  <li>Tidyverse. (n.d.). <a href="http://haven.tidyverse.org/index.html"><span style="font-style:italic">haven.tidyverse.org</span></a></li>
  <li>Tidyverse. (n.d.). <a href="http://lubridate.tidyverse.org/index.html"><span style="font-style:italic">lubridate.tidyverse.org</span></a></li>
  <li>Tidyverse. (n.d.). <a href="http://readr.tidyverse.org/index.html"><span style="font-style:italic">readr.tidyverse.org</span></a></li>
  <li>Tidyverse. (n.d.). <a href="http://readxl.tidyverse.org/index.html"><span style="font-style:italic">readxl.tidyverse.org</span></a></li>
  <li><a href="#"></a></li>
  <li>Tidyverse. (n.d.). <a href="http://stringr.tidyverse.org/index.html"><span style="font-style:italic">stringr.tidyverse.org</span></a></li>
</ul>
