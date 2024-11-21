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

**AUDIOBOOK vs. EBOOK**

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/audio-e-boxplot.png" alt=""> 
</figure>

The boxplots look very similar, but we can already see some *slight* differences. It appears that ebooks have a slightly higher average rating; however, ebooks also have more outliers on the lower end. 

| format | mean | median | mode | min | max|
|--------|------|--------|------|-----|----|
| audiobook | 3.85 | 3.9 | 4.0 | 2.8 | 4.7 | 
| ebook | 3.89 | 4.0 | 4.0 | 2.4 | 4.7 |


**WAITLIST vs. AVAILABLE**

*insert figure here*

explanation

| availability | mean | median | mode | min | max|
|--------------|------|--------|------|-----|----|
| waitlist | 3.88 | 3.9 | 4.0 | 2.4 | 4.7 |
| available | 3.85 | 3.9 | 4.0 | 2.8 | 4.5 |


**DIFFERENCE in Ratings for Book Rank**

Are audiobooks and ebooks rated similarly at the same rankings? 

