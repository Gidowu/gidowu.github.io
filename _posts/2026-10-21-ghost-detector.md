---
layout: post
title: Ghost Detector
date: 2026-10-21
---

For this project I made a ghost detector with my LilyPad Arduino. The idea is that ghosts only show up when it is dark and cold so the board checks a light sensor and a temperature sensor. When both of them say "dark" and "cold," it sounds the alarm. The alarm is all the red lights turning on: the two red LEDs on the ProtoSnap board and the red part of the little RGB light in the middle of the board. If it is not dark and cold, every light stays off.

The light sensor is already built into the ProtoSnap but the temperature sensor is a separate piece. I connected it to the board with three alligator clips: one for the signal to the A9 tab, one for power, and one for ground.

The program reads both sensors over and over. The light sensor gives a number and in my room it reads about 70 with the lights on and about 0 when I cover it with my hand. The temperature sensor gives a raw number too so the program has to turn it into voltage, then Celsius, then Fahrenheit before it means anything. Then it compares both readings to a "dark" limit and a "cold" limit. I set my cold limit just above my room's temperature so I could test the alarm without needing anything freezing.

For the extra credit, the board figures out the limits by itself. For the first 30 seconds after it turns on, a green light stays on while it keeps track of the lowest and highest readings it sees from both sensors. Then it sets each limit halfway between those two numbers. I made it so the detector still works the whole time, even if the board doesn't learn anything useful in those 30 seconds.

Here is the board with the alarm going off:

![The red lights on during the ghost alarm](/assets/img/ghost-detector-output.jpg)

**Tip for my past self:** Don't just guess the numbers for "dark" and "cold." Find out what your sensors actually read in your own room first. Cover the light sensor with your hand and see how far the number drops and warm the temperature sensor with the warmth of your hand to see how much it moves. Every room is different so a guess is almost always wrong and once you know the real numbers the limits are easy to pick.
