---
title: Exploring the Book of Esther in the Tidy Verse
author: C Ried
date: '2017-11-30'
slug: exploring-the-book-of-esther-in-the-tidy-verse
categories:
tags: ['R','bible','nlp']
---

```r
library(httr)
library(tidytext)
library(jsonlite)
library(tidyverse)
library(wordcloud)
library(XML)
source("~/keys.R")
key <- biblia
```

There is much to be learned in the form of writing and the relationship it has within and outside the text. The question we might want to ask is there a way to identify the story arc of the situation.  Using spacy to tag all of the words will increase the likelyhood to better understand the 

```r
style <- "oneVersePerLineFullReference" #oneVersePerLine, bibleTextOnly, oneVersePerLineFullReference
output <- "html"
passage <-"Esther1-10"
resp <- GET(paste0("https://api.biblia.com/v1/bible/content/LEB.",output,"?passage=",passage,"&style=",style,"&key=",key))
```


```r
# parse html
html <- content(resp,"text")
doc = htmlParse(html, asText=TRUE)
plain.text <- xpathSApply(doc, "//p", xmlValue)
plain.text <-  gsub('[\r\n\t]', '', plain.text)
plain.text <- tibble(Text = plain.text)
```



#### Create the Data Frame 
*TODO:* Need to make sure to figure out the book regex to include books such as 1 Timothy where there are parts of the book  

```r
passage <- plain.text %>% 
  mutate(
        Book = str_extract(Text, "^([*?\\w]+)"), 
        Chapter = as.numeric(str_extract(Text,"\\d+(?=:\\n?)")), 
        Verse = as.numeric(str_extract(Text,"(?<=\\:)\\d+")),  
        Line = str_replace(Text, "^([*?\\w]+\\s\\w+\\:\\w+)","")) 

tibble(Text = passage$Text)
```

```r
data("stop_words") # Remove stop words 
passage_frame <- passage %>% select(Book, Chapter, Verse, Line) %>% unnest_tokens(word, Line) %>%
    anti_join(stop_words)
head(passage_frame)
```


Here to simply look at the entire passage as a whole, this is what we are able to retrieve in counts after having removed the words. 

```r
passage_frame_cnt <- passage_frame %>% count(word, sort = TRUE)
head(passage_frame_cnt)
```

```r
passage_framea_cnt <- passage_frame %>% group_by(Chapter) %>% count(word, sort = TRUE)
head(passage_framea_cnt)
```


### Word frequencies by chapter 
```r
library(ggplot2)

g <- passage_framea_cnt %>%
  top_n(5) %>%
  filter(n > 1) %>%
  ggplot(aes(reorder(word, n), n, fill = as.factor(Chapter))) +
  geom_col() +
  xlab(NULL) +
  facet_grid(.~Chapter) + 
  coord_flip()

g
```



```r
gb <- passage_framea_cnt %>% 
  filter(word %in% c("king","jews","mordecai","haman","esther", "women")) %>%  
  ggplot(aes(Chapter, n, fill = word )) + 
  geom_col() + 
  labs(x = "Chapter", y = "Occurance") +
  facet_grid(. ~ word)
gb
  
ga <- passage_framea_cnt %>% filter(word %in% c("king","jews")) %>%  
  ggplot(aes(Chapter, n )) + 
  geom_col() + 
  labs(x = "Chapter", y = "Occurance") +
  scale_fill_brewer() + 
  facet_grid(. ~ word) 
  

  ga
```

### Sentiment Analysis of the story and its progression 



### Generating the Wordcloud for each chapter 
```r
  passage_frame_cnt %>%
  with(wordcloud(word, n, max.words = 100, random.color = TRUE))

```


###References

* Quantify the Narrative Arc* https://blog.reedsy.com/narrative-arc/
* http://tidytextmining.com/tidytext.html
* https://cran.r-project.org/web/packages/httr/vignettes/quickstart.html
* https://github.com/Faithlife/bibliaapi.com/blob/gh-pages/docs/Bible_Content.md
* https://cran.r-project.org/web/packages/ggridges/vignettes/gallery.html
* http://stringr.tidyverse.org/articles/stringr.html