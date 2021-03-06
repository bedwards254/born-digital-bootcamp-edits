.. _KryoFlux_setup:

======================================================
Transferring data from floppy disks using the KryoFlux
======================================================
-----------------
Before you begin:
-----------------
* This workflow uses tools stored in Windows. If necessary, restart the Digital Archives Lab workstation and boot to the Windows hard drive. You can find instructions on how to do this :ref:`here <BC_Windows>`.
* **Make sure the Digital Archives' Lab workstation is not connected to the internet.** Unplug the yellow ethernet cord at the back of the computer.
* As you unpack the KryoFlux, pay attention to the labels on the data cable and the KryoFlux enclosure. These will help ensure that the floppy disk drive and the KryoFlux are connected correctly.
* As you are setting up the KryoFlux, avoid placing any drives on the metal shelves over the workstations.
--------------------
Set-up instructions:
--------------------
1. Using the data cable, connect the KryoFlux to the correct floppy disk drive.

  - The data cable has three connectors: one for the KryoFlux; one for 3.5" floppy disk drives; and one for 5.25" floppy disk drives. Each connector on the cable is clearly labelled.
  - The data cable's red wire signifies pin 1. When connecting the data cable to the KryoFlux, be sure to align the red wire with the **Pin 1** label on the KryoFlux enclosure.
  
2. Using the USB cable, connect the KryoFlux to the lab workstation.

**Check that the associated driver is correct:**

3. In the Windows Search Box, type `device manager` and hit **enter**.
4. From the list, select **Universal Serial Bus Controllers**. If you see **KryoFlux Disk System** listed here, you can skip to step 11.
5. If you do not see **KryoFlux Disk System** listed, select **Ports (COM & LPT)**.
6. Right-click on **Bossa Program Port**.
7. Select **Update driver software**.
8. Select **Browse my computer for driver software**.
9. Select **Let me pick from a list of device drivers on my computer**.
10. At this stage you should see **KryoFlux Disk System** listed. Select it and hit **Next**. You should see the following confirmation message: **Windows has sucessfully updated your driver software**. Hit **Close**.

-------------------------
Complete KryoFlux set-up:
-------------------------

**NOTE:** All terminal commands are case-sensitive.

11. Type `cmd` into the Windows Search Box to open a terminal window.
12. Type the following command into the terminal window in order to navigate to the DTC folder and hit **enter**:

::

  cd ..\..\"Program Files (x86)"\kryoflux_2.51_windows\dtc

**NOTE:** For the coputer on the right in the lab, the file path should be as follows:

::

  cd ..\..\"Program Files (x86)"\kryoflux_3.00_windows\dtc

13. Type the following command and hit **enter** 

::

  dtc -c2

**NOTE:** The resulting prompt will likely say: **Control command rejected by the device. CM: maxtrack = 83**.

14. Ensure that the power cable is plugged in and connect the power adaptor to the back of the floppy disk drive.

  - The power adaptor has two connectors: the smaller one is for 3.5" floppy disk drives and the larger one is for 5.25" floppy disk drives. Both are clearly labelled.
  - When working with the 5.25" drive, in particular, be careful to make sure that the adaptor is properly aligned.
  - When disconnecting the adaptors, grip the white plastic piece and not the wires, as these are quite fragile and easily come loose if mishandled.
  
15. Insert a floppy disk.
16. Re-type the following command and hit **enter**:

::

  dtc -c2

**NOTE:** The resulting prompt will likely say something like: **CM: maxtrack = 83**.

---------------------
Capture stream files:
---------------------

17. Ensure that the Digital Archives hard drive dock is powered on.
18. Type the following command and hit **enter**:

::

  dtc -p -fJ:\digitalArchives\diskImages\[collectionName]_diskImages\
  [MSSnumber_ID]\[MSSnumber_ID] -i0 -i4 -i9 -l8

*For example*::

  dtc -p -fJ:\digitalArchives\diskImages\Lomax_diskImages\
  785_01\785_01 -i0 -i4 -i9 -l8

**NOTE:** You may need to double check the drive letter associated with the Digital Archives hard drive dock, as it may not always be ``J:``. If necessary, substitute the correct drive letter at the beginning of the file path.
19. Imaging will begin. Progress will be logged in the terminal window.

-------------------------------
Verify correct encoding format:
-------------------------------
20. Review the terminal output to determine which encoding format is correct:

  - Incorrect formats will register as ``unformatted``.
  - The correct format will be listed as ``OK``.
  - If MFM is the correct format, use ``-i4`` in step 21.
  - If Apple DOS 400/800 is the correct format, use ``-i9`` in step 21.
  - If neither format is correct, make a note of this and set disk aside for further review at a later date.
  
-------------------------------------
Capture correctly encoded disk image:
-------------------------------------
21. Type the following command and hit **enter**:

::

  	dtc -fJ:\digitalArchives\diskImages\[collectionName]_diskImages\
	[MSSnumber_ID]\[MSSnumber_ID] -i0 -fJ:\digitalArchives\
	diskImages\[collectionName]_diskImages\
	[MSSnumber_ID]\[MSSnumber_ID].img -i[4 or 9] -m1 -l8

*For example*::

  	dtc -fJ:\digitalArchives\diskImages\Lomax_diskImages\
	785_01\785_01 -i0 -fJ:\digitalArchives\diskImages\
	Lomax_diskImages\785_01\785_01.img -i4 -m1 -l8

22. Once imaging is complete, remove the floppy disk from the drive.
23. Label the disk with its MSSnumber\_ID. Be sure not to obscure any original labels.

-----------------------------------
Repeat for remaining floppy disks:
-----------------------------------
24. Insert next floppy disk.
25. Repeat from step 18.

**Time-saving tip:** Use the up arrow to page through commands that you have previously run in the terminal window. Once you have found the correct command, you can edit it as needed before running it again.

------------------------
Disconnect the KryoFlux:
------------------------
26. Click the **Safely remove hardware** icon and select **KryoFlux Disk System**.
27. Once it is safe to remove the KryoFlux, carefully disconnect the power (taking care not to pull on the wires), then the USB cable, and finally the data cable.
28. Replace all components in the KryoFlux box and return to the cabinet.
