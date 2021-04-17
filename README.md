# TrackPointDriver
This is an alternative ThinkPad TrackPoint driver for Windows offering a reliable TrackPoint scrolling experience.

# Story
I've been using a couple of [Lenovo ThinkPad USB Keyboard with TrackPoint] for over a decade and they are still going strong.
The newest [ThinkPad TrackPoint Keyboard II], while pleasant to type on, has a rather unimpressive layout by comparison. I ruled out upgrading for the time being.
The one feature I use most on the TrackPoint is scrolling while holding down the middle button.
However Lenovo [official driver] TrackPoint scrolling implementation is rather unreliable.
On some application it just won't work on others like Visual Studio it will work for a while until it won't.
This driver primary goal is therefore to get the scrolling working everywhere and reliably exactly like your standard mouse wheel. 

# Feature
TrackPoint scrolling: hold down middle button to scroll vertically or horizontally using your TrackPoint.

# Installation
* First install the [official driver] from Lenovo.
* TODO: Make sure test signing is enabled on your computer.
* Go to Windows Device Manager.
* Locate your TrackPoint device below "Mice and other pointing devices".
* Right click your TrackPoint device and select "Update driver".
* Click "Browse my computer for drivers".
* Click "Let me pick a list off available drivers on my computer".
* Click "Have Disk…" button.
* "Browse" to this driver location on your computer and select the INF file.
* Select the driver and click "Next".
* Validate various Windows warning messages if needed until installation succeeds.

# Usage
You can still adjust TrackPoint stick sensitivity as usual from Windows Mouse Properties.

# Hardware
While designed to work for [Lenovo ThinkPad USB Keyboard with TrackPoint] this driver could potentially work for other TrackPoint hardware or even any mouse pointer device.

# Resources
* [Linux driver] for the same hardware.
* Lenovo ThinkPad USB Keyboard with TrackPoint:
  * [Official site]
  * [Official driver]
  * [User guide]

[Linux driver]: https://github.com/bseibold/tpkbdctl
[user guide]: http://download.lenovo.com/ibmdl/pub/pc/pccbbs/options_iso/45k1918_ug.pdf
[Official site]: https://support.lenovo.com/us/en/solutions/pd005137-thinkpad-usb-keyboard-with-trackpoint-overview
[Official driver]: https://download.lenovo.com/ibmdl/pub/pc/pccbbs/options/thinkpad_usb_keyboard_with_trackpoint_112.exe
[Lenovo ThinkPad USB Keyboard with TrackPoint]: https://support.lenovo.com/us/en/solutions/pd005137-thinkpad-usb-keyboard-with-trackpoint-overview
[ThinkPad TrackPoint Keyboard II]: https://www.lenovo.com/us/en/accessories-and-monitors/keyboards-and-mice/keyboards/KBD-BO-TrackPoint-KBD-US-English/p/4Y40X49493