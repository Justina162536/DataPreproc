# DataPreproc
---
title: "2Užduotis"
author: "Justina Naujalytė"
date: "`r Sys.Date()`"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```


## R Užduoties (antros) aprašymas
Atverkite duomenų failą donate.sas7bdat (SAS Data Set; informaciją apie aukojimų
skaičių (kartais) per ketvirtį). Ar kintamieji turi sąlyginių ir grubių išskirčių? Grubiąsias
pašalinkite. Žr. install.packages(”sas7bdat”), funkcija read.sas7bdat().

Pradinio duomenų failo atsidarymas
```{r}

library("tidyr")
library(sas7bdat)
getwd()
setwd("C:/Users/justi/OneDrive/Desktop/R duomenys")
duomenys = read.sas7bdat("donate.sas7bdat")
duomenys
```

Tikrinama, ar yra sąlyginių išskirčių ir jos parodomos
```{r}
q1 <- quantile(duomenys$Qtr4, 0.25,na.rm=T)
q3 <- quantile(duomenys$Qtr4, 0.75,na.rm=T)
IQR = q3-q1

x = duomenys$Qtr4

outlier_ind <- which(x > q1 -3*IQR(x, na.rm = TRUE) & x<q1-1.5*IQR(x, na.rm = TRUE) | x  < q3+3*IQR(x, na.rm = TRUE) & x > q3+1.5*IQR(x, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```
```{r}
q1 <- quantile(duomenys$Qtr3, 0.25,na.rm=T)
q3 <- quantile(duomenys$Qtr3, 0.75,na.rm=T)
IQR = q3-q1

x = duomenys$Qtr3

outlier_ind <- which(x > q1 -3*IQR(x, na.rm = TRUE) & x<q1-1.5*IQR(x, na.rm = TRUE) | x  < q3+3*IQR(x, na.rm = TRUE) & x > q3+1.5*IQR(x, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```
```{r}
q1 <- quantile(duomenys$Qtr2, 0.25,na.rm=T)
q3 <- quantile(duomenys$Qtr2, 0.75,na.rm=T)
IQR = q3-q1

x = duomenys$Qtr2

outlier_ind <- which(x > q1 -3*IQR(x, na.rm = TRUE) & x<q1-1.5*IQR(x, na.rm = TRUE) | x  < q3+3*IQR(x, na.rm = TRUE) & x > q3+1.5*IQR(x, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```
```{r}
q1 <- quantile(duomenys$Qtr1, 0.25,na.rm=T)
q3 <- quantile(duomenys$Qtr1, 0.75,na.rm=T)
IQR = q3-q1

x = duomenys$Qtr1

outlier_ind <- which(x > q1 -3*IQR(x, na.rm = TRUE) & x<q1-1.5*IQR(x, na.rm = TRUE) | x  < q3+3*IQR(x, na.rm = TRUE) & x > q3+1.5*IQR(x, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```

Tikrinama, ar yra grubių išskirčių
```{r}
lower_bound <- quantile(duomenys$Qtr1, 0.25,na.rm=T)
upper_bound <- quantile(duomenys$Qtr1, 0.75,na.rm=T)

outlier_ind <- which(duomenys$Qtr1 < lower_bound -3*IQR(duomenys$Qtr1, na.rm = TRUE) | duomenys$Qtr1  > upper_bound+3*IQR(duomenys$Qtr1, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```
```{r}
lower_bound <- quantile(duomenys$Qtr2, 0.25,na.rm=T)
upper_bound <- quantile(duomenys$Qtr2, 0.75,na.rm=T)

outlier_ind <- which(duomenys$Qtr2 < lower_bound -3*IQR(duomenys$Qtr2, na.rm = TRUE) | duomenys$Qtr2  > upper_bound+3*IQR(duomenys$Qtr2, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```
```{r}
lower_bound <- quantile(duomenys$Qtr3, 0.25,na.rm=T)
upper_bound <- quantile(duomenys$Qtr3, 0.75,na.rm=T)

outlier_ind <- which(duomenys$Qtr3 < lower_bound -3*IQR(duomenys$Qtr3, na.rm = TRUE) | duomenys$Qtr3  > upper_bound+3*IQR(duomenys$Qtr3, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```
```{r}
lower_bound <- quantile(duomenys$Qtr4, 0.25,na.rm=T)
upper_bound <- quantile(duomenys$Qtr4, 0.75,na.rm=T)

outlier_ind <- which(duomenys$Qtr4 < lower_bound -3*IQR(duomenys$Qtr4, na.rm = TRUE) | duomenys$Qtr4  > upper_bound+3*IQR(duomenys$Qtr4, na.rm = TRUE))
outlier_ind
duomenys[outlier_ind, ]
```

Pašalinamos grubios išskirtys ir parodomas failas po pašalinimo
```{r}
clean_duomenys2 <- duomenys[-outlier_ind, ]
clean_duomenys2
```
