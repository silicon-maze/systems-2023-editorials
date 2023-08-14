# **The Secrets of the Force**

Category: Web

Author: Aditya Harish

Answer / Flag: `MAZE{t3mpl4at3_____1nj3ct1on}`

## Problem Statement

You find yourself on a secret mission to unravel the mysteries of the Force. However, you face a challenge that only your astute skills can overcome.

You have discovered a remote outpost where the ancient Jedi artifacts are hidden. To access these artifacts, you must prove your worth by solving a series of challenges. One such challenge lies within a website known as The Holocron.

The Holocron, an enigmatic digital relic, holds the key to uncovering the whereabouts of the Jedi artifacts. It presents you with a simple task: enter your name to embrace the Force and reveal the path to your destiny. You know that the Jedi use a unique way to store their keys. For each website, the key is name of the website's folder. You also know that the Jedi use an insulating framework. 

## Hint

The Jedi decided that their system of storing keys was secure enough, so they decided to trust the user's input for all their templates. Can you exploit this?

## Solution

The key can be obtained by performing a template injection. Using the clues from original problem statement, we can determine that the website is built on Flask, which uses the Jinja2 template engine. 
A payload that can be used for this task can be something like : 
`{{[].__class__.__base__.__subclasses__()[144].__init__.__globals__['sys'].modules['os'].getcwd()}}`. 
We can view the directory name by using the `getcwd()` method of the `os` library. All objects in python are subclasses of the `object` class. We can list all the subclasses of the `object` class using the `__subclasses__` method. The 144th index of `__subclasses__` is the `catch_warnings` class, which imports the `sys` module, from which the `os` module can be accessed. Other paylods built on the same idea will also work. 
