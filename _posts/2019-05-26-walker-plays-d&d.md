---
layout: post
title: "J. Walker Blackston, python and board game novice, tries Dungeons and Dragons"
date: 2019-05-26
---

Today I played roughly 4+ hours of what became my first Dungeons and Dragons campaign. High school me rolls his eyes, but he can shove it because I am both smarter and stronger than he is. 

In all seriousness, I see the appeal. The genuine joy you experience when hilarious shit happens to you or your buddies ios rarely duplicated. I don't expect to be swapping my gym membership for a D4 games budget any time soon (a local D&D hangout), but I'll be damned if I didn't have a blast and will continue with this campaign occasionally. 

Importantly, this experience brought me an idea for my first "personal project" to write in python. I realized this when thinking about how traits and turns are structured. To the un-churched, nearly everything in D&D revolves around a series of multi-sided die. A few are 20-sided (or "d20"), where others are d6 or d4 etc., all with equal probability of rolling. These rolls dictate player traits, attack abilities, and any other special attributes related to your character arc. 

One condition I'd like to play with here is the concept of "advantaged" or "disadvantaged" rolls. This simply means that when you roll 2 d20's, you take the lower of the rolls. If you were creating a D&D Python game, how would you simulate these rolls and make a decision?

''' #let r_1 and r_2 be the set of possible rolls
r_1 = list(range(1, 20, 1)
r_2 = list(range(1, 20, 1)
#create a function that will take in the move of both, draw randomly with equal probability for all numbers, and make a simple decision to give advantage:

import random
import numpy as np
def die():
    
    print('Please roll: ')
    roll = input()
    
    if roll != 'roll':
        print('Please type "roll" to roll die') 
    
    else:
        roll_one = list(range(1, 21))
        roll_two = list(range(1, 21))

        if roll_one > roll_two:
            print('You rolled a ' + str(roll_one) + ' and ' + str(roll_two) + '. ' 'Advantage: ' + str(roll_one))
            roll = roll_one
            return roll_one 
        
        elif roll_one < roll_two:
            print('Disadvantage: ' + str(roll_two))
            roll = roll_two
            return roll_two   
'''
I got the first iteration of this to run! Holy cow that felt cool. But then I got cheeky and decided to refactor. Due to some pointers from a professional, I decided to simplify and clean it up, which represents the code you see above. This has taught me several lessons: 1) always save checkpoints of successful code, and 2) if it ain't broke, don't fix it. So now I will be refactoring *this* code to make it run again. 

Here goes nothin'

