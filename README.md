# -media-investment-analysis
the project analyses the media adavetisement investment of a small company for one month using Excel, SQL and R Programming  
-- Changing the date format to YYYY-MM-DD using Excel
Select date column and right click > format cell > date > type

-- site activity and date graph 
Aggregaetd the site activities by date using COUNTIFS 

-- Bulidng the line series graphs for cost and imprrssions using R programming 
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
ggplot(data = dataset_interview)+geom_line(mapping = aes(x=date, y= cost, color=cost))+labs(title="Relationship between Date & Cost")

--date and impressions graph
ggplot(data = dataset_interview)+geom_line(mapping = aes(x=date, y= impressions, color=impressions))+labs(title="Relationship between Date & impressions")

-- Measuirng the CPM using SQL
## CPM by each site 
SELECT site, SUM (cost)*1000/sum(impressions) as CPM 
  FROM `project-interview-366520.advetisement_data.ad_data` 
 GROUP BY site
ORDER BY CPM DESC

## Total CPM by sites
SELECT  SUM(CPM) as total_cpm
FROM
(SELECT site, SUM (cost)*1000/sum(impressions) as CPM 
  FROM `project-interview-366520.advetisement_data.ad_data` 
 GROUP BY site
ORDER BY CPM DESC)

## CPM by each ad_type
SELECT ad_type, SUM (cost)*1000/sum(impressions) as CPM 
  FROM `project-interview-366520.advetisement_data.ad_data` 
 
GROUP BY ad_type
ORDER BY CPM DESC

## Total CPM by ad_types
SELECT  SUM(CPM) as total_cpm
FROM
(SELECT ad_type, SUM (cost)*1000/sum(impressions) as CPM 
  FROM `project-interview-366520.advetisement_data.ad_data` 
 
GROUP BY ad_type
ORDER BY CPM DESC)

-- Aggregating the device_category, line_item_type_id, impressions and cost by date using COUNTIFS function on EXCEL

-- Detecting the outlier in impressions using SQL
SELECT date,  sum(impressions) as imp
 FROM `project-interview-366520.advetisement_data.ad_data` 
WHERE  date BETWEEN '2019-06-10' and '2019-06-17'  
GROUP BY date
ORDER BY imp

-- June 13 has the highest impression. Let's check which website has the highest impression  
SELECT site,  sum(impressions) as imp
 FROM `project-interview-366520.advetisement_data.ad_data` 
WHERE date = '2019-06-13'  
GROUP BY site
order by imp desc

-- Detecting the outlier in cost using SQL
SELECT site, date,  sum(cost) as cost
 FROM `project-interview-366520.advetisement_data.ad_data` 
WHERE  date BETWEEN '2019-06-17' and '2019-06-24'  
GROUP BY date, site
ORDER BY cost desc


