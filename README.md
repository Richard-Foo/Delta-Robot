### Rotational Delta Robot

#### Summary / Context

Mechanical and electronic designs for a “delta” style process robot.
In particular, a “rotational delta”, which is driven by 3 pivoting upper arms.
(As opposed to a Kossel or Rostock delta, and similar designs where each “elbow” is mounted to a shuttle moving along a rail.)

![Delta robot example](http://upload.wikimedia.org/wikipedia/commons/3/31/TOSY_Parallel_Robot.JPG)

This repo contains my own modifications to the [FirePick Delta](http://delta.firepick.org) project.
As such, I refer you to the [FirePick repo](https://github.com/firepick-delta/firepick-delta) for the more complete project.

My primary focus here is related to pick & place.
Use care when applying these mods to other use cases.

Code here is predominantly C++ and should be easily portable.
At the moment, I’m targeting the Raspberry Pi2 B platform for motor control, which is a major difference from the main project.  Among the key reasons are its dual-core processor (supporting 4 threads) and its raw clockspeed, both of which are important for super-granular path calculations.
It’s also an incredible value at $35 - we’ll see how much one board can take on.

The primary issue with using RPi2 for motor control is that its OS lacks realtime features.
However, it operates at 1GHz, so being able to signal a pulse at 20KHz with relatively low jitter would seem very achievable.
A fallback option would be to use RPi2 for the floating-point calculations and feed a constant stream of micro-steps to a very cheap, small realtime AVR controller to handle the actual driver pulse output.

#### Repository Structure

The following folders will appear as they have content committed:
* Control - Code that interfaces with the outside world - touchscreen, HTTP, etc.
* Documentation - Reference docs
* Electronics - PCB designs, schematics, and Gerber files
* Kinematics - Code for kinematic math, path calculations, and motor control
* Mechanical - 3D CAD designs, CNC G-code scripts, and parts images


#### Licensing

![CC-BY-SA](http://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/CC-BY-SA_icon.svg/320px-CC-BY-SA_icon.svg.png)

These files are licensed under [*Creative Commons Attribution-ShareAlike (CC BY-SA)*](https://creativecommons.org/licenses/by-sa/4.0/legalcode).  Commercial use is OK, but you are required under the license conditions to share your changes with the Internet, and also credit this author.  Before using this code, please familiarize yourself with the licensing terms and conditions.

[View License Summary](http://creativecommons.org/licenses/by-sa/4.0/) | [View Legal Code](https://creativecommons.org/licenses/by-sa/4.0/legalcode)

#### Maintainer

* [@Richard-Foo (Richard Hornbaker)](https://github.com/Richard-Foo)


#### A Few Words About Formats

* Electronic design files are in Eagle CAD format.  A free version is available which can view any file, but only edit smaller boards.
