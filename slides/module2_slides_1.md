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
<h3 style="color: #789">Module 2: R basics (1)</h3>  
2018-01-01  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
  <p style="color: #00061a; font-size: 1.1em; font-weight:700">
    Session 1: Fundamental building blocks of R programming
  </p>
  <p>(break)</p>
  <p>Session 2: Gearing up for data analysis in R</p>
</div>


Fundamental Building Blocks of R Programming
========================================================
type:section

```r
print("Hellow World!")
```

```
[1] "Hellow World!"
```
  

Key concepts
========================================================
* Obejcts
* Expressions
* Functions
* Environments
* R data frames


R Objects
========================================================
type: section


Key object types
========================================================
* Vectors (`c()`)
* Lists (`list()`)
* Factors (`factor()`)
* Data frame (`data.frame()`)


Basic ("atomic") vector types
========================================================
* `logical`: Boolean values of `TRUE` and `FALSE`
* `double`: floating-point numbers representing real numbers
* `integer`: integers
* `complex`: complex numbers
* `character`: string of alphanumeric letters


========================================================

```r
# this is a logical vector
logical_vector <- c(TRUE, FALSE, T, F)

is.logical(logical_vector)
```

```
[1] TRUE
```

```r
class(logical_vector)
```

```
[1] "logical"
```


========================================================

```r
# this is a double (numeric)  vector
double_vector <- c(1, 2, 3)

is.double(double_vector)
```

```
[1] TRUE
```

```r
class(double_vector)
```

```
[1] "numeric"
```

```r
# this is an integer (numeric) vector
integer_vector <- c(1L, 2L ,3L)

is.integer(integer_vector)
```

```
[1] TRUE
```

```r
class(integer_vector)
```

```
[1] "integer"
```


========================================================

```r
# this is a character vector
character_vector <- c("a", "b", "c")

is.character(character_vector)
```

```
[1] TRUE
```

```r
class(character_vector)
```

```
[1] "character"
```


========================================================

```r
x <- 1
y <- "Am I a vector?"

is.vector(x)
```

```
[1] TRUE
```

```r
is.vector(y)
```

```
[1] TRUE
```


Accessing elements in a vector
========================================================


Lists
========================================================


Accessing elements in a list
========================================================


R Expressions
========================================================
type: section


Expressions
========================================================
* Executable pieces of code
* Consisting of objects, operators, control structures and functions


Operators
========================================================
* Arithmetic operators
* Logical operators
* Relational operators
* Assignment operators
* Others
    * User-defined operators
    * From third-party pacakges


Arithmetic operators
========================================================
|Operator|Description|Example|
|--------|--------------------------------|--------------------------------|
|`+`|addition|`1 + 1    # returns 2`|
|`-`|subtraction|`3 - 2  # returns 1`|
|`*`|multiplication|`3 * 4  # returns 12`|
|`/`|division|`5 / 2 # returns 2.5`|
|`^` or `**`|exponentiation|`2**4  # returns 16`|
|`%%`|modulus|`5 %% 2  # returns 1`|
|`%/%`|integer division|`5 %% 2  # returns 2`|


Logical operators
========================================================
|Operator|Description|Example|
|--------|--------------------------------|--------------------------------|
||||
||||
||||
||||
||||


Relational operators
========================================================
|Operator|Description|Example|
|--------|--------------------------------|--------------------------------|
||||
||||
||||
||||
||||


Assignment operators
========================================================
|Operator|Description|Example|
|--------|--------------------------------|--------------------------------|
||||
||||
||||
||||
||||


Flow Control
========================================================
* Loops
* Conditionals


Loops
========================================================
* `while` loops


```r
while ( condition ) {
  expression
}
```

* `for` loops


```r
for ( i in expression_1 ) {
  expression_2
}
```


while loop
========================================================
* If the given `condition` is satisfied (i.e. evaluates as `TRUE`), then the following `expression` is executed.
* Onces the `expression` is executed, the `condition` is re-evaluated.
* The `expression` is repetitively executed as long as the `condition` is satisfied.
    * beware of infinite loop!


========================================================

```r
count <- 0

while (count < 5) {
  print(count)
  count = count + 1  # increase count by 1 at each iteration
}
```

```
[1] 0
[1] 1
[1] 2
[1] 3
[1] 4
```


for loop
========================================================
* Requires an iterable object (e.g. vector or list).
* Iterates over all elements of the given object in order.
* At each step of iteration, can use the given element for the `expression` if appropriate.


```r
for (element in iterable_obj) {
  expression
}
```


========================================================

```r
fruits <- c("apple", "banana", "clementine")

# iterating over elements directly
for (fruit in fruits) {
  print(paste("I love ", fruit, "!", sep=""))
}
```

```
[1] "I love apple!"
[1] "I love banana!"
[1] "I love clementine!"
```


```r
flavors <- c("chocolate", "vanilla", "cookie dough")

# iterating over elements indirectly
for (i in 1:length(flavors)) {
  flavor <- flavors[i]
  print(paste("Do you want some", flavor, "ice cream?"))
}
```

```
[1] "Do you want some chocolate ice cream?"
[1] "Do you want some vanilla ice cream?"
[1] "Do you want some cookie dough ice cream?"
```


Conditionals
========================================================
* `if` statement
* Basic structure
    * if ( condition ) { expression }


```r
a <- TRUE

if (a) {
  print("Hello World!")
}
```

```
[1] "Hello World!"
```


Multiple conditions
========================================================
* `if`-`else` statement
* allows for multiple conditions


```r
a <- 1
b <- 2

if (a > b) {
  print("a is larger than b.")
} else if (a < b) {
  print("a is smaller than b.")
} else {
  print("a and b are equal!")
}
```

```
[1] "a is smaller than b."
```


R Functions
========================================================
type: section


R Environments
========================================================
type: section


Questions?
========================================================
type: section


========================================================
type: section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Ic_pause_circle_outline_48px.svg/2000px-Ic_pause_circle_outline_48px.svg.png" title="plot of chunk unnamed-chunk-14" alt="plot of chunk unnamed-chunk-14" width="45%" style="display: block; margin: auto; box-shadow: none;" />
