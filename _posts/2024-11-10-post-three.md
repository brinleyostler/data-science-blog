---
layout: post
title:  "Exploring AZ's Most Popular Books (EDA)"
date: 2024-11-10
description: Using Python to perform an Exploratory Data Analysis on my AZ-best-books dataset.   
image: "/assets/img/AZ-pink-sky.jpeg"
---
<p class="intro"><span class="dropcap">I</span> know the burning question that lingers in your mind is what Arizona's most popular books are, so I did the work for you. Let's get into it!</p>

#### In case you missed it...
Check out my [last post](https://brinleyostler.github.io/data-science-blog/blog/post-two/) for code on how I collected this data!

## Burning Questions

### 1) Are the most popular books even any good?

These books are ranked based on how popular they are, not how highly rated they are. In order for a book to be popular, it means a lot of people are borrowing it and reading it. But are the books even any good?

#### SUMMARY STATISTICS

| mean | median | mode | min | max|
|------|--------|------|-----|----|
| 3.87167 | 3.9 | 4.0 | 2.4 | 4.7 |

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/book-ratings.png" alt=""> 
</figure>

It appears that the average rating of our most popular books is 3.87, and the ratings range from 2.4 to 4.7 (out of 5.0). Not bad, but there's more to look at. Are there discrepencies in the ratings between audiobooks and ebooks? Waitlist and available books? Is rank correlated with rating? 

#### AUDIOBOOK vs. EBOOK

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/audio-e-boxplot.png" alt=""> 
</figure>

The boxplots look very similar, but we can already see some *slight* differences. It appears that ebooks have a slightly higher average rating; however, ebooks also have more outliers on the lower end. 

| format | mean | median | mode | min | max|
|--------|------|--------|------|-----|----|
| audiobook | 3.85 | 3.9 | 4.0 | 2.8 | 4.7 | 
| ebook | 3.89 | 4.0 | 4.0 | 2.4 | 4.7 |


#### WAITLIST vs. AVAILABLE

*insert figure here*

explanation

| availability | mean | median | mode | min | max|
|--------------|------|--------|------|-----|----|
| waitlist | 3.88 | 3.9 | 4.0 | 2.4 | 4.7 |
| available | 3.85 | 3.9 | 4.0 | 2.8 | 4.5 |


#### DIFFERENCE in Ratings for Book Rank

Are audiobooks and ebooks rated similarly at the same rankings? 

With this question, I took each ebook's rating at rank 1, then rank 2, all through rank 240 and subtracted each audiobook's rating at rank 1, then rank 2, through rank 240. The plot below shows these differences. 

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/rating-diff-plot.png" alt=""> 
</figure>

It appears that while some rankings have large differences in rating, the differences seem to be consistent across rank. We can't see any obvious positive or negative trends. 

Summary of rating differences:
| mean | median | mode | min | max |
|------|--------|------|-----|-----|
| 0.0425 | 0.1 | 0.2 | -1.4 | 1.3 |


### 2) Do the most popular books have the longest wait time?

Is wait time correlated to the most popular books? While it intuitively makes sense the the more popular a books is, the more people are reading it, leading to longer wait times. However, some books actually have a much higher number of copies than other books, meaning a lower average wait time.

Follow-up question: to help manage long wait times, does the library purchase a higher number of copies for the more popular books? (Is rank correlated to the number of copies?)
