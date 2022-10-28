---
title: Introduction to NLP using Python
author: Chris Ried
date: '2020-10-03'
slug: introduction-to-nlp-using-python
categories: []
tags: ["nlp", 'python']

---

The following post is using SpaCy to do all of the NLP work. Throughout the following post we will cover a number of different NLP tasks that are foundational to the work that can be built upon to generate complex syntatical modelling. 


## Tokenization
This process takes any body of text (more specifically a Document) and breaks it down either to the sentence level or the word level.

```python
import spacy 
nlp = spacy.load('en')
doc = nlp(u'I am flying to Frisco')
print([w.text for w in doc])
```

## Lemmatization 
Lemmatization is taking the root form of a word. Below we have a better idea of what that might look like.

```python
doc = nlp(u'this product integrates both libraries for downloading and applying patches')
for token in doc: 
  print(token.text, token.lemma_)
```
> this this
> product product
> integrates integrate
> both both
> libraries library
> for for
> downloading download
> and and
> applying apply
> patches patch

The line *integrates integrate* is a perfect example. 

