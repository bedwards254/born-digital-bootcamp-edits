.. _img_migration:

========================================================
Migrating KryoFlux image files in preparation for ingest
========================================================

-----------------
Before you begin:
-----------------

* This workflow uses tools stored as part of the BitCurator suite. If necessary, restart the Digital Archives Lab workstation and boot to the BitCurator hard drive. You can find instructions on how to do this :ref:`here <BC_Windows>`.
* Ensure that the Digital Archives Lab workstation is not connected to the Internet by unplugging the ethernet cable.

----------------------------
Locate existing image files:
----------------------------

1. Ensure that the Digital Archives hard drive dock is powered on.
2. Open a terminal window but right-clicking anywhere on the Desktop and selecting **Open Terminal**.
3. Navigate to the directory in which existing image files are stored:

 - In the terminal window, type:
 
 ::
 
 	cd ../../media/bcadmin/New\ Volume/digitalArchives/diskImages/
	Mackey_diskImages
 
 - Hit **enter**.
 
-------------------------------------------------------
Calculate the MD5 checksum for the existing image file:
-------------------------------------------------------

4. Calculate and log the MD5 checksum for first existing raw disk image file. In the terminal, type the following command and hit **enter**:

::

  	md5sum [MSSnumber_ID]/[MSSnumber_ID].img >[MSSnumber_ID]/imgMD5.txt
	
*For example*::

	md5sum 1297_24/1297_24.img >1297_24/imgMD5.txt
	
This will create a new text file inside your folder that contains the MD5 checksum for the raw disk image.

-----------------------------------------------------
Migrate the existing raw disk image using ewfacquire:
-----------------------------------------------------
  
5. In the terminal, type the following command and hit **enter**:

::

	ewfacquire ./[MSSnumber_ID]/[MSSnumber_ID].img -C ["MSSnumber_ID"] -D 	
	["Description of media"] -e ["your netID"] -E ["Collection name"] -f 
	"encase6" -m 	"removable" -M "logical" -N "Migration from img" -c 
	"deflate" -o 0 -S "1.4 GiB" -P 512 -g 64 -t ./[MSSnumber_ID]/
	[MSSnumber_ID]
	
	
*For example*::

	ewfacquire ./1297_24/1297_24.img -C "1297_24" -D "3.5 inch floppy 
	disk" -e "netID" -E "Nathaniel Mackey papers" -f "encase6" -m 
	"removable" -M "logical" -N "Migration from img" -c "deflate" -o 0 
	-S "1.4 GiB" -P 512 -g 64 -t ./1297_24/1297_24


6. As prompted in the terminal window, hit **enter** five times. Look for acknowledgement that a new forensically packaged disk image has been successfully createdx: you should see an acquiry start and completion time, an MD5 hash (checksum) calculated over the data, and a confirmation message reading ``ewfacquire: SUCCESS``.
	
------------------------------------------
Verify the new disk image using ewfverify:
------------------------------------------

7.	In the terminal, type the following command and hit **enter**:

::

	ewfverify [MSSnumber_ID]/[MSSnumber_ID].E01 	
	>[MSSnumber_ID]/verify[MSSnumber_ID].txt
	
*For example*::

	ewfverify 1297_24/1297_24.E01 >1297_24/verify1297_01.txt
	
This will create another new text file inside your folder that contains verification information for the new forensically packaged disk image. Open and review the file to ensure that verification has been successful.

--------------------------------------------------------------------------
Compare checksums for raw disk image and forensically packaged disk image:
--------------------------------------------------------------------------

8. Open both the **MD5** and **verify** text files created at steps 4 and 7. Compare the first few characters in each MD5 hash to ensure that they match.

-------------------------------------
Repeat for remaining raw disk images:
-------------------------------------

7. Repeat from step 4.

**Time-saving tip:** Use the up arrow to page through commands that you have previously run in the terminal window. Once you have found the correct command, you can edit it as needed before running it again.