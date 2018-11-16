========================================================
Migrating KryoFlux image files in preparation for ingest
========================================================

-----------------
Before you begin:
-----------------

* This workflow uses tools stored as part of the BitCurator suite. If necessary, restart the Digital Archives Lab workstation and boot to the BitCurator hard drive.
* Ensure that the Digital Archives Lab workstation is not connected to the Internet by unplugging the ethernet cable.

----------------------------
Locate existing image files:
----------------------------

1. Ensure that the Digital Archives hard drive dock is powered on.
2. Open a terminal window but right-clicking anywhere on the Desktop and selecting **Open Terminal**.
3. Navigate to the directory in which existing image files are stored:

 - In the terminal window, type `cd`.
 - Double-click the correct volume in the left-hand toolbar.
 - Drag and drop the folder containing the existing image files into the terminal window. This will auto-populate the correct path for you.
 - Hit **enter**.
 
---------------------------------------------------------------
Migrate existing raw disk image to E01 file using ewfacquire:
---------------------------------------------------------------

4. Calculate an MD5 checksum for first existing raw disk image file. In the terminal, type the following command and hit **enter**:

::

  sudo md5sum ./[MSS#_ID]/[MSS#_ID].img 
  

5. In the terminal, type the following command and hit **enter**:

::

  ewfacquirestream ./[MSS#_ID]/[MSS#_ID].img -C [MSS#_ID] -D [Description of media] 
  -e [your name] -E [Collection name] -f encase6 -m removeable -M logical -l log_[MSS#_ID] 
  -t ./[MSS#_ID]/[MSS#_01].e01 > ./[MSS#_ID]
  
6. Review the MD5 checksum generated using the ``ewfaquirestream`` command; ensure it matches the MD5 checksum generated using the ``md5sum`` command.

-------------------------------------
Repeat for remaining raw disk images:
-------------------------------------

7. Repeat from step 4.

**Time-saving tip:** Use the up arrow to page through commands that you have previously run in the terminal window. Once you have found the correct command, you can edit it as needed before running it again.