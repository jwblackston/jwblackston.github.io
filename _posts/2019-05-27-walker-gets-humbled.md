---
layout: post
title: "J. Walker Blackston, python noob, writes first own function that works, immediately creates a mistake"
date: 2019-05-27
---

It only took a few hours before I realized the foolishness of my mistake. As I mentioned last, I forgot to save my successful code to run a D&D dice simulator that would print advantage or disadvantage rolls. I am now refactoring it with a tutorial I remember from deep in the ether of other simple python tutorials. I will highlight where this differs from my function. This function brought to you by O'Reilly Python cookbooks:

'''
import random

def die(num, sides):    #num equals number of die, sides equal sides of each
    return reduce(lambda x, y, s=sides: x + random.randrange(s),
        range(num+1)) + num
'''

There are a couple of things to note. 1) This code is almost embarassingly simple and allows me to see how much work I have left to truly understand writing good code, and 2) it makes use of some functions I simply do not have stored in my mental roledex for use as needed. 

My first attempt had me thinking I would need to initialize the length of the dice, forgetting that the random module would allow a dice to roll and choose a random number from a given range. Then I realized that my input and main argument for the dice() function were the same, causing roll to be undefined in the global space but defined locally as a simple input() string. I also first thought that creating a disadvantaged roll and advantaged roll would require separate functions, now I see that it can be included as one succinct if-then statement. Adding this to the function above, we get: 

'''
import random
import numpy as np
from functools import reduce

def dice(num, sides):
    def accumulate(x, y, s=sides): return x + random.randrange(s)
    return reduce(accumulate, range(num+1)) + num

print('How many dice are you rolling?')
valid_die = ['1', '2']
num = []
die = input()
    
if die in valid_die:
    num = int(die)
else: 
    print('Please enter a valid number of die')

print('How many sides per die?')
valid_sides = ['4', '6', '8', '20']
sides = []
side_per = input()
    
if side_per in valid_sides:
    sides = int(side_per)
else:
    print('Please enter valid number of sides per die')
'''

This provides a much more definitive program, although I still think it could be simplified and refactored because the function itself only returns one number from a dice roll. 
