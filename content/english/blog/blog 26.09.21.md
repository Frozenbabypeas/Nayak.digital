---
title: "First game!"
date: 2021-09-26T08:36:34+10:00
image: "images/portfolio/jonathan-petersson-W8V3G-Nk8FE-unsplash.jpg"
tags: ["python","github","projects"]
description: "Third"
draft: false
---

I've gone through the full Sodoku project following <a href="https://www.youtube.com/watch?v=r_cmJBgrq5k&list=PLryDJVmh-ww0J6BDQrdLtRyNOv4Lym_xo">A plus coding</a> on youtube.  It’s a very indepth, logical explanation on how to make the game full with different levels and the Sodoku logic.  Just going through this hurt my head more times than I would have expected.  But, the YouTuber made a lot of sense on why he was doing things… learning the way he logically went through indexes still didn’t help.  Maybe I need to do a certificate.  I would not be able to do this again without this video.  I think it was important that I followed this; my own code has a number of comments which I hope will jog my memory in the future if I’d like to come back to make this program more efficient.  I’ve also noted some a few steps I took to fix some errors he never had.  Just to name two:

Beautiful soup will naturally use an “Lxml” parser in its get request, which would mean it would make it difficult to play the game on a different machine.  You will need to add in a HTML parser to remove this precaution message:
```python
    soup = BeautifulSoup(html_doc, 'html.parser')
```

Another problem is the height and width position settings for the text.  I don’t know why I’m struggling with this but its clear that his code won’t allow for the text to centre align on the button.  So instead, I used a division by cell size to give it better than what I was getting.
```python
    x = ((self.width - width)) // cellsize #text position
    y = ((self.width - height)) // cellsize #text position
```
I’ve tried many iterations to get the text to align centre to the button but I’m losing my patience.  After all its my first game!

#### Link to my Github

I’ve got a <a href="https://github.com/Frozenbabypeas/Sodoku.git">git hub repository</a> with this code shareable if anyone wishes to follow.  Huge shout out to <a href="https://github.com/a-plus-coding">A Plus Coding</a>.  I would really recommend following his channel and supporting him if anyone was new to learning.

#### Till next week

I really need to put this website online.  I really want to start focusing on a few business related projects.  The few ones I’m looking at include API connections and CSV imports.  I’ve dabbled with importing and exporting CSV but I’m really looking at automating a lot of these functions.  One of the tasks I want to do:
 <ul>
  <li>Generate an XML table to report on outstanding clients that haven’t been actioned vs clients that have been actioned.</li>
  <li>Automate communication and responses through email and sms.</li>
</ul> 	

I know there are already tools out there in the ether to do this.  I’m not looking to re-invent the wheel; I am looking to understand and simplify the cost through Python.  My goal will always be the same, learning through code!

Additionally, I need to set up this website to be published online!