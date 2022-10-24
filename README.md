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
dataset_interview <- read_csv("dataset_interview.csv")

-- viewi the dataset
glimpse(dataset_interview)
