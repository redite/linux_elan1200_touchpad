## ELAN1200 touchpad driver
<br/>
A linux kernel module for ElanTech 1200 touchpad in Asus UX310UQ laptop. The way of processing the touchpad data by the default hid-multitouch driver results in random jumps of a cursor and random right-click events interpreted as two-finger taps during two-finger scrolling. This driver somewhat minimises the glitches by filtering out the unrelated reports from the touchpad and exporting ABS_MT_TOUCH_MAJOR as a diagonal plus offset.
<br/><br/>
In conjunction with limiting the MaxTapMove property of the synaptics xorg driver,
the delta between the coordinates of the touch and release events which decides whether an event is a move or a tap, the unwanted right-clicks occur even more rare.
<br/><br/>
The repository also contains a userspace driver, based on https://github.com/redmcg/FTE1001 which can be used for debugging the data from a hidraw device.
<br/><br/>
I also added an optional patch for the xorg synaptics driver 1.9.0, which adds an additional property, "MaxTapMoveTwoFingers", in order to have an ability to make rules for two-finger taps more strict than for single-finger taps.
<br/><br/>

The driver is tested on Debian 9, kernel 4.9.

### Problem report
https://bugzilla.kernel.org/show_bug.cgi?id=120181
