+++
date = "2014-09-20T00:00:00"
description = "Drive an RC car with a bluetooth controller and a Raspberry Pi"
thumbnail = "images/automaton_pi.jpg"
image = "images/automaton_pi.jpg"
title = "Automaton Pi"
slug = "automaton-pi"
author = "Shaun Donachy"
draft = false
hidesidebar = true
+++
<style type="text/css">.centerVid{text-align:center;}</style>
### A raspberry pi project

The Automaton Pi project was created while I was studying machine learning with my fellow hackers [Mack](https://mackstump.com/) and [Ljiljana](https://github.com/zljiljana) and we wanted a hands-on project to work on.

### Our idea

If we can do object detection with a Raspberry Pi camera and use that same RPi to drive the vehicle, then we can create an autonomous RC car. Simple.

### The platform

First, we needed to get the platform ready, and the platform was our vehicle-mounted RPi. We acquired a pulse-width modulation servo driver from [Adafruit](https://adafruit.com). We hacked the Helion Animus RC car and replaced its all-in-one components with an electronic speed control. The steering servo was usable from the original vehicle.

<div class="image centered"><image src="../../images/automaton_pi_pwm_controller.png"></image></div>

We succeeded in getting the python script to control the steering servo of the vehicle.

<div class="centerVid"><video src="../../mov/wheel_servo_action.m4v" controls controlsList="nodownload" preload="metadata" poster="../../mov/wheel_servo_action.png"></video></div>

It was a challenge to reverse engineer the signal protocol for the electronic speed control. With some trial and error, we were able to get the motor to accelerate nicely. Getting reverse to work correctly took a bit more to figure out. Some RC enthusiast forums came in handy for solving that one.

<div class="centerVid"><video src="../../mov/esc_motor_action.m4v" controls controlsList="nodownload" preload="metadata" poster="../../mov/esc_motor_action.png"></video></div>

Mounted everything on the vehicle and took it for a spin! Wow, it works! The RPi is powered by a portable battery 5v battery intended for phone charging. Unfortunately using the keyboard doesnt provide as fine of control as an analog joystick might...

<div class="centerVid"><video src="../../mov/driving_action.m4v" controls controlsList="nodownload" preload="metadata" poster="../../mov/driving_action.png"></video></div>

Yes, that's pretty much what it looks like when I try to use a mouse and keyboard to play Rocket League. Maybe better. So the next challenge was getting bluetooth to work with a (ps3) controller. Then we needed to get the signal from the joystick into python. We ended up needing to switch from the Raspbian distribution to the arch pi distribution for an upgraded version of Bluez. Bluez understood how to pair and work with the PS3 controller, and pygame was able to pick up the controller inputs! We were in business! Even with the limited range it was exhilirating to be driving my (formerly busted) RC car again, but this time with controller!

Getting to this point was quite a challenge, but a great learning experience. The vehicle platform was then ready for the next phase. We need a method of capturing driver input and begin gathering training data on a task. We'll also need a fast way of accessing imagery from the RPi camera to perform some basic image processing. With some good luck we may yet have an automaton!

#### To Be Continued...
