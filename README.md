# frc-shooter-software


This repository describes the shooter software for the robotics FRC Stronghold 2016 competition, running on a Raspberry Pi 2 model B.

One of the goals of this robotics game is to be able to pick up large foam balls from the ground, and to shoot them through a hole placed on a wall approx. 8 feet high. The software described here needs to be able to control the robot to move it in position, and the shooter to automatically shoot the ball through the hole when in range. 

Here is the full [game manual](https://firstfrc.blob.core.windows.net/frc2016manuals/GameManual/FRC-2016-game-manual.pdf).

I code in C++ every day (and like it), so I plan on using C++ for this development. [OpenCV](http://opencv.org/) seems to be the standard for processing the camera output, so that's what I'll use. This is my first try at robotics, so I thought I would take baby steps and proceed as follows:

1. setup raspberry pi with camera attached to the swing/tilt servo, and use OpenCV to do face detection and have the camera track the detected face.
2. mount the Raspberry PI (from now on called *The PI*) and camera to the robot, with a flashlight attached to the servo in the same axis as the camera, and see if we can have the camera trach the target when the robot is driven around.
3. finally connect the PI to the [roboRIO](https://decibel.ni.com/content/docs/DOC-30419) and control the shooter and vehicle to shoot the boulders.

### Initial hardware order from Amazon

* CanaKit Raspberry Pi 2 Ultimate Starter Kit with WiFi ($84.99 - [amazon](http://www.amazon.com/gp/product/B00G1PNG54))
* Raspberry PI 5MP Camera Board Module ($24.99 - [amazon](http://www.amazon.com/gp/product/B00E1GGE40))
* Mini Pan-Tilt Kit - Assembled with Micro Servos  ($24.99 - [amazon](http://www.amazon.com/gp/product/B00PY3LQ2Y))

### First attempt with the PI

When the order arrived (love Amazon's 2 day shipping), I quickly connected everything together. The USB ports are very tight, so make sure you align the connectors well and gently wiggle them, and they will slide right in. The camera connector is tricky, you need to pull up a small white plastic tab on the top, slide in the ribbon, and push the plastic tab back down. Connected a spare monitor via the HDMI cable, et voila! 

After inserting the micro sd memory card and connecting the micto-usb power supply, the system booted right up into [NOOBS](https://www.raspberrypi.org/help/noobs-setup/), an utility program which allows to select and install a real operating system. 

**Note:** If you don't have a sd card with [NOOBS](https://www.raspberrypi.org/help/noobs-setup/) preinstalled, you can download it from [here](https://www.raspberrypi.org/downloads/noobs/), and just copy the contents of this unzipped archive to a freshly formatted (FAT) sd card.

The PI booted into NOOBS in a couple seconds, and from there it was super easy to install [raspbian](https://www.raspbian.org/), the Ubuntu based lunix operating system which is optimized for the PI. Raspbian booted straight into an X11 desktop, which has a command window and a web browser. I found I had ro run a few commands immediately ([ymmv](http://www.urbandictionary.com/define.php?term=ymmv))

```
- sudo dpkg-reconfigure tzdata  # update the timezone for the system clock
- sudo apt-get update           # update the system package list
- sudo apt-get upgrade          # if you feel like it - upgrade all installed packages
- sudo vi /boot/config.txt      # set disable_overscan=1 and comment out other overscan lines
- sudo apt-get emacs            # what can I say, I like emacs, but vi and nano are OK too
- transfer startup files from my PC (.emacs, .el files, .Xdefaults, etc...) using Filezilla downloaded on the PC
  use: sftp://ip_address, username=raspberry, password=pi
- sudo raspi-config             # enable camera
- sudo reboot                   # 
- raspistill -o img.jpg         # test camera 
```

### A word of warning

Well, I coundn't get the camera to work. So I played with it, connected and disconnected it multiple times, used [raspi-config](https://www.raspberrypi.org/documentation/configuration/raspi-config.md), rebooted multiple times... still no luck. During the "apt-get upgrade" which took some time, I was looking at the PI and turning it in my hands when I involunarily popped the sd card out. Big mistake: the card was in the middle of being written to and apparently this destroyed the card. I couldn't boot on it anymore and it isnt recognized on my other PCs anymore.

Unfortunately, I have lots of regular size SD cards around, but no other micro sd, and the spare one I have ordered from Amazon will only arrive tomorrow (sunday). So this ends my PI experiments for the day and gives me the opportunity to write this account you are reading right now.

