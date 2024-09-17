---
layout: post
title:  "Example Post Formatting"
date:   2014-12-15
description: This is a post was provided by the template to show how to format different parts of the blog post in markdown.
---

<p class="intro"><span class="dropcap">C</span>urabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Vestibulum id ligula porta felis euismod semper. Donec sed odio dui. Aenean lacinia bibendum nulla sed consectetur.</p>

# Heading 1

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

###### Heading 6

<blockquote>Aenean lacinia bibendum nulla sed consectetur. Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Cras mattis consectetur purus sit amet fermentum. Nulla vitae elit libero, a pharetra augue. Curabitur blandit tempus porttitor. Donec sed odio dui. Cras mattis consectetur purus sit amet fermentum.</blockquote>

Nullam quis risus eget urna mollis ornare vel eu leo. Cras mattis consectetur purus sit amet fermentum. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor.

## Unordered List
* List Item
* Longer List Item
  * Nested List Item
  * Nested Item
* List Item

## Ordered List
1. List Item
2. Longer List Item
    1. Nested OL Item
    2. Another Nested Item
3. List Item

## Definition List
<dl>
  <dt>Coffee</dt>
  <dd>Black hot drink</dd>
  <dt>Milk</dt>
  <dd>White cold drink</dd>
</dl>

Donec id elit non mi porta gravida at eget metus. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Maecenas faucibus mollis interdum. Donec sed odio dui. Cras justo odio, dapibus ac facilisis in, egestas eget quam.

## Table

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
| Header      | Title       |
| Paragraph   | Text        |

## Code Snippet

{%- highlight python -%}
def print_hi(name):
  print("Hi" + name)
print_hi('Tom')
#=> prints 'Hi, Tom'.
{%- endhighlight -%}


## Figure with Caption

<figure>
	<img src="{{site.url}}/{{site.baseurl}}/assets/img/touring.jpg" alt=""> 
	<figcaption>Figure 1. - This is an example figcaption</figcaption>
</figure>


{%- highlight html -%}
<figure>
	{% raw %}<img src="{{site.url}}/{{site.baseurl}}/assets/img/touring.jpg" alt="">{% endraw %}
	<figcaption>Figure 1. - This is an example figcaption</figcaption>
</figure>
{%- endhighlight -%}

