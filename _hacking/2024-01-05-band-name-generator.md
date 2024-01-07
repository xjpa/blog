---
layout: post
title: 'Band Name Generator'
description: 'Project #1 for 100 days of code in python, input/printing/functions practice'
date: 2024-01-05 15:30:00 +0000
category: articles
tags: [hacking, project-100daysofcode]
comments: true
---

Code: [github.com/xjpa/100daysofcode/tree/main/day-001](https://github.com/xjpa/100daysofcode/tree/main/day-001)

<!-- more -->

# 100 days, 100+ projects...

My 100 days of code journey starts here. I am undergoing this [100 Days of Code in Python](https://100daysofpython.dev/) challenge to have an excuse to review my python skills while going through from the basics to:

- webdev

- data viz

- artificial intelligence

- automation

- APIs

- scraping

and more! Should be fun!

I like the course as it's not handholdy, especially after day 50, you are pretty much given lectures for that day to introduce new concepts you'll need for the project. It's up to you on how to approach it.

# Band Name Generator

That said, today is very easy. It's just some practice with functions like [input()](https://docs.python.org/3/library/functions.html#input) and [print()](https://docs.python.org/3/library/functions.html#print)

It's simply concatenating 2 user inputs to generate a band name.

```terminal
$ python band_name_generator.py
hi
⦾ What city did you grow up in?
Permutation City
⦾ What is the name of your pet?
K-9
⦾ Band name generated: Permutation City K-9
```

[the code](https://github.com/xjpa/100daysofcode/blob/main/day-001/band_name_generator.py):

```python
print("hi")
city = input("⦾ What city did you grow up in?\n")
pet = input("⦾ What is the name of your pet?\n")
name = city + " " + pet
print("⦾ Band name generated: " + name)
```

While this course is broken down into 100 days, I think I could likely do 2 projects per day for the first few days, until it gets more time draining, then I'll do 1 project a day.

I have a lot of studying to do on other topics so I either do 2 projects/day or I do 1 project a day and just turn it into something more advanced, speaking of

# Band Name Generator 2.0

I want to take on something more than what the final exercise for that course's day provides, so I did the following, going beyond the lessons for that day.

[the code](https://github.com/xjpa/100daysofcode/blob/main/day-001/app.py):

```python
import random

def get_input(prompt):
    while True:
        user_input = input(prompt).strip()
        if user_input.isalpha():
            return user_input.capitalize()
        else:
            print("Invalid input, please enter only letters.")

def generate_band_name(city, pet):
    """ Generate a band name based on the city and pet name. """
    adjectives = ["Groovy", "Electric", "Mystic", "Wild", "Jazzy"]
    adjective = random.choice(adjectives)
    return f"{adjective} {city} {pet}"

def main():
    print("Welcome to the Band Name Generator!")
    city = get_input("⦾ What city did you grow up in?\n")
    pet = get_input("⦾ What is the name of your pet?\n")

    name = generate_band_name(city, pet)
    print(f"⦾ Band name generated: {name}")

    with open("band_names.txt", "a") as file:
        file.write(name + "\n")
    print("Band name saved to 'band_names.txt'.")

if __name__ == "__main__":
    main()

```

Some enhancements

- input validation
- string capitalization for a more polished look
- random adjective added to make things more interesting
- save output to a file
- modularized the code into functions

Some new python stuff added that werent taught for the course that day:

- functions
- list
- while loop
- [string operations](https://docs.python.org/3/library/string.html): .strip(), isalpha(), capitalize()
- [f-strings](https://realpython.com/python-f-strings/)
- conditional statements
- importing a library, in this case [random](https://docs.python.org/3/library/random.html), particularly [random.choice()](https://github.com/python/cpython/blob/3.6/Lib/random.py#L255), its source code from the cpython repo:

```python
def choice(self, seq):
    """Choose a random element from a non-empty sequence."""
    try:
        i = self._randbelow(len(seq))
    except ValueError:
        raise IndexError('Cannot choose from an empty sequence') from None
    return seq[i]
```

It's quite interesting looking at the source code for its implementation, some things to pick up for a beginner would be its conciseness and aside from it, would be its use of exception handling with try-except block and raising exceptions with raise.

A good reading would be:

[docs.python.org/3/tutorial/errors](https://docs.python.org/3/tutorial/errors.html)

- file handling and writing
- mian function and `__main__`
