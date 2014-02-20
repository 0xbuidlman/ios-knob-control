iOS Knob Control
================

This is a generic, reusable knob control you can insert into any application.
You provide any square image for the knob. The control animates rotation of the image
in response to a one-finger rotation gesture from the user. The knob has a number
of configurable modes:

- Linear return mode: Like a circular generalization of the UIPickerView control.
  Only certain discrete positions are allowed. The knob rotates
  to follow the user's gesture, but on release returns to an allowed position with
  one of several available animations. The time scale for the return animation may
  be configured as a property of the control.
- Wheel of Fortune mode: Like linear return, except for the animation after the
  user releases the knob. Only a narrow strip between each pair of segments is excluded, like
  the pegs on the rim of a carnival wheel. If the knob was released in one of those
  small excluded strips, it rotates just far enough to exit the excluded strip.
  Otherwise, the knob stays where the user leaves it. This mode is like continuous
  mode except for the behavior in the excluded strips and the availability of the
  positionIndex property.
- Continuous mode: Like a circular generalization of the UISlider control or a
  potentiometer/volume knob. Usually used with min. and max. angles, but can also
  be circular. Knob remains wherever the user leaves it and can attain any value
  between the min. and max. equally.
- Rotary dial mode (not available yet): Like an old rotary telephone dial.

The knob control can be circular, permitting the user to rotate it all the way around,
or it can have a min. and max. angle in continuous and discrete modes.

The control is distributed as a single pair of files (IOSKnobControl.h and IOSKnobControl.m
in this directory), which you can simply drop into your project. You have to provide at
least one image for the knob. You may use any of the images in this project or supply your own.

The knob control and all images must be square. Images will usually be circles or regular polygons, with a
transparent background or a solid one that matches the view behind it. However, the aspect
ratio must be 1:1. The effect of the animation is circular rotation. This only works if the control
is square. You can produce other effects, for example, by partially clipping a square control
or using an oblong background. But the control itself always has to be square.

The control honors the enabled property. That is, if you set enabled to NO, it enters the
UIControlStateDisabled and stops responding to user input. If specified, a disabled image is displayed
instead of the normal image. Even when disabled, the control's position may always be specified
at any time programmatically, with or without animation. With appropriate foreground and background
images, a disabled knob control may be used as a dial view to display a numeric value.

The KnobControlDemo.xcodeproj sample project can be used to build a simple demo app
to exercise the different modes of the control and provides examples of use. This demo project
uses storyboards and autolayout and so iOS 6.0 or greater. The control may easily be used in a
64-bit binary without problem. The demo project is configured to build a 64-bit binary and does
so without complaint.

The control itself, the IOSKnobControl class, may be compiled down to iOS 5.0, but the demo
project will not build if the iOS Deployment Target is set below 6.0 for reasons that have
nothing to do with the control. The control uses ARC, so it cannot be used below iOS 5.0
without modification. It has not been tested below iOS 6.1, however, and there may be problems
there that have not yet been discovered.

Known bugs and other issues are tracked on [Github](https://github.com/jdee/ios-knob-control/issues).

---

Notes
-----

- The control now supports a different image for each control state, like the UIButton control.
  It also enters the highlighted mode any time there is a touch down in the control, particularly
  while being dragged. This is analogous to the behavior of the UIButton control, which remains
  in the UIControlStateHighlighted as long as a touch is down in the control's frame.
- Not all combinations of parameters work at the moment in the demo app, but most combinations
  work if you do it yourself. The reason is that I always use the same hexagonal knob image
  in the demo app in discrete mode. That could be confusing with a min. and max., so I
  disabled the circular switch and the min. and max. fields in discrete mode. But the
  control should work with that combination, if you have an image that makes sense for it.
  You can certainly go into the sample project and comment out all use of the
  imageNamed:@"hexagon" and make sure to always use imageNamed:@"knob", enable all the
  controls and observe the behavior with just about any combination of parameters. Meaning
  and usage is explained for everything in the IOSKnobControl.h file.

Media
-----

Some images (the nice ones) courtesy of Mike Calvert (@bloodymonster).

License
=======

The software and media here are available under [The BSD 3-Clause License](http://opensource.org/licenses/BSD-3-Clause):

```
Copyright (c) 2013-14, Jimmy Dee
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted
provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions
   and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions
   and the following disclaimer in the documentation and/or other materials provided with the
   distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse
   or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR
    IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND
    FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR
    CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
    CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
    SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
    THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
    OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
    POSSIBILITY OF SUCH DAMAGE.
```