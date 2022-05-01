# R-Final-Project-
COVID 19 ANALYSIS 
#Loading Library
```{r}
library(covid19.analytics)
library(tidyverse)    
library(tidyr)
library(dplyr)
library(tidytext)
library(ggplot2)
library(readr)
library(plotly)
library(RColorBrewer)
library(dplyr)
library(stats)
library(graphics)
library(pheatmap)

```

#dataset discription# covid19.analytics Package from RStudio to get access to and analyze the live worldwide data from the novel CoViD19 from JHU repository.
# obtain all the records combined for " confirmed " , " deaths " and " recovered " cases
# for the global ( worldwide ) * aggregated * data
#The return reading bellow shows the current data up to 04/29/2022  4010 obs. of 14 variables

```{r}
covid19.data.ALLcases <- covid19.data ()

```
#time serious data for global " confirmed " cases
# The time series shows the date retrived and the range of the date the data sample was collected.
#Data retrieved on 2022-04-30 11:57:01 || Range of dates on data: 2020-01-22--2022-04-29
```{r}
tsc <- covid19.data("ts-confirmed")
```
## read the time series data for all the cases 
```{r}
tsa <- covid19.data(case = "ts-ALL")
```


#plots in a static and interactive plot total number of cases per day, the user can specify multiple locations or global totoals

```{r}
totals.plt(tsa)
```
#function to compute daily changes and "Growth Rates" per location; "Growth Rates" defined as the
#ratio between changes in consecutive days
#compute changes and growth rates per location for 'US'
```{r}

growth.rate(tsc,geo.loc="US")

```
itrends function to visualize trends in daily changes in time series data interactively
```{r}

itrends(tsc, geo.loc="US")
```
#live.map function to map cases in an interactive map
```{r}
live.map(covid19.data("ts-confirmed"))
```
```{r}
France.data <- tsc[ (tsc$Country.Region == "France") & (tsc$Province.State == ""),]
France.data 

```
# run a SIR model for a given geographical location
```{r}
 generate.SIR.model ( tsc, "US" , tot.population =332635023)
```
##To sum up my covid 19 analysis and visualization##
 
 The “covid19.analytics” R package allows users to obtain live* worldwide data from the novel Coronavirus Disease originally reported in 2019, COVID-19. I used 

After loading the important library and data from RStudio, I explored analyze the data using different method.
First I run all cases of covid19 data that gives me global ( worldwide ) * aggregated * data
#The return reading shows the current up to date live data 
The time serious data for global ” confirmed ” cases and shows the date retrieved and the range of the date the data sample was collected
To read the time series data for "all" the cases
plots in a static and interactive plot shows the total number of cases per day, the user can specify multiple locations or global totals. as we explore through the graph it show us all current cases of the glob.

The growth rate function compute daily changes and "Growth Rates" per location; "Growth Rates" defined as the ratio between changes in consecutive days. I showed to compute changes and growth rates per location for 'US'
 itrends function to visualize trends in daily changes in time series data interactively
live.map function to map cases in an interactive map on the glob, we can go to any country on the map and explore the numbers.
