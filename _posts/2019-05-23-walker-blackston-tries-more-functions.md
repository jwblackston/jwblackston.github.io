---
layout: post
title: "J. Walker Blackston, aspring data scientist, Struggles with functions for cleaning data"
date: 2019-05-23
---

Well, this morning I worked through a few guided phases of DataQuest's Python For Data Science project which seeks to analyze app data from the Google Play and iOS Apple Stores. 

The project, while outwardly simple, contains many steps that are common to data science. To successfully import and clean our data, we needed to create some personalized functions that can handle our specific needs. In this case, it was the need to identify non-English characters (based on ASCII indexing) and scrub duplicates from our data at the same time. We made some really handy functions for this, the first being a data exploration tool that will provide spaces between some highlighted rows and count/print the number of columns and rows in the set:

```python
def explore_data(dataset, start, end, rows_cols = False):
    data_slice = dataset[start:end]
    for row in data_slice:
        print(row)
        print('\n')

    if rows_cols:
        print('Number of rows:', len(dataset))
        print('Number of columns:', len(dataset[0]))
```

Then we wrote a short program that will detect duplicates in data. I know there are likely better functions out there for this, but it was cool to create my own and see what the computer reads through to do so:

```python
dup_rows = [] #initialize empty lists
unique_rows = []

for dat in data:
  name = dat[0]
  if name in unique_rows:
    dup_rows.append(name)
  else:
    unique_row.append(name)
```
Which will be updated to include an 'is_english' function to detect non-ASCII characters in a string:

```python
def is_english(string):
    non_am = 0

    for char in string:
        if ord(character) > 127:
            non_am += 1

    if non_am > 3:
        return False
    else:
        return True
```
Which is also just super neat because it uses the built-in function, 'ord()' to tell us the index of characters passed into the string parameter, iterate over however many characters are in the string, and spit out a counter of non-ASCII values. In general, if a string contains more than 3 non-ASCII it's apparently considered non-English. Now I know!

Anyhow, this was super hard to do without peaking, and I think I know why. I still cannot intuit the way that functions can and should handle variables you pass in. For example, when the dup_rows.append(name) command is specified, I wanted to write it initially with the parameter 'dat' because that's the iterator. But the purpose of the function is to take the iterator to craft a new variable that was originally empty. This will just take practice I guess :/

Here goes nothin'
