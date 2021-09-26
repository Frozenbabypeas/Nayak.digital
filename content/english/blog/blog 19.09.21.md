---
title: "2 Projects, 1 cup"
date: 2021-09-19T08:36:34+10:00
image: "images/portfolio/alvaro-reyes-qWwpHwip31M-unsplash.jpg"
tags: ["python","github", "projects"]
description: "Second"
draft: false
---

Who would have thought there would be so much to learn! It’s hurting my head!
Going through some projects on YouTube has both excited and frustrated me.  I’ve learnt a lot of principles, mainly recursion and backtracking.  I wouldn’t say I understand these concepts fully and can use them seamlessly in any project; I would say that I’ve used it and understand why to use it.  Two projects I’ve worked on are the Sudoku solver and an Amazon Web-scrapper.  Curtesy of <a href="https://www.youtube.com/watch?v=eqUwSA0xI-s">Tech with Tim</a> and <a href="https://www.youtube.com/watch?v=HiOtQMcI5wg&t=721s">Alex the Analyst</a>.

#### Close but no cigar

Both projects have issues.  The Sudoku solver needs me to print a grid (which I have made) rather than automatically create its own.  I have an idea behind how this logic would work, I would have to use the random number generator for each list and make sure it follows the three rules, each row, column and 3 x 3 boxes has to have a unique number up to 9.  I’m excited in finding the answer on this one; I’d rather not look at tutorials for this.

The Web-Scrapper works but there are a few kinks I can’t resolve.  The email element doesn’t do anything and I’m getting no errors.  Maybe it’s the smtp server?  Also, I am only scraping through one website and keeping tabs on one pricing.  I tried using a competitor website I actually wanted to check prices regularly and I tried pulling out the text within a text function Lambda.  It only pulled the site name.  So it works! Just not the way I wanted to.  More to learn!


Sudoku:
```python
board = [
    [7,8,0,0,0,0,1,0,0],
    [3,0,0,1,0,0,0,0,0],
    [0,0,0,4,0,0,0,9,0],
    [8,0,0,0,1,0,0,0,0],
    [1,0,0,0,0,0,0,7,0],
    [0,0,9,0,0,0,4,2,0],
    [0,0,0,0,0,0,0,1,0],
    [0,0,0,3,0,1,0,0,0],
    [2,1,0,0,0,0,0,6,0]
]
####This will eneter numbers to the board and find the solution###
def solve(bo):

    find = find_empty(bo)
    if not find:
        return True
    else:
        row, col = find

####loop through numbers from 1 to 9 and check to see if this is a valid solution###
    for i in range(1,10):
        if valid(bo, i, (row, col)):
            bo[row][col] = i

            if solve(bo):
                return True
            
            bo[row][col] = 0

    return False        

####This will check if the board is valid###
def valid(bo, num, pos,):
    #check row
    for i in range(len(bo[0])):
        if bo[pos[0]][i] == num and pos[1] !=i:
            return False 

    #check column
    for i in range(len(bo[0])):
        if bo[i][pos[1]] == num and pos[0] !=i:
            return False

    #check box
    box_x = pos[1] // 3
    box_y = pos[0] // 3

    for i in range(box_y * 3, box_y*3 +3):
        for j in range(box_x * 3, box_x*3 +3):
            if bo[i][j] == num and (i,j) != pos:
                return False

    return True

####This will print the faux board###
def print_board(bo):

####This is to seperate the board with a line after a row of 3###
    for i in range(len(bo)):
        if i % 3 == 0 and i != 0:
            print("------------------------")

 ####This is to seperate each coloum and leave a space at the end###       
        for j in range(len(bo[0])):
            if j % 3 == 0 and j !=0:
                print(" | ", end="")
                
####Type in print_board(board) after this to print the above board###
            if j == 8:
                print(bo[i][j])
            else:
                print(str(bo[i][j]), end=" ")


def find_empty(bo):
    for i in range (len(bo)):
        for j in range(len(bo[0])):
            if bo[i][j] ==0:
                return (i,j)
    return None
####This will check to see if there is a number in a given sqaure###

print_board(board)
solve(board)
print("-------------------------------")
print_board(board)
```

Web scraper:
```python
from bs4 import BeautifulSoup
import requests
import time
import datetime
import re
import csv
import pandas as pd

import smtplib

# Connect to website

URL = "https://www.amazon.com.au/Denon-AVR-S750H-Receiver-Channel-165W/dp/B07RNCYFQ6/ref=sr_1_3?dchild=1&keywords=recievers&qid=1631962075&sr=8-3"

headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:92.0) Gecko/20100101 Firefox/92.0,"}

page = requests.get(URL, headers = headers)

# Grab Data
soup1 = BeautifulSoup(page.content, "html.parser")
soup2 = BeautifulSoup(soup1.prettify(), "html.parser")

tittle = soup2.find(id="productTitle").get_text()
price = soup2.find(id="priceblock_ourprice").get_text()

# Clean data
tittle = tittle.strip()
price = price.strip()[1:]

# Create a date when new line is added
today = datetime.date.today()

# Create the CSV file
header = ["Title", "Price", "Date"]
data = [tittle, price, today]

with open("Webscraper.csv", "w", newline="", encoding="UTF8") as f:
    writer = csv.writer(f)
    writer.writerow(header)
    writer.writerow(data)

# Append new data to the same CSV file
with open("Webscraper.csv", "a+", newline="", encoding="UTF8") as f:
    writer = csv.writer(f)
    writer.writerow(data)

# Automate function to check pricing automatically
def check_price():
    URL = "https://www.amazon.com.au/Denon-AVR-S750H-Receiver-Channel-165W/dp/B07RNCYFQ6/ref=sr_1_3?dchild=1&keywords=recievers&qid=1631962075&sr=8-3"
    headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:92.0) Gecko/20100101 Firefox/92.0,"}
    page = requests.get(URL, headers = headers)
    soup1 = BeautifulSoup(page.content, "html.parser")
    soup2 = BeautifulSoup(soup1.prettify(), "html.parser")
    tittle = soup2.find(id="productTitle").get_text()
    price = soup2.find(id="priceblock_ourprice").get_text()
    tittle = tittle.strip()
    price = price.strip()[1:]
    today=datetime.date.today()
    header = ["Title", "Price", "Date"]
    data = [tittle, price, today]
    with open("Webscraper.csv", "a+", newline="", encoding="UTF8") as f:
        writer = csv.writer(f)
        writer.writerow(data)

# Loop function to alert process
while True:
    if (check_price == 999):
        send_mail()
    else:
        quit()
```
I have removed the send_mail() function.  For obvious reasons.


#### Moving forward

Both projects are exciting and not complete.  But I’m happy I’m progressing and learning the issues rather than just watching a video and thinking that it’s easy and doable.  I used to do that for a long while and when push came to shove, I just got frustrated and quit.

I'm also working on getting this site live.  First steps would be to build a repo on github to connect to my files, next to find a hosting site other than hostinger (i'm sure there are better cost effective services there) and then connect them!  At the moment, I am using visual studio code for all my website needs and using cmd promt to host the hugo site.  I've learnt alot in these past 3 weeks and theres just soo much more to go! I still want to learn API and build more tools, this is will be a long and exciting road for me!