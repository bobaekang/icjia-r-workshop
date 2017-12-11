# ICJIA R Workshop

[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/hyperium/hyper/master/LICENSE)

This workshop is planned to offer a gentle introduction to the R programming language for ICJIA researchers who want to leverage the power and flexibility of R to improve their technical prowess as researcher.

# Workshop curriculum (*in development*)
The workshop consists of six separate modules which are meant to be followed in order. The goal of this workshop is help its participants to get familiar with basic concepts and tools for using R for data analysis tasks and research projects.

## Module 1: Introduction to R
In this module, participants will be introduced to the R language and the benefits of using R for their research projects. They will also get familiar with the R Studio IDE. An overview of the entire workshop curriculum is provided at the end of the module.

* R language
* Why R?
* comparison
    * with Excel
    * with SPSS
    * with Python
* R Studio
* basic workflow
* workshop overview

## Module 2: R basics
Here, participants will learn the basic building blocks of R language. Once participants gain some knowledge in the fundamental topics, they will be introduced to the popular `tidyverse` framework and provided with a recommendation as to a "good" style for coding in R.

* objects
* operators
* data types
    * boolean
        * NA
    * character
    * numeric
        * NaN
    * integer
    * factor
    * list
    * vector
        * not a class in itself
    * data.frame
    * NULL
    * more: table, matrix, etc.
* loops and conditionals
* functions
* data frame
* comments
* libraries/packages
* tidyverse framework
* R style guide

## Module 3: Data manipulation
This module focuses on manimuplating and transforming tabular data using R. Participants will learn how to import data into R environment and use common `tidyverse` syntax to clean and analyze data. Specifically, core functions from dplyr, tidyr, stringr, and lubridate packages will be covered.

* import/export data
    * using `.feather` format
* dplyr package
    * `arange()`
    * `select()`
    * `filter()`
    * `mutate()`
    * `group_by()` and `summarise()`
    * `%>%`, pipe operator
* tidyr package
    * `gather()`
    * `spread()`
    * `separate()`
    * `extract()`
    * `unite()`
* stringr package
* lubridate package
* exercise

## Module 4: Data visualization
In this module, participants will get started with generating plots to visually present and communicate insights from data. The main focus of this module is the popular ggplot2 package. Participants will also be introduced to some options for generating maps and interactive plots.

# base R plots
* ggplot2 package
    * basic components
    * histogram
    * scatter plot
    * line plot
    * labels
    * themes
* plotting maps
    * rgdal pacakge
    * ggmap package
    * tmap package
* interactive plots
    * plotly package
    * highcharter package


## Module 5: Statistical analysis
In this module, participants will learn how to conduct basic statistical analysis with R. 

* formula
* `lm()`
* `glm()`
* jmv package
* advanced modeling
    * time series
    * survival analysis
    * machine learning


## Module 6: Presentations and beyond
This module will introduce participants to various ways to share their work by using R Markdown, R Presentation, and Shiny. 

* R Markdown and R notebooks
* ioslides
* Shiny
    * `flexdashboard`
    * `shinydashboard`
* what's next?
    * custom formatting with CSS
    * modularization
    * R package
* wrapping up


# Resources
* [Quick-R](https://www.statmethods.net/index.html)
* [R Tutorial](http://www.r-tutor.com/r-introduction)
* [R Tutorial](http://www.cyclismo.org/tutorial/R/index.html)
* [R for Data Science](http://r4ds.had.co.nz/)
* [R-bloggers](https://www.r-bloggers.com/)
* [Cheat sheets](https://www.rstudio.com/resources/cheatsheets/)
* Free courses at Coursera and Edx
* Google!