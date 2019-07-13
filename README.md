## San Francisco Yearly Average of Daily Max Temp 

For Daily Weather Data at Station USW00023272 From 1921 to 2017 

![SF Yearly Max Temp From 1921 to 2017 From Daily Weather Data at Station USW00023272](sfYealyMaxDailyTemp.png)

The program below wrangles data using R code. The data is from the weather station nearest my home in Duboce Triangle, SF, CA. [The National Oceanic and Atmospheric Administration (NOAA) National Centers For Environmental Information](https://www.ncdc.noaa.gov/) is the data source. The daily weather data summaries are for all time, relative to this SF weather station existence.

```{r}
    library(tidyverse)
    sfDaily <- read_csv("data/sf1921to2017GhcnDaily.csv")
    sfDaily <- sfDaily[,colSums(is.na(sfDaily))<nrow(sfDaily)]
    sfDaily$YEAR <- substring(sfDaily$DATE,1,4)
    sfYearMax <- sfDaily %>%
        group_by(sfDaily$YEAR) %>%
        summarise((sfDaily = mean(TMAX)))
    plot(sfYearMax)
    
## Parsed with column specification:
## cols(
##   .default = col_character(),
##   LATITUDE = col_double(),
##   LONGITUDE = col_double(),
##   ELEVATION = col_double(),
##   DATE = col_date(format = ""),
##   PRCP = col_double(),
##   SNOW = col_double(),
##   SNWD = col_integer(),
##   TMAX = col_integer(),
##   TMIN = col_integer(),
##   WT03 = col_integer(),
##   WT04 = col_integer(),
##   WT05 = col_integer(),
##   WT16 = col_integer(),
##   WT18 = col_integer()
## )

```

### MIT License

Copyright (c) 2019 Jeffrey Long

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
