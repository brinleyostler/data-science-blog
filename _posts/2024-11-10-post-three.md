---
layout: post
title:  "Exploring AZ's Most Popular Books (EDA)"
date: 2024-11-10
description: Using Python to perform an Exploratory Data Analysis on my AZ-best-books dataset.   
image: "/assets/img/AZ-pink-sky.jpeg"
---
<p class="intro"><span class="dropcap">I</span> know the burning question that lingers in your mind is what Arizona's most popular books are, so I did the work for you. Let's get into it!</p>

#### In case you missed it...
Check out my [last post](https://brinleyostler.github.io/data-science-blog/blog/post-two/) and my GitHub respository [AZ-top-books]](https://github.com/brinleyostler/AZ-top-books) for code on how I collected this data!

## Burning Questions

### 1) Are the most popular books even any good?

These books are ranked based on how popular they are, not how highly rated they are. In order for a book to be popular, it means a lot of people are borrowing it and reading it. But are the books even any good?

#### SUMMARY STATISTICS

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/book-ratings.png" alt=""> 
</figure>

| mean | median | mode | min | max|
|------|--------|------|-----|----|
| 3.87167 | 3.9 | 4.0 | 2.4 | 4.7 |

It appears that the ratings of our most popular books center around 3.87 and are skewed left with fewer ratings below 3.2. The ratings range from 2.4 to 4.7 (out of 5.0). Not bad, but there's more to look at. Are there discrepencies in the ratings between audiobooks and ebooks? Is rank correlated with rating? Let's explore further.


#### AUDIOBOOK vs. EBOOK

Let's start by looking at the rating differences for audiobooks vs ebooks.

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/audio-e-boxplot.png" alt=""> 
</figure>

| format | mean | median | mode | min | max|
|--------|------|--------|------|-----|----|
| audiobook | 3.85 | 3.9 | 4.0 | 2.8 | 4.7 | 
| ebook | 3.89 | 4.0 | 4.0 | 2.4 | 4.7 |

The boxplots look very similar, but we can already see some *slight* differences. It appears that ebooks have a slightly higher average rating; however, ebooks also have more outliers on the lower end. 


#### DIFFERENCE in Ratings for Book Rank

Are audiobooks and ebooks rated similarly at the same rankings? 

With this question, I took each ebook's rating at rank 1, rank 2, through rank 240 and subtracted each audiobook's rating at rank 1, then rank 2, through rank 240 and took the absolute value. The plot below shows these differences. 

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/rating-diff-plot.png" alt=""> 
</figure>

It appears that while some rankings have large differences in rating, the differences seem to be consistent across rank. We can't see any obvious positive or negative trends. 

Summary of rating differences:

| mean | median | mode | min | max |
|------|--------|------|-----|-----|
| 0.4067 | 0.3 | 0.2 | 0.0 | 1.4 |

There are differences, but on average they don't seem to be too major. An average difference of 0.4 is relatively small. Even a max difference of 1.4 shows that the ratings at each rank seem to be consistent.


#### CORRELATION between Rank and Rating

The remaining question about rank and rating: are they correlated? Do book ratings decrease for the less popular books and increase for the more popular ones?

**Correlation: -0.063**

The correlation between rank and rating is very close to zero. This tells us that there is not much of a relationship. There is a *slight* negative correlation, indicating that as the rank increases (descends on the list becoming less popular) rating decreases... *slightly*. The relationship is not strong whatsoever, so rank is not indicative of rating and vice versa.




### 2) Do the most popular books have the longest wait time?

Is wait time correlated to the most popular books? While it intuitively makes sense the the more popular a book is, the more people want to read it, leading to longer wait times. However, some books actually have a much larger number of copies than other books, leading to a lower average wait time.

Let's investigate:

#### SUMMARY STATISTICS

**Wait Weeks**

| mean | median | mode | min | max |
|------|--------|------|-----|-----|
| 14.51 | 18.0 | 27.0 | 0.0 | 27.0 |

This table demonstrates the summary statistics of the wait time in the numeric format. Let's inspect the raw scraped data before it was converted into a number.

**Wait Time**

Here are the value counts:

| 6 months | No wait | 2 weeks | 3 weeks | 6 weeks | 4 weeks | Everything else |
|----------|---------|---------|---------|---------|---------|-----------------|
| 216 | 107 | 74 | 11 | 9 | 8 | <7 counts |

**Insights**

The most common wait time is 6 months. But! We need to note that for the wait time, once it reaches 6 months, it stops counting any higher. So, in reality, a book's wait time could be much longer, but it will be recorded on the website as '6 months'. This could very likely be skewing the value counts. However, this *does* tell us that a vast majority of the books have a wait time of *at least* 6 months.

The second most common wait time is no wait time at all.

Following the two ends of the wait time spectrum, the most common wait time is 2 weeks. 


#### Wait Time as Rank Increases

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/wait-ranks.png" alt=""> 
</figure>

From the image, it is difficult to tell a relationship, especially with the large skew of data on the low end ('No wait') and on the high end ('6 months'). There also does not seem to be a clear difference between ebooks and audiobooks.


#### Wait Time as Rating Increases

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/wait-rating.png" alt=""> 
</figure>

This plot seems similar to the one before. It's difficult to see any obvious trends in wait time as it relates to book ratings. Which, this may be due to the large number of '6 month' and 'No wait' books.


#### Wait Time as Copies Increase

One thing that seems to make intuitive sense is that the wait time decreases as the book's copies increase. The more copies available to readers, the fewer number of people would need to wait. Let's see:

<figure>
    <img src="{{site.url}}/{{site.baseurl}}/assets/img/wait-copies.png" alt=""> 
</figure>

While there is not an obvious linear trend, we can see on the plot that the wait time seems to drop off around 25 copies. Any book that has more than 25 copies has a wait time of about 6 weeks or less.

**Correlation: -0.332**

The correlation between wait weeks and copies is relatively weak, but still tells us a little bit about the data. As the number of copies increases, on average the number of wait weeks decreases... *slightly*. Which is what we expected.


### Follow-up: Rank vs. Copies

This question got me thinking about which books have a larger number of copies. To help manage long wait times, does the library purchase a higher number of copies for the more popular books? In other words, is rank correlated to the number of copies?

**Correlation: -0.222**

Just like before, the correlation isn't all that strong, but it does tell us about the relationship between rank and copies. As rank decreases (the book is more popular), on average the number of copies increases... *slightly*.

This may be due to the library trying to manage long wait times for popular books. However, they are restricted by copyrights and other licensing issues. They may not be allowed to have over a certain number of copies for a particular book. 


### Going Further

To investigate this data further, I would love to go back and scrape *all* the book data from the websites. I only scraped the top 240 books of each format. 
- Would rating differences diverge or converge with more books?
- Would our correlation between rank and rating change as we collected more data? 


What should I investigate further about this dataset? Did I miss something in my EDA? Let me know in the comments!

Thanks for reading!


<script src="https://utteranc.es/client.js"
repo="brinleyostler/data-science-blog"
issue-term="pathname"
label="💬"
theme="boxy-light"
crossorigin="anonymous"
async>
</script>