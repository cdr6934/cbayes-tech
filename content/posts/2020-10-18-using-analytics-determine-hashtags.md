---
title: Using Analytics to Determine Ideal Hashtags for Instagram 
author: Chris Ried
date: '2020-10-18'
slug: using-analytics-to-determine-ideal-hashtags
categories: ["analytics"]
tags: ["R","analytics"]
---


```r
library(stringr)
library(readr)
library(tidyverse)
library(lubridate)
```

I have been curious on what makes an interesting post on instagram based on a larger dataset of images that have been tagged with #generativeart. Some of this is just data discovery, this could seem that there may be a correlation between the tags that have been used and the amount of likes there are. 



```r
# Extract hashtags
patt <- regex("#\\S+")
genart <- read_csv("~/InstaCrawlR/table-generativeart-2020-10-11 13:35:33.csv")
genart_db <- genart %>% select(ID, Likes, Owner, Date, Text) %>% mutate(hashtags = str_extract_all(Text,patt) )
genart_db_table <- genart_db %>% unnest(cols = "hashtags") %>% mutate(Year = year(Date), Month = month(Date), DayOfWeek = wday(Date),  Day = day(Date), Hour = hour(Date))
```

```r
genart_db_table %>% head()
```
That will generate a rather large dataset 
```r
genart_db_table %>% count()
```

Instead of having too muc
```r
  exclude_tags <- c("#fishart","#artphotohraphy", "#marinephotography","#underwaterscenes","#sharkattack","#акула","#вебпанк","#сос","#seaphotography","fishart","#sharks","#enhancedvitimins")
genart_db_hashtag_mean <- genart_db_table %>% 
  group_by(hashtags) %>% 
  summarize(AverageLikes = mean(Likes), Count = n()) %>% 
  filter(!hashtags %in% exclude_tags, Count > 50) %>% 
  arrange(-AverageLikes)
 genart_db_hashtag_mean %>% head(30) %>% ggplot(aes(reorder(hashtags,AverageLikes), AverageLikes)) + geom_col() + coord_flip() + labs(title = "Most Common Hashtags in Generative Art Posts", 
                                                                                 x
                                                                                 = "Hashtag")
 
  genart_db_hashtag_mean %>% filter(AverageLikes < 200, Count > 200, Count < 40000) %>%  ggplot(aes(AverageLikes, Count, label = hashtags)) + geom_point() + geom_text(check_overlap = TRUE, angle = 45, hjust =0)
  
```
This leads to some very interesting issues of certain tags that may need to be removed from the set due to their  

```r
genart_db_table %>% 
  group_by(hashtags) %>% 
  summarize(Count = n()) %>% 
  arrange(-Count) %>% head(30)  %>% 
  ggplot(aes(reorder(hashtags,Count), Count)) + geom_col() + coord_flip() + labs(title = "Most Common Hashtags in Generative Art Posts", 
                                                                                 x
                                                                                 = "Hashtag")
```
So it appears that the #generativeart tag is the greatest here which would make sense... 

```r
genart_db_table %>% filter(hashtags %in% c("#generativeart")) %>% 
  group_by(hashtags, Hour) %>% summarize(Count = n()) %>% 
    ggplot(aes(Hour, Count)) + geom_col() +labs(title = "Most Common Occurence in Generative Art Posts",  x = "Hour")
```

But we might want to see if there is a difference at a more granular level. 
```r
genart_db_table %>% filter(hashtags %in% c("#generativeart")) %>% 
  group_by(hashtags, Hour, DayOfWeek) %>% summarize(Count = n()) %>% 
    ggplot(aes(Hour, Count)) + geom_col() + facet_grid(DayOfWeek ~ .) +labs(title = "Most Common Hashtags in #generativeart Posts by Day", 
                                                                                 x = "Hashtag")
```
None really when looking at the detail here. 

```r
genart_db_table %>% filter(hashtags %in% c("#generativeart", "#digitalart","#creativecoding", "#generative", "#codeart","#abstractart")) %>% 
  group_by(hashtags, Hour) %>% summarize(Count = n()) %>% 
  mutate(PercentTotal = Count / sum(Count)) %>% 
    ggplot(aes(Hour, PercentTotal/5, fill = hashtags)) + geom_col()  +labs(title = "Most Common Hashtags in #generativeart Posts by Day (%)", 
                                                                                 x = "Hashtag") 
```
Now we want to make sure we don't just take that to mean that generativeart need to 

## TODO 
* Add a graph of the 