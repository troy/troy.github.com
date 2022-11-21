---
layout: post
title: One-click Canon PIXMA MX870 scanning in OS X
date: Aug 28, 2011
---

Problem: Canon PIXMA MX870 says "Set the PC to start scanning" when the "Black" or "Color" scan start buttons are pressed.

Solution: How I enabled one-button scanning

1. Install most of the OS X drivers and software from [canon.com](http://usa.canon.com/cusa/consumer/products/printers_multifunction/office_all_in_one_inkjet_printers/pixma_mx870#DriversAndSoftware). I think I installed all of the drivers, or at least ran their downloaded installers. As of this writing, that's ICA Driver, CUPS Driver, Scanner Driver, Mini Master Setup. I also installed MP Navigator and IJ Network Tool from the software downloads. Reboot.

2. After installing the "Canon IJ Network Scanner Selector," a printer/scanner icon should appear in the dock. The installer sets up the app to run at startup, which I left enabled. The dock dropdown "Scan images using the operations panel of the scanner" option is enabled. The scanner MAC address is listed and selected in "Open Settings":

    ![](http://images.yort.com/blog/canon-pixma-mx870-1.png)

    ![](http://images.yort.com/blog/canon-pixma-mx870-2.png)

3. Run MP Navigator (3.1) and on the main menu, there's an option in the upper right "One-click." Mouseover it and a different menu will be shown, including a "Start scanning by clicking the button" checkbox. This was not the default. I wish I was making this up.

    ![](http://images.yort.com/blog/canon-pixma-mx870-3.png)

4. On that MP Navigator One-click screen, click Preferences. Note that you may have 2 entries under "Product Name" ("MX870 Series" and "MX870 Series (Network: <Your MAC>)." I disabled "Compress scanned images when transferring" for both product names. On the Scanner Button Settings screen, I changed the paths under "Save to PC" but didn't make any other changes.

    ![](http://images.yort.com/blog/canon-pixma-mx870-4.png)

    ![](http://images.yort.com/blog/canon-pixma-mx870-5.png)

5. After making these changes, I was still seeing "Set the PC to start scanning" when I tried to scan. I shut down MP Navigator and restarted the printer (with the PC on) and it started auto-scanning. I didn't restart the PC except after step 1. I'm not sure whether the problem was a one-time issue because the settings changed or a recurring one with the order that they were originally powered on.

**Notes**

* My scanner LCD options (Document or Photo, DPI) are interpreted correctly. Scanning PDFs from the document feeder and bitmap images from the platen both work. Bitmaps from the ADF are not supported (the scanner says to use the platen). I haven't tried PDFs from the platen.

* Tested with: OS X 10.6.8, Canon IJ Network Scanner Selector 4.5.0, MP Navigator EX 3.1.3, MX870 driver 10.51.1.0.

Here's the printer options from System Preferences. I didn't make any changes:

![](http://images.yort.com/blog/canon-pixma-mx870-6.png)