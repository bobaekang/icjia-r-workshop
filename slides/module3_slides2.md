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

<small>Note: Many `stringr` functions have base R alternatives</small>


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

```r
str_to_upper("hello world")
```

```
[1] "HELLO WORLD"
```

```r
str_to_lower("HELLO WORLD")
```

```
[1] "hello world"
```

```r
str_to_title("hello WORLD")
```

```
[1] "Hello World"
```


========================================================
**Base R alternative**

```r
# equivalent to str_to_upper()
toupper(string)

# equivalent to str_to_lower()
tolower(string)
```


Trim whitespace
========================================================

```r
str_trim(string, side = c("both", "left", "right"))
str_squish(string)
```
* `string` input is a character vector
* `side` input determines which side of a string to trim
    * "both" trims whitespaces on both the beginning and the end
    * "left" trims whitespaces only on the beginning
    * "right" trims whitespaces only on the end


========================================================
**Example**

```r
str_trim("  trim both  ", side = "both")
```

```
[1] "trim both"
```

```r
str_trim("  trim left only  ", side = "left")
```

```
[1] "trim left only  "
```

```r
str_trim("  trim right only  ", side = "right")
```

```
[1] "  trim right only"
```

```r
str_squish("  whitespaces all    over the  place   ")
```

```
[1] "whitespaces all over the place"
```


========================================================
**Base R alternative**

```r
# equivalent to str_trim()
trimws(x, which = c("both", "left", "right"))
```


Concatenate strings into one
========================================================

```r
str_c(..., sep = "", collapse = NULL)
```
* The first argument (`...`) is one more more character vectors
* `sep` is a separator string between input vectors; default value is none (`""`).
* `collapse` is an optional string used to combined input vectors into a single string


========================================================
**Example**

```r
str_c(c("one", "two"), c("plus three", "minus four"), sep = " ")
```

```
[1] "one plus three" "two minus four"
```

```r
str_c(c("one", "two", "three"), "plus four", sep = " ")
```

```
[1] "one plus four"   "two plus four"   "three plus four"
```

```r
str_c(c("one", "two", "three"), collapse = " plus ")
```

```
[1] "one plus two plus three"
```

```r
str_c(c("one", "two", "three"), "plus four", sep = " ", collapse = " and ")
```

```
[1] "one plus four and two plus four and three plus four"
```


========================================================
**Base R alternative**

```r
# equivalent to str_c()
paste (..., sep = " ", collapse = NULL)
```


Detect a pattern
========================================================

```r
str_detect(string, pattern)
```
* `string` input is a character vector
* `pattern` input is a character vector of length 1 that is a pattern to look for. A pattern input can include regualr expressions.
* Output is a boolean vector of the same length (`TRUE` or `FALSE`)

<small>Note: We will discuss regular expressions later.</small>

========================================================
**Example**

```r
str = c("I like apple", "You like apple", "Apple, I like")
pat = "I like"
str_detect(str, pat)
```

```
[1]  TRUE FALSE  TRUE
```

**Base R alternative**

```r
# equivalent to str_detect()
grepl(pattern, x, ...)
```


Get strings/positions matching a pattern
========================================================

```r
str_subset(string, pattern)
str_which(string, pattern)
```
* `string` input is a character vector
* `pattern` input is a character vector of length 1 that is a pattern to look for. A pattern input can include regualr expressions.
* `str_subset()` returns the matching strings while `str_which()` returns the index for the matches


========================================================
**Example**

```r
str = c("I like apple", "You like apple", "Apple, I like")
pat = "I like"
str_subset(str, pat)
```

```
[1] "I like apple"  "Apple, I like"
```

```r
str_which(str, pat)
```

```
[1] 1 3
```


========================================================
**Base R alternative**

```r
# equivalent to str_subset()
grep(pattern, x, value = TRUE, ...)

# equivalent to str_which()
grep(pattern, x, value = FALSE, ...)
```


Extract and replace substrings
========================================================

```r
str_sub(string, start = 1L, end = -1L)
str_sub(string, start = 1L, end = -1L, omit_na = FALSE) <- value
```
* `string` input is a character vector
* `start` and `end` are integer vectors
    * `start` is the position of the first substring character; default is the first character
    * `end` is the position of the last substring character; default is the last character
* Output is a character vector of substring from `start` to `end`.
* `str_sub()` can be used to replace substrings when used with the assignment operator (`<-`)


========================================================
**Example**

```r
str <- "Hello world"
str_sub(str, start = 7)
```

```
[1] "world"
```

```r
str_sub(str, end = 5) <- "Hi"
str
```

```
[1] "Hi world"
```


========================================================
**Base R alternative**

```r
# equivalent to str_sub()
substr(x, start, stop)

# equivalent to str_sub() <- value
substr(x, start, stop) <- value
```


More on stringr
========================================================
* `stringr` on [tidyverse.org](http://stringr.tidyverse.org/)
* `stringr` [CRAN documentation](https://cran.r-project.org/web/packages/stringr/stringr.pdf)
* `stringr` [Github repository](https://github.com/tidyverse/stringr)


Regular expression (regex)
========================================================
> "Regular expressions are a concise and flexible tool for describing patterns in strings." <br>-*stringr.tidyverse.org*

* Regex allows us to use more complex and dynamic patterns for manipulating and working with strings


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


========================================================
**Example**

```r
str <- c("HELLO", "world", "123", "\n")
str_detect(str, "\\d") # has any digit
```

```
[1] FALSE FALSE  TRUE FALSE
```

```r
str_detect(str, "\\D") # has no digit
```

```
[1]  TRUE  TRUE FALSE  TRUE
```

```r
str_detect(str, "\\w") # has any alphanumetic character
```

```
[1]  TRUE  TRUE  TRUE FALSE
```

```r
str_detect(str, "\\s") # has any whitespate
```

```
[1] FALSE FALSE FALSE  TRUE
```


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


========================================================
**Example**

```r
str <- c("HELLO", "world", "123", "\n")
str_detect(str, ".") # has any character except \n
```

```
[1]  TRUE  TRUE  TRUE FALSE
```

```r
str_detect(str, "(d|1)") # has d or 1
```

```
[1] FALSE  TRUE  TRUE FALSE
```

```r
str_detect(str, "[Oo]") # has O or o
```

```
[1]  TRUE  TRUE FALSE FALSE
```

```r
str_detect(str, "[^HELLO123]") # has characters other than...
```

```
[1] FALSE  TRUE FALSE  TRUE
```


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


========================================================
**Example**

```r
str <- c("apple", "apricot", "banana", "pineapple")
str_detect(str, "^(a|ba)")
```

```
[1]  TRUE  TRUE  TRUE FALSE
```

```r
str_detect(str, "apple$")
```

```
[1]  TRUE FALSE FALSE  TRUE
```


Quantifiers
========================================================

|Quantifier |Description                             |
|:----------|:---------------------------------------|
|`*`        |Matches at least 0 times                |
|`+`        |Matches at least 1 time                 |
|`?`        |Matches at most 1 time; optional string |
|`{n}`      |Matches extactly `n` times              |
|`{n,}`     |Matches at least `n` times              |
|`{,n}`     |Matches at most `n` times               |
|`{n,m}`    |Matches between `n` and `m` times       |


========================================================
**Example**

```r
str <- c("apple", "apricot", "banana", "pineapple")
str_detect(str, "p*")
```

```
[1] TRUE TRUE TRUE TRUE
```

```r
str_detect(str, "p+")
```

```
[1]  TRUE  TRUE FALSE  TRUE
```

```r
str_detect(str, "p{2,}")
```

```
[1]  TRUE FALSE FALSE  TRUE
```


More on regular expression
========================================================
* [Regular-Expressions.info](https://www.regular-expressions.info/rlanguage.html)
* RStudio. (2016).["Basic Regular Expressions in R: Cheat Sheet".](https://www.rstudio.com/wp-content/uploads/2016/09/RegExCheatsheet.pdf)
* Tidyverse. (n.d.). ["Regualr Expressions"](http://stringr.tidyverse.org/articles/regular-expressions.html). *stringr.tidyverse.org*.


Working with Dates/Datetimes
========================================================
type:section
<img src="../images/calendar.png" title="plot of chunk unnamed-chunk-31" alt="plot of chunk unnamed-chunk-31" width="30%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cdn4.iconfinder.com/data/icons/small-n-flat/24/calendar-512.png">Iconfinder.com</a>
</div>


Dates/Datetimes basics
========================================================
* `Date` class
* `POSIXct` and `POSIXlt` classes


lubridate from tidyverse
========================================================
type:section
<img src="../images/lubridate.png" title="plot of chunk unnamed-chunk-32" alt="plot of chunk unnamed-chunk-32" width="25%" style="box-shadow: none; display: block; margin: auto;" />
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
    * Default value corresponds to `"1970-01-01"`


========================================================
**Example**

```r
as_date(17618)
```

```
[1] "2018-03-28"
```

```r
class(as_date("20180328"))
```

```
[1] "Date"
```

```r
as_datetime("2018/03/28")
```

```
[1] "2018-03-28 UTC"
```

```r
class(as_datetime("2018-03-28"))
```

```
[1] "POSIXct" "POSIXt" 
```


========================================================
**Base R alternative**

```r
# equivalent to as_date()
as.Date(x, ...)

# equivalent to as_datetime()
as.POSIXct(x, tz = "", ...)
```


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
* Any of these can be used to *set* the corresponding time component when used with the assignment operator (`<-`).


========================================================
**Example**

```r
today <- as_date("2018-03-28")
year(today)
```

```
[1] 2018
```

```r
month(today) <- 4
today
```

```
[1] "2018-04-28"
```


Parse date-time
========================================================

```r
parse_date_time(x, orders, tz = "UTC", truncated = 0, locale = Sys.getlocale("LC_TIME"), exact = FALSE, drop = FALSE, ...)
fast_strptime(x, format, tz = "UTC", lt = TRUE, cutoff_2000 = 68L)
```
* `x` is a character or numeric vector of dates
* `orders` is a character vector of date-time order format
    * e.g. `"ymd"` for year-month-date format
* `exact` is a boolean value for using the "exact" match for the date-time format specificed by `orders`
* `drop` is a boolean value for dropping, or removing the values not matching the format
* `format` is a character string of formats

========================================================
**Date format symbols**

|Symbol |Description                 |Example |
|:------|:---------------------------|:-------|
|%Y     |Year in 4 digits            |2018    |
|%y     |Year in 2 digits            |18      |
|%B     |Month in words              |March   |
|%b     |Month in words, abbriviated |Mar     |
|%m     |Month in 2 digits           |03      |
|d      |Date in 2 digits            |28      |


========================================================
**Example**

```r
dates = c("2018-03-28", "2018/03/28", "20180328")
parse_date_time(dates, "ymd")
```

```
[1] "2018-03-28 UTC" "2018-03-28 UTC" "2018-03-28 UTC"
```

```r
fast_strptime(dates[1], "%Y-%m-%d")
```

```
[1] "2018-03-28 UTC"
```

```r
fast_strptime(dates[2], "%Y/%m/%d")
```

```
[1] "2018-03-28 UTC"
```

```r
fast_strptime(dates[3], "%Y%m%d")
```

```
[1] "2018-03-28 UTC"
```


========================================================
**Base R alternative**

```r
# equivalent to fast_strptime()
strptime(x, format = "", tz = "")
```
* No base R alternative for `parse_date_time()`
    * In fact, being able to handle multiple dates formats with the same order is one of the advantages of using `parse_date_time()`


Quickly parse date-time
========================================================

```r
ymd_hms(..., quiet = FALSE, tz = NULL, ...)
ymd(..., quiet = FALSE, tz = "UTC", ...)
```
* The first `...` argument is a character vector of dates in appropriate format
* `quiet` is a boolean value for displaying messages
* `tz` is a character string speficiying time zone
* `ymd_hms` and other similar functions does the same work `parse_date_time()`, but with a predefined order.


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
<img src="../images/data_transfer.png" title="plot of chunk unnamed-chunk-45" alt="plot of chunk unnamed-chunk-45" width="30%" style="box-shadow: none; display: block; margin: auto;" />
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
* `file` is a path to the .csv file to import
* `x` is a data object to export
* `path` is a path to the directory where the exported data will be created
* The output of`read_csv()` is a `tibble` object
* The output of `write_csv()` is a .csv file


Using data.table
========================================================

```r
fread(input, sep="auto", sep2="auto", nrows=-1L, header="auto", na.strings="NA", stringsAsFactors=FALSE, skip=0L, colClasses=NULL, col.names,
strip.white=TRUE, fill=FALSE, ...)
fwrite(x, file = "", append = FALSE, quote = "auto", sep = ",", na = "", row.names = FALSE, col.names = TRUE, ...)
```
* `input` is a path to the .csv file to import
* `x` is a data object to export
* `file` is a path to the directory where the exported data will be created
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
* `path` is a path to the excel file (.xls or .xlsx) to import
* `sheet` is the name of a sheet in the excel file to import
* `col_names` is a boolean value for using the first row to import as column names 
* `skip` is a number of rows to skip
* `guess_max` is a number of rows to use to guess the class of each column
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
* `file` is a path to the SPSS file (.sav) to import in `read_sav()`, or a path to export the data in `write_sav()`
* `data` is a data object to export
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
* `path` is a path to the .feather file to import in `read_feather()`, or a path to export the data in `write_feather()`
* `x` is the data object to export
* The output of `read_feather()` is a `tibble` object
* The output of `write_feather()` is a feather file


More on feather
========================================================
* Wickham, H. (2016), ["Feather: A Fast On-Disk Format for Data Frames for R and Python, powered by Apache Arrow"](https://blog.rstudio.com/2016/03/29/feather/). *RStudio Blog*.
* `feather` [CRAN documentation](https://cran.r-project.org/web/packages/haven/haven.pdf)


Questions?
========================================================
type: section
<img src="https://cdn.dribbble.com/users/433975/screenshots/1627606/question-mark-dribbble.gif" title="plot of chunk unnamed-chunk-52" alt="plot of chunk unnamed-chunk-52" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://dribbble.com/shots/1627606-question-mark">Joel Ploz</a>
</p>


References
========================================================
<ul style="font-size: 0.6em; list-style-type:none">
  <li>Grolemund, G. & Wickham, H. (2017). <a href="http://r4ds.had.co.nz/"><span style="font-style:italic">R for Data Science</span></a>.</li>
  <li>Kabacoff, R. (2017). <a href="https://www.statmethods.net/input/dates.html">"Date Values"</a>. <span style="font-syle:italic">Quick-R</span>.</li>
  <li>RStudio. (2017). <a href="https://www.rstudio.com/resources/cheatsheets/">"Dates and Times Cheat Sheet"</a>.</li>
  <li>RStudio. (2017). <a href="https://www.rstudio.com/resources/cheatsheets/">"Work with Strings Cheat Sheet"</a>.</li>
  <li>Tidyverse. (n.d.). <a href="http://haven.tidyverse.org/index.html"><span style="font-style:italic">haven.tidyverse.org</span></a></li>
  <li>Tidyverse. (n.d.). <a href="http://lubridate.tidyverse.org/index.html"><span style="font-style:italic">lubridate.tidyverse.org</span></a></li>
  <li>Tidyverse. (n.d.). <a href="http://readr.tidyverse.org/index.html"><span style="font-style:italic">readr.tidyverse.org</span></a></li>
  <li>Tidyverse. (n.d.). <a href="http://readxl.tidyverse.org/index.html"><span style="font-style:italic">readxl.tidyverse.org</span></a></li>
  <li>Tidyverse. (n.d.). <a href="http://stringr.tidyverse.org/index.html"><span style="font-style:italic">stringr.tidyverse.org</span></a></li>
</ul>
