---
layout: post
title: "Simultaneous Fireflies: Three Patterns, One Program"
date: 2026-10-18
---

This week, I worked on the Simultaneous Fireflies project using my LilyPad USB Plus. The goal was to write one Arduino program that makes three sets of LEDs follow different firefly patterns at the same time.

The first firefly is the Big Dipper, which uses the built-in red LED. It starts flashing every 3 seconds, gradually increasing its brightness by 30 every 0.1 seconds before turning off. The second is the Flash Bulb, which uses two yellow LEDs. It turns on for half a second every 4 seconds. The last one is the Blue Ghost, which uses two blue LEDs. Unlike the others, it stays on and randomly increases or decreases its brightness by 50 every 0.5 seconds, while staying within the brightness range of 0 to 255.

One thing I had to figure out was how to make all three patterns work together without one interrupting the others. Since Arduino runs the code one instruction at a time, I couldn't use a separate delay for each firefly. Instead, I used one shared timer and a single delay of 100 milliseconds at the end of the loop. Each firefly checks the timer to know when to update its LED.

I also used boolean variables to keep track of whether the Big Dipper and Flash Bulb were currently flashing. This helped the program remember what each firefly was doing while the loop continued running. I kept the brightness and timing variables for each firefly separate so that their patterns would work independently.

**Photo of my project:**

![LilyPad ProtoSnap Plus with the yellow, blue, and red LEDs all lit](/assets/img/fireflies-output.jpg)

The photo shows all three fireflies lit at the same time. I pressed the Reset button and took the picture shortly afterward to capture them together.

**A tip for others trying this project for the first time:**

Before you start coding, look at your board and check which pins actually have an LED attached. The handout lists a few pin choices for each firefly, and some of them, like A9 and pin 10, are just empty sew tabs on the expansion ports, so nothing lights up even when your code is correct. The labels printed on the ProtoSnap board show which pins connect to the colored LED pairs. I used A5 for the yellow LEDs and A8 for the blue ones, which the handout also allows, and they lit up right away. 
