# -media-investment-analysis
the project analyses the media adavetisement investment of a small company for one month primarily using R Programming  

-- installing and loading R packages
install.packages("tidyverse")
library(tidyverse)
install.packages("dplyr")
library(dplyr)
install.packages("tidyr")
library(tidyr)
install.packages("here")
library(here)
install.packages("skimr")
library(skimr)
install.packages("ggplot2")
library(ggplot2)

-- importing the data
setwd("/cloud/project/")
dataset_interview <- read_csv("Dataset_interview.csv")

-- viewi the dataset
glimpse(dataset_interview)

-- date and cost graph
ggplot(data = dataset_interview)+geom_line(mapping = aes(x=date, y= cost))+labs(title="Relationship between Date & Cost")

--date and impressions graph
ggplot(data = dataset_interview)+geom_line(mapping = aes(x=date, y= impressions))+labs(title="Relationship between Date & impressions")
