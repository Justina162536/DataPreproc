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
