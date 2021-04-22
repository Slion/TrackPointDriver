# TrackPointDriver
This is an alternative ThinkPad TrackPoint driver for Windows
offering a reliable TrackPoint scrolling experience.

# Story
I've been using a couple of [Lenovo ThinkPad USB Keyboard with TrackPoint] for over a decade
and they are still going strong.
The newest [ThinkPad TrackPoint Keyboard II], while pleasant to type on,
has a rather unimpressive layout by comparison. I ruled out upgrading for the time being.
One unique feature I use most on the TrackPoint is scrolling while holding down the middle button.
However with Lenovo [official driver], TrackPoint scrolling is rather unreliable.
On some application it just won't work.
On others like Visual Studio it will work for a while until it won't.
This driver primary goal is therefore to get the scrolling working everywhere, reliably,
exactly like your standard mouse wheel. 

# Feature
TrackPoint scrolling: hold down middle button to scroll vertically or horizontally using your TrackPoint.

# Download
Available from [slions.net].

# Installation
* First install the [official driver] from Lenovo.
You will still need it to be able to adjust sensitivy and other parameters from Windows Mouse Properties settings.
* Make sure you enable the [installation of unsigned drivers] on you computer. This is best done by running the following command as administrator: `bcdedit /set testsigning on`.
If this is denied because of UEFI Secure Boot and you can’t deactivate it then you won't be able to install that driver until a signed version is available.
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
Hold down the middle button and use your TrackPoint for mouse wheel emulation.
It works both vertically and horizontally.

# Hardware
While designed to work for [Lenovo ThinkPad USB Keyboard with TrackPoint]
this driver could potentially work for other TrackPoint hardware or even any mouse pointer device.

# Development

## prerequisite
After installing Visual Studio 2019 make sure you install the [Windows Driver Kit].
You may also need to add some missing components through Visual Studio Installer, notably those Spectre-mitigated libs.

## Debugging
Use [DebugView] and Enable Verbose Kernel Output from the Capture menu to obtain debug output from a driver debug build.
I have not used actual step-by-step debugging as it requires a more complex setup with an host and a target machine, physical or virtual.

# Omissions
Our target hardware can be configured by sending it HID reports. Settings such as TrackPoint sensitivity can thus be changed and possibly read I guess.
However we spared ourselves the task of reverse engineering that configuration protocol.
In fact it turns out using the [official driver] mouse properties page works just fine together with our custom driver. 
Nevertheless it's clearly possible to analyze communications between the [official driver] and the hardware using [WireShark] together with [USBPcap].
Note that [USBPcap] is bundled with [WireShark]. Such a reverse engineering was done for that [Linux driver].
See [sensitivity report](docs/trackpoint-sensitivity-report.md).

# Conclusion
That was an interesting dip in Windows kernel driver development.
Actually implementing a proper mouse wheel emulation from a mouse driver filter was really straight forward.
That brings the question: why could Lenevo engineers not get this done years ago? Go figure! 

# Resources
* Upstream forks:
  * [Invertible USB Mouse Driver Filter Driver]
  * [Microsoft Firefly Driver Sample]
* Lenovo ThinkPad USB Keyboard with TrackPoint:
  * [Official site]
  * [Official driver]
  * [User guide]
* [Linux driver] for the same hardware  

[Linux driver]: https://github.com/bseibold/tpkbdctl
[user guide]: http://download.lenovo.com/ibmdl/pub/pc/pccbbs/options_iso/45k1918_ug.pdf
[Official site]: https://support.lenovo.com/us/en/solutions/pd005137-thinkpad-usb-keyboard-with-trackpoint-overview
[Official driver]: https://download.lenovo.com/ibmdl/pub/pc/pccbbs/options/thinkpad_usb_keyboard_with_trackpoint_112.exe
[Lenovo ThinkPad USB Keyboard with TrackPoint]: https://support.lenovo.com/us/en/solutions/pd005137-thinkpad-usb-keyboard-with-trackpoint-overview
[ThinkPad TrackPoint Keyboard II]: https://www.lenovo.com/us/en/accessories-and-monitors/keyboards-and-mice/keyboards/KBD-BO-TrackPoint-KBD-US-English/p/4Y40X49493
[Windows Driver Kit]: https://docs.microsoft.com/en-us/windows-hardware/drivers/download-the-wdk
[Invertible USB Mouse Driver Filter Driver]: https://github.com/tthk/Invertible-USB-Mouse-Driver-Filter-Driver
[Microsoft Firefly Driver Sample]: https://github.com/microsoft/Windows-driver-samples/tree/master/hid/firefly
[WireShark]: https://www.wireshark.org
[USBPcap]: https://desowin.org/usbpcap/
[DebugView]: https://docs.microsoft.com/en-gb/sysinternals/downloads/debugview
[installation of unsigned drivers]: https://www.maketecheasier.com/install-unsigned-drivers-windows10/
[slions.net]: https://slions.net/resources/trackpoint-driver.12