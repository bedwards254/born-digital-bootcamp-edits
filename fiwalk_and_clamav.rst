.. _fiwalk_and_clamav:

===============================================
Generating Fiwalk reports, with virus checking
===============================================

-----------------
Before you begin:
-----------------
* This workflow uses tools stored as part of the BitCurator suite. If necessary, restart the Digital Archives Lab workstation and boot to the BitCurator hard drive. You can find instructions on how to do this :ref:`here <BC_Windows>`.
* Ensure that the Digital Archives Lab workstation is not connected to the Internet by unplugging the ethernet cable.

----------------------------------
Run Fiwalk with the ClamAV plugin:
----------------------------------
1. Ensure that the Digital Archives hard drive dock is powered on.
2. Open a terminal window but right-clicking anywhere on the Desktop and selecting **Open Terminal**.
3. In the terminal, type the following command and hit **enter**:

::

  	cd /home/bcadmin/.fiwalk

4. In the terminal, type the following command and hit **enter**:

::

  	fiwalk -c clamconfig.txt -X /media/bcadmin/New\ 	
	Volume/digitalArchives/diskImages/
	[collectionName]_diskImages/[MSSnumber_ID]/fiwalk.xml 
	/media/bcadmin/New\ Volume/digitalArchives/diskImages
	/[collectionName]_diskImages/[MSSnumber_ID]/
	[disk image filename with extension]

*For example*::

  	fiwalk -c clamconfig.txt -X /media/bcadmin/New\ 	
	Volume/digitalArchives/diskImages/Mackey_diskImages/1297_01/
	fiwalk.xml /media/bcadmin/New\ Volume/digitalArchives/
	diskImages/Mackey_diskImages/1297_01/1297_01.E01
	
------------------
Review fiwalk.xml:
------------------
5. Once you've run the command listed above, you should find a **fiwalk.xml** file in the same folder as your disk image. Open **fiwalk.xml**.
6. For each file listed in **fiwalk.xml**, review the ``<clamav>`` tags. As long as the file is not infected with any viruses, their contents will be ``0``. If you notice that one or more files are contaminated, consult the digital archivist.

---------------------------------
Repeat for remaining disk images:
---------------------------------
7. For each remaining disk image, repeat from step 4.

**Time-saving tip:** Use the up arrow to page through commands that you have previously run in the terminal window. Once you have found the correct command, you can edit it as needed before running it again. 

  