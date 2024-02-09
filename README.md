# Lyrical_Search_Engine_ISRproject1
First hand experience building a text-based mini search engine using TF-IDF and BM-25 Ranking methods.

# Goals of this Project
In this project I got first hand experience building a text-based mini search engine. In particular, there are three main learning objectives: 
* Basics of tokenization (e.g. stemming, case-folding, etc.) and its effect on information retrieval; 
* Basics of index building and Boolean retrieval; 
* Basics of the Vector Space model and ranked retrieval.


# Observation
Let us understand from 2 examples.

### INSTANCE-1

For query 'boat' we got following scores:

#### TF_IDF

Rank: 1 ; Score: 0.8702256269735131 ; DocumentID: Sam-smith-blind-eye-lyrics

Rank: 2 ; Score: 0.5490512403779657 ; DocumentID: Major-lazer-cold-water-lyrics

Rank: 3 ; Score: 0.5490512403779657 ; DocumentID: Kris-kross-amsterdam-and-conor-maynard-are-you-sure-lyrics

Rank: 4 ; Score: 0 ; DocumentID: Erykah-badu-kiss-me-on-my-neck-lyrics

Rank: 5 ; Score: 0 ; DocumentID: Daniel-caesar-we-find-love-lyrics

#### COSINE

Rank: 1 ; Score: 0.5800534800082907 ; DocumentID: Derek-minor-until-the-end-of-time-lyrics

Rank: 2 ; Score: 0.524132767165299 ; DocumentID: John-legend-for-the-first-time-lyrics

Rank: 3 ; Score: 0.4882147063795788 ; DocumentID: Method-man-if-time-is-money-fly-navigation-lyrics

Rank: 4 ; Score: 0.40647747202618945 ; DocumentID: Partynextdoor-not-nice-lyrics

Rank: 5 ; Score: 0.40647747202618945 ; DocumentID: Linkin-park-from-the-inside-lyrics

#### BM25

Rank: 1 ; Score: 2.8897554160315315 ; DocumentID: Sam-smith-blind-eye-lyrics

Rank: 2 ; Score: 1.8791898980781874 ; DocumentID: Kris-kross-amsterdam-and-conor-maynard-are-you-sure-lyrics

Rank: 3 ; Score: 1.824404156406801 ; DocumentID: Major-lazer-cold-water-lyrics

Rank: 4 ; Score: 0.0 ; DocumentID: Erykah-badu-kiss-me-on-my-neck-lyrics

Rank: 5 ; Score: 0.0 ; DocumentID: Daniel-caesar-we-find-love-lyrics


#### OBSERVATION: 
We can observe from above data that scoring for 'boat' is same for two different document in TF-IDF. But for same 2 documents the scoring is different in BM-25. This is because the TF_IDF just takes frequency into consideration whereas BM-25 takes both frequency as well as length of document into consideration. 


### INSTANCE-2

For query 'make no sense' we get following results:

#### TF-IDF:

1) Bring-me-the horizon...

2) Florence-the-machine...

3) Kid-cudi-ghost-lyrics...

4) Linkin-park-one-....

5) Devlin-all-along...

#### Cosine:

1) Bring-me-the horizon...

2) Florence-the-machine...

3) Linkin-park-one-....

4) Kid-cudi-ghost-lyrics...

5) Shawn-mendes-act-like...

#### BM-25:

1) Bring-me-the horizon...

2) Florence-the-machine...

3) Linkin-park-one-....

4) Kid-cudi-ghost-lyrics...

5) Shawn-mendes-act-like...


We can see that almost top 5 ranking documents shared by our model are same. However, if the dataset would be big we would have got different results due to different characteristic of each model which I will discuss below.


TF-IDF is simple use multiplication of Term frequency and Inverse term frequency. By IDF it gives more importance to the rare and distinctive words in the text.It may work well for short documents where the number of words is less. TF_IDF can not show importance of different words as it gives equal weight to all. 

Cosine on the other hand normalize the vector distance unlike euclidean distance. Even if the two documents are far apart because of size, they could still have smaller angle in cosine method. The higher the angle, the more dissimiliar are the documents. Cosine measures the angle of the data vectors in vector space and not the magnitude.

BM25 takes into account both frequency of words as well as the length of document so it is good for capturing the context of the text. It is the best among above two and is widely used. However just like above two it also does not give importance to the order of words.

Based on the above reasons I would like to rank in following way:

### BM25 > Cosine > TF-IDF
