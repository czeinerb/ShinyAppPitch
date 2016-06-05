---
title       : Calculating the area of a triangle with Shiny
subtitle    : Developing Data Products Assignment
author      : Bela Czeiner
job         : Coursera student
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, bootstrap]    # {mathjax, quiz, bootstrap}
ext_widgets : {rCharts: [libraries/nvd3]}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

# Calculate the area of a triangle with Shiny

The solution calcuates the are of a triangle using two methods 
and compares the results:

    1. Calculate it using Heron's formula, the classic geometry method 
    2. A geometric approximation

### Source data

The user need to enter:

    - Coordinates of the cornerns of a triangle in a Cartesian coordinate system 
    - A measure of granularity, which determines the number of data points for the the approximation

---
# Calculation with Heron's formula
Heron's formula uses the semi-perimeter (one-half the perimeter) and the measures of the three sides:

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png)
$  Area = \sqrt{s(s - a)(s - b)(s - c)}$ ,       where $s = \frac{a + b + c}{2}$

The same formula using the coordinates of the cornerns of the triangle:
$$Area =  \frac{\left\lvert (x_1*y_2 + x_2*y_3 + x_3*y_1 - x_1*y_3 - x_2*y_1 - x_3*y_2) \right\rvert}{2}$$
(_For more details see:_ https://en.wikipedia.org/wiki/Heron%27s_formula)

---
# Calculation with geometric approximation

The second solution uses a square fitted around the triangle filled with a matrix of dots or grid points. The area of the triangle is calculated as the ratio of the number of grid points within the triangle (_TriDots_) versus the total number of grid points (_AllDots_) multiplied by the the size of the whole suare (_SqSize_).

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png)
$  Area = \frac{TriDots}{AllDots}  *  SqSize$


---
# Comparison or results



While calculation with Heron's formula gives the arithmetically correct area of the triagle the geometric approximation would only give the same results with infinite number of grid points. 
We can see that with more grid points the area calculated with approximated approximation is getting closer to the real value.

For a triangle with coordinates: 
> 1st corner (x, y): 0, 5; 2nd corner (x, y): 2, 0; 3rd corner (x, y): 6, 8

Area with Heron's formula: 
> __18__ squared units

Area with approximation:
> Where granularity = 10 (resulting in 100 grid points): __15.47__ squared units

> Where granularity = 100 (resulting in 1000 grid points): __17.73__ squared units



