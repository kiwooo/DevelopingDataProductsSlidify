---
title       : Developing Data Products
subtitle    : Motor Vehicles Dataset Analysis
author      : kiwooo
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Synopsis
1. The shiny app will provide prediction based the MT Cars dataset
2. An user would be allowed to choose the number of cylinders between(4, 6 and 8), hp and wt  
3. The prediction is rendered in a layout

--- .class #id 

## Load MT Cars Dataset



```r
library(shiny)
data(mtcars)
str(mtcars)
```

--- 


## Fit a linear Model


```r
modelFit <- lm(mpg ~ hp + cyl + wt, data=mtcars)
mpg <- function(hp, cyl, wt) {
        modelFit$coefficients[1] + modelFit$coefficients[2] * hp +
                modelFit$coefficients[3] * cyl + modelFit$coefficients[4] * wt
}
```

---

## Predict based on Input 


```r
    # based on sample input hp=100 cycl=4 mpg=3000
    predicted_mpg <- mpg(100, as.numeric(4), 3000/1000)
    predicted_mpg
```

```
## (Intercept) 
##    23.68059
```
---




