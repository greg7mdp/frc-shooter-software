# frc-shooter-software


This repository describes the shooter software for the robotics FRC Stringhold 2016 competition, running on a Raspberry Pi 2 model B.

One of the goals of this robotics came is to be able to pick up large foam balls from the ground, and to shoot them through a hole placed on a wall approx. 8 feet high. The software described here needs to be able to control the robot to move in position, and the shooter to automatically shoot the ball through the hole when in range. 

Here is the full [game manual](https://firstfrc.blob.core.windows.net/frc2016manuals/GameManual/FRC-2016-game-manual.pdf).

I code in C++ every day (and like it), so I plan on using C++ for this development. [OpenCV](http://opencv.org/) seems to be the standard for processing the camera output, so that's what I'll use. This is my first try at robotics, so I thought I would take baby steps and proceed as follows:

### Initial hardware order from Amazon:

* Raspberry PI 5MP Camera Board Module ($24.99 - [amazon](http://www.amazon.com/gp/product/B00E1GGE40))
* CanaKit Raspberry Pi 2 Ultimate Starter Kit with WiFi ($84.99 - [amazon](http://www.amazon.com/gp/product/B00G1PNG54))
* Mini Pan-Tilt Kit - Assembled with Micro Servos  ($24.99 - [amazon](http://www.amazon.com/gp/product/B00PY3LQ2Y))
