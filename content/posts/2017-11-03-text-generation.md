---
title: Text Generation
author: C Ried
date: '2017-11-03'
slug: text-generation
categories:
tags: ['generative','text']
---
# IN PROGRESS 

Text Generation (Generative Texr) is a very interesting field of study. There are a number of different packages that help generate the lists of words to give the user a better understanding of the technology. 

* [Tracery](https://github.com/galaxykate/tracery)

The following Node library gives a structure which is used to generate random words that are assigned to lexical structure that is defined by the user. 

```r
    centar : {
        animal : ["wolf","bear","tiger","lion","snake","anteater"],
        fruit : ["banana","tomato","cherry","strawberry","starfruit"],
        said : ["purring", "whispering", "saying", "murmurring", "growling"],
        timeofday : ["morning","evening","dusk","dawn","afternoon","breakfast","breakfast"],
        lastSyl : "a ia ea u y en am is on an o io i el ios ax ox ix ex izz ius ian ean ekang anth".split(" "),
        vipTitle : ["Dr.", "Professor", "Lord", "Sir", "Captain", "His Majesty"],

        response : ["#animal# love #fruit##lastSyl#", "#animal# #said# at #timeofday#", "#lastSyl##lastSyl#"],
        "origin" : "<h3>#vipTitle# Watson, let me tell you of a #response#</h3>"
    }
```

The following API 

# Wordmuse API 
The following API can be used to generate related words that are pulled to create lexical randomness with less randomly features. 

* words with a meaning similar to ringing in the ears							            https://api.datamuse.com/words?ml=ringing+in+the+ears
* words related to duck that start with the letter b						  	          https://api.datamuse.com/words?ml=duck&sp=b*
* words related to spoon that end with the letter a							              https://api.datamuse.com/words?ml=spoon&sp=*a
* words that sound like elefint												                        https://api.datamuse.com/words?sl=elefint
* words that start with t, end in k, and have two letters in between	        https://api.datamuse.com/words?sp=t??k
* words that are spelled similarly to coneticut	                              https://api.datamuse.com/words?sp=coneticut
* words that rhyme with forgetful	                                            https://api.datamuse.com/words?rel_rhy=forgetful
* words that rhyme with grape that are related to breakfast	                  https://api.datamuse.com/words?ml=breakfast&rel_rhy=grape
* adjectives that are often used to describe ocean	                          https://api.datamuse.com/words?rel_jjb=ocean
* adjectives describing ocean sorted by how related they are to temperature	  https://api.datamuse.com/words?rel_jjb=ocean&topics=temperature
* nouns that are often described by the adjective yellow	                    https://api.datamuse.com/words?rel_jja=yellow
* words that often follow "drink" in a sentence, that start with the letter w	https://api.datamuse.com/words?lc=drink&sp=w*
* words that are triggered by (strongly associated with) the word "cow"	      https://api.datamuse.com/words?rel_trg=cow
* suggestions for the user if they have typed in rawand so far	              https://api.datamuse.com/sug?s=rawand