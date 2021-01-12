---
title: "Lab 3 Homework"
author: "Hao Li"
date: "2021-01-12"
output:
  html_document: 
    keep_md: yes
    theme: spacelab
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the tidyverse

```r
library(tidyverse)
```

## Mammals Sleep
1. For this assignment, we are going to use built-in data on mammal sleep patterns. From which publication are these data taken from? Since the data are built-in you can use the help function in R.

```r
?msleep
```
Updated sleep times and weights were taken from V. M. Savage and G. B. West. A quantitative, theoretical framework for understanding mammalian sleep. Proceedings of the National Academy of Sciences, 104 (3):1051-1056, 2007.


2. Store these data into a new data frame `sleep`.

```r
data("msleep")
sleep <- data.frame(msleep)
```

3. What are the dimensions of this data frame (variables and observations)? How do you know? Please show the *code* that you used to determine this below.  

```r
dim(sleep)
```

```
## [1] 83 11
```
This data frame has 83 obs. of 11 variables.


4. Are there any NAs in the data? How did you determine this? Please show your code.  

```r
any(is.na(sleep))
```

```
## [1] TRUE
```
There are some NA's.


5. Show a list of the column names in this data frame.

```r
names(sleep)
```

```
##  [1] "name"         "genus"        "vore"         "order"        "conservation"
##  [6] "sleep_total"  "sleep_rem"    "sleep_cycle"  "awake"        "brainwt"     
## [11] "bodywt"
```

6. How many herbivores are represented in the data?  

```r
table(sleep$vore)
```

```
## 
##   carni   herbi insecti    omni 
##      19      32       5      20
```
There are 32 herbivores.

7. We are interested in two groups; small and large mammals. Let's define small as less than or equal to 1kg body weight and large as greater than or equal to 200kg body weight. Make two new dataframes (large and small) based on these parameters.

```r
small <- subset(sleep, bodywt <= 1)
large <- subset(sleep, bodywt >= 200)
```

8. What is the mean weight for both the small and large mammals?

```r
mean(small$bodywt)
```

```
## [1] 0.2596667
```


```r
mean(large$bodywt)
```

```
## [1] 1747.071
```

9. Using a similar approach as above, do large or small animals sleep longer on average?  

```r
mean(small$sleep_total)
```

```
## [1] 12.65833
```


```r
mean(large$sleep_total)
```

```
## [1] 3.3
```
Small animals tend to sleep longer on average.


10. Which animal is the sleepiest among the entire dataframe?

```r
max(sleep$sleep_total)
```

```
## [1] 19.9
```


```r
which(sleep$sleep_total == 19.9)
```

```
## [1] 43
```

```r
sleep[43,]
```

```
##                name  genus    vore      order conservation sleep_total
## 43 Little brown bat Myotis insecti Chiroptera         <NA>        19.9
##    sleep_rem sleep_cycle awake brainwt bodywt
## 43         2         0.2   4.1 0.00025   0.01
```
Little brown bat is the sleepiest.


## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   