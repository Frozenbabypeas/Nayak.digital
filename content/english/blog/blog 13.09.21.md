---
title: "Python and the wroad to wrangle!"
date: 2021-09-13T12:14:34+10:00
image: "images/portfolio/python-chrisreid.jpg"
tags: ["python","hugo", "webdesign"]
description: "First"
draft: false
---

I've started this blog on the hopes to diarise my journey in making myself competent in coding.  I'm pretty good with computers since a very young age, both at home playing computer games after school and working as an excel specialist straight out of University.  I've never really worked on learning computer science or formal training on coding.  Wrapping my head around programming languages felt too cumbersome.  But now, I’ve seen the light! The wonders of building your own tool!  The power of making your own toy! The joy in designing something that feels soo right!


#### Sliding my way through tutorials...

Python is my first step.  I’ve already started in python beginner courses.  I went to <a href="https://www.datacamp.com/">datacamp</a>, and set up a free account.  This was my first step in learning the basic principles of programing python.  And it’s stupidly easy!  Of course it starts getting harder and harder but learning the foundations are just too important.  I was doing this for a few weeks and then went to <a href="https://www.youtube.com/watch?v=DLn3jOsNRVE&t=4195sTech">Tech with Tim on YouTube</a>.  He has a lot of videos on how to Python including one very good video.  It was based on 5 mini python projects which I jumped on immediately, of which I made 3 (mainly because of timing).

<dl>
  <dt>Question Tester</dt>
  <dd>- It’s a simple question and answer game.  Get an answer right, get a point.  At the end it will count the points.  This game really helps understand the basics of variables and If functions.</dd>
  <dt>Rock, Paper, Scissors</dt>
  <dd>- Self-explanatory on the game.  I learnt how to use the while loop appropriately while using a list and randomising the index of the list for the AI.</dd>
  <dt>Number Guesser</dt>
  <dd>- A guessing game which lets you know if you’re higher or lower than the AI counting how many tries it’s taken you to win.  Great way to learn about if functions in while loops.</dd>
</dl> 

These projects were a great way to lean on the starter courses from data camps and I would encourage anyone that’s starting out to follow a similar path.
 
```python

import random

print("Welcome to my number guessing game!")

top_of_range = input("Type your number: ")

if top_of_range.isdigit():
    top_of_range = int(top_of_range)
    
    if top_of_range <= 0:
            print("Please give me a number greater than 0.")
            quit()
else:
    quit()

random_number = random.randint(0,top_of_range)

guesses = 0

print("Guess the number between 0 and " + " " + str(top_of_range))

while True:
    guesses += 1
    user_guess = input("Guess the number: ")
    if user_guess.isdigit():
        user_guess = int(user_guess)
    else:
        print("Please use a number next time!")
        continue
   
    if user_guess == random_number:
        print("Well done, you got it!")
        break
    elif user_guess > random_number:
        print("You are above the number.")
    else:
        print("You are below the number.")
            
print("You got in ", guesses, "guesses")

```


#### Goals

My Goal for the future is to work on more projects with python to get my head around what else is out there.  There is a strong desire to:
 <ul>
  <li>Use API calls and connect seamlessly with other programs.</li>
  <li>Create better tools for my workplace that harness automation for routine tasks.</li>
</ul> 	

Of course, I want to do more fun things as well but really, pushing me to learn python was built out of a need to help efficiency in my workplace.  I know myself well enough that this push is going to grow making more fun things.
