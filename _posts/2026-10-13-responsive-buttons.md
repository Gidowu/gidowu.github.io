---
layout: post
title: "Responsive Buttons: Loops and Held Presses"
tags: [arduino, buttons, loops]
---

This week, I worked on an Arduino program called Responsive Buttons using the LilyPad USB Plus. The assignment builds on the random LED program we worked on in class. Each time I press the button, the program randomly selects one LED from pins 5 through 8. The LED stays on while I hold the button and turns off when I release it. I also had to make sure that the same LED is never selected twice in a row.

One part I had to think through was how to tell the difference between pressing and holding the button. Since the program keeps running through `loop()`, I needed a way to remember whether the button was already pressed. I used a boolean variable called `previousButton` to keep track of its previous state. This way, the program only selects a new LED when the button changes from not pressed to pressed. If I keep holding it, the same LED stays on. Once I release the button, the LED turns off.

I also used two `while` loops in my program. The first one helps set up the LED pins as outputs without writing the same code several times. The second one makes sure the program doesn't choose the same LED as the previous press. If it picks the same pin, it keeps generating another random pin until it gets a different one.

### Three Tips for My Past Self

**1. Understand the button states before writing the code.**

I would tell myself to first think about what should happen when the button is pressed, held, and released. Understanding these three situations makes it easier to figure out what conditions the program needs.

**2. Test what happens when the button is held.**

It's not enough to press the button quickly and see an LED turn on. I would also hold it for a few seconds to make sure the same LED stays on without changing or flickering. Then I would release it to check that it turns off.

**3. Pay attention to the condition inside a `while` loop.**

I would remind myself that a `while` loop keeps running as long as its condition is true. If nothing changes inside the loop, it could keep running forever. In my program, the random LED loop works because it generates another random pin each time until it finds one that is different from the previous LED.

### Thinking About My Choice of Conditionals

For this assignment, I used `if` and `else if` statements together with `previousButton` to control when the LED turns on and off. I chose this approach because I needed the program to recognize a new button press without treating a held button as another press.

Another way I could have done this was to use a `while` loop that waits until the button is released. That would also work for a simple program like this, but the problem is that the Arduino would stay inside that loop until I let go of the button.

For example, if I wanted to add other lights that keep changing, like the fireflies from our earlier assignments, those lights might stop updating while the button is held. Using `if` statements avoids that because the program checks the button and continues through the rest of `loop()`.

The trade-off is that I need an extra variable, `previousButton`, to remember the previous button state. Even with that extra variable, I think using `if` and `else if` makes more sense for this assignment, especially if I want to add more features later. A `while` loop would be useful if I only wanted the program to wait for the button to be released.
