R Presentation
========================================================
author: TabbyK.N
date:18.6.2017 
autosize: true

Introduction
========================================================


- This application predicts height of child through his gender and the height of the parents.
- The source code can be found here Shiny-Application-and-Reproducible-Pitch/server.R

- The app developed and deployed at: https://tabbykn.shinyapps.io/server/

Data Loading and Processing
========================================================


```

library(HistData)
library(dplyr)
library(GGally)
library(ggplot2)

# loading dataset
data("GaltonFamilies")
gf <- GaltonFamilies

# transform inches to cms
gf <- gf %>% mutate(fh=father*2.54,
                    mh=mother*2.54,
                    mph=midparentHeight*2.54,
                    ch=childHeight*2.54)

# fit different linear models for testing
m1 <- lm(ch ~ mph, data=gf)
m2 <- lm(ch ~ mph + gender, data=gf)
m3 <- lm(ch ~ fh + mh + gender, data=gf)

```

Plot of parents mid heights versus child's height
========================================================

``` 
install.packages("caTools")
library(caTools)
gg<-plot( mph ~ ch,data= gf)
abline(lm(gf$mph~gf$ch), col="red") 


```


