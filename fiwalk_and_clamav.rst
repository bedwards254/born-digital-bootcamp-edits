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

4. In the terminal, type the following command and hit **enter**::

	for i in [MSSnumber]_{ID..ID} *enter*
		do *enter*
		
  		fiwalk -c clamconfig.txt -X /media/bcadmin/New\ Volume1/digitalArchives/diskImages/
		[collectionName]_diskImages/$i/fiwalk.xml /media/bcadmin/New\ Volume1/digitalArchives/diskImages/[collectionName]_diskImages/$i/$i.img *enter*
		
		done *enter*

*For example*::

	for i in 123_{01..06}
		do
		
  		fiwalk -c clamconfig.txt -X /media/bcadmin/New\ Volume/digitalArchives/diskImages/Mackey_diskImages/$i/
		fiwalk.xml /media/bcadmin/New\ Volume/digitalArchives/diskImages/Mackey_diskImages/$i/$i.E01
		
		done
	
------------------
Review fiwalk.xml:
------------------
5. Once you've run the command listed above, you should find a **fiwalk.xml** file in the same folder as your disk image. Open **fiwalk.xml**.
6. For each file listed in **fiwalk.xml**, review the ``<clamav_infected>`` tags. As long as the file is not infected with any viruses, their contents will be ``0``. If you notice that one or more files are contaminated, consult the digital archivist.

A quick way to search the XML file is to hit **Ctrl+F** on the keyboard and type in **"clamav_infected>** and hit enter. You can then type **1** to see if any infected files appear. 


  
