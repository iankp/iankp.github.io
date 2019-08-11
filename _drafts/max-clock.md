---
layout: post
title: "Two Button Alarm Clock: Reviving an Old Project"
tags: avr microcontroller embedded c clock
excerpt: "In this post, I revive an old alarm clock that I made using the ATtiny84 microcontroller and the MAX7219 LED display driver. I also start the process of moving the circuit from a breadboard to a protoboard."
featured-image: /assets/images/maxclock/20190815_165822.jpeg
featured-image-alt: "Alarm clock on protoboard"
---

<!-- Introduction, description of past state of project -->
One of the projects that I created while I was still in high school was an alarm clock, based on one of Atmel's (now Microchip's) AVR microcontrollers, the ATtiny84. I found the standard four-button alarm clock interface (Clock, Alarm, Hour, Minute) to be somewhat bothersome, primarily due to the inability to "rewind" the time when setting it. (Did you just add one minute too many? Well, time to push the minute button 59 more times!) Additionally, this design is lacking in that it isn't very extensible – adding a second alarm, for example, means that an "Alarm 2" button must be added. As one can imagine, the number of buttons gets quickly out of hand when adding new functionality, leaving the user searching for buttons whenever they wish to configure the clock.

The solution? Reduce the number of buttons down to two. The interface then becomes a menu, rather than a button for each function. Pressing a single one of the two buttons navigates left or right in the menu, a short press of both buttons represents the "select" or "enter" action, and a long press on both buttons goes back.

(In hindsight, perhaps a four or five button "D-pad" arrangement would have been more flexible and intuitive. I think that the reason I went with this idea when I was starting the project was more to show that it could be done with only two buttons, rather than because it was necessarily the best idea.)

The display comprises six 7-segment display digits, each a separate module. These digits are driven by the MAX7219 LED display driver, which interfaces with the microcontroller using serial and can drive the LEDs directly.

# 2019 Hardware Update
<!-- Development done in 2019 -->
After retrieving the project from storage, the first step was of course to apply power and see if it still worked (after an initial visual inspection to make sure that everything appeared to be connected properly, that is). Sure enough, upon applying power, the display lit up and started counting from midnight (00:00:00).

At this point the components (the AVR, the MAX7219, and the display segments) were all located on the same breadboard. Unfortunately, I was too eager to continue with the project, and neglected to get a photo of this configuration, however I did get a photo after the display segments were removed:

{% include figure_centered.html src="/assets/images/maxclock/20190810_133150.jpeg" caption="Partial Original Breadboard Circuit" alt="partial original breadboard circuit" width="50%" %}

Because each 7-segment digit had the two rows of pins along the left and right sides of the digit, each had to be inserted into the breadboard sideways. This meant that the display was oriented vertically, and had to be read top-down. To resolve this awkwardness and to create a more permanent final product, I decided that my next step would be to solder the display—the digits and the MAX7219—onto a protoboard.

Here you can see the protoboard display partially complete. At this point, I was starting to regret using the parts I had on hand rather than just going out and buying an integrated display. So many wires to solder!

{% include figure_centered.html src="/assets/images/maxclock/20190810_144931.jpeg" caption="Partially Complete Protoboard Display" %}

Finally, the soldering was complete. The connection to the protoboard is the three serial wires (clock, data, and chip select/load) and ground/5&nbsp;V.

{% include figure_centered.html src="/assets/images/maxclock/20190815_165822.jpeg" caption="MAXClock, with the display now on a protoboard" alt="full view protoboard" %}

<!-- TODO: add more info about this circuit -->
The smaller board that is on the left of the above image generates a 32,768&nbsp;Hz square wave, used to keep time. I designed and etched this PCB with the help of one of my mentors when I was originally working on this project. I will add more information about this board at a later date.

<!-- TODO Video demo here -->
I'll update this post with a video demo later, as well.

In my next post, I will be looking at the software that I wrote for this device. I would like to add several features, including button debounce, digit flashing when setting the time, and support for alarms.

# External Links
* [ATtiny84](https://www.microchip.com/wwwproducts/en/ATTINY84)
* [MAX7219](https://www.maximintegrated.com/en/products/power/display-power-control/MAX7219.html)
