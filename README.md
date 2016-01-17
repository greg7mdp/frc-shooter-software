# frc-shooter-software


This repository describes the shooter software for the robotics FRC Stronghold 2016 competition, running on a Raspberry Pi 2 model B.

One of the goals of this robotics came is to be able to pick up large foam balls from the ground, and to shoot them through a hole placed on a wall approx. 8 feet high. The software described here needs to be able to control the robot to move in position, and the shooter to automatically shoot the ball through the hole when in range. 

Here is the full [game manual](https://firstfrc.blob.core.windows.net/frc2016manuals/GameManual/FRC-2016-game-manual.pdf).

I code in C++ every day (and like it), so I plan on using C++ for this development. [OpenCV](http://opencv.org/) seems to be the standard for processing the camera output, so that's what I'll use. This is my first try at robotics, so I thought I would take baby steps and proceed as follows:

1. setup raspberry pi with camera attached to the swing/tilt servo, and use OpenCV to do face detection and have the camera track the detected face.
2. mount raspberry pi (from now on called *PI*) and camera to the robot, with a flashlight attached to the servo in the same axis as the camera, and see if we can have the camera trach the target when the robot is driven around.
3. finally connect the raspi to the [roboRIO](https://decibel.ni.com/content/docs/DOC-30419) and control the shooter and vehicle to shoot the boulders.

### Initial hardware order from Amazon

* CanaKit Raspberry Pi 2 Ultimate Starter Kit with WiFi ($84.99 - [amazon](http://www.amazon.com/gp/product/B00G1PNG54))
* Raspberry PI 5MP Camera Board Module ($24.99 - [amazon](http://www.amazon.com/gp/product/B00E1GGE40))
* Mini Pan-Tilt Kit - Assembled with Micro Servos  ($24.99 - [amazon](http://www.amazon.com/gp/product/B00PY3LQ2Y))

### First attempt with the Raspi

When the order arrived (love Amazon's 2 day shipping), I quickly connected everything together. The USB ports are very tight, so make sure you align the connectors well and gently wiggle them, and they will slide right in. The camera connector is tricky, you need to pull up a small white plastic tab on the top, slide in the ribbon, and push the plastic tab back down. Connected a spare monitor via the HDMI cable, et voila! 

After inserting the micro sd memory card and connecting the micto-usb power supply, the system booted right up into [NOOBS](https://www.raspberrypi.org/help/noobs-setup/), an utility program which allows to select and install a real operating system. 

**Note:** If you don't have a sd card with [NOOBS](https://www.raspberrypi.org/help/noobs-setup/) preinstalled, you can download it from [there](https://www.raspberrypi.org/downloads/noobs/), and just copy the contents of this unzipped archive to a freshly formatted (FAT) sd card.

The PI booted into NOOBS in a couple seconds, and from there it was super easy to install [raspbian](https://www.raspbian.org/), the Ubuntu based lunix operating system which is optimized for the PI. Raspbian booted straight into an X11 desktop, which has a command window and a web browser. I found I had ro run a few commands immediately:

- sudo dpkg-reconfigure tzdata  > update the timezone for the system clock
- 

