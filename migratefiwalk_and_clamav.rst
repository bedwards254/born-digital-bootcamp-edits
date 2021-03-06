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
2. Locate **fiwalk.bash** on the desktop and double-click. 
3. The file should look like this: 

::

  	cd /home/bcadmin/.fiwalk

	for i in [MSSnumber]_{ID..ID} 
		do
		
  		fiwalk -c clamconfig.txt -X /media/bcadmin/New\ Volume1/digitalArchives/diskImages/
		[collectionName]_diskImages/$i/fiwalk.xml /media/bcadmin/New\ Volume1/digitalArchives/diskImages/[collectionName]_diskImages/$i/$i.img *enter*
		
		done
		
4. Edit the information in brackets [ ] above to match your collection information. The ID numbers should equal
the folder numbers you are wanting to scan. 

*For example*::

	for i in 123_{01..06}
		do
		
  		fiwalk -c clamconfig.txt -X /media/bcadmin/New\ Volume/digitalArchives/diskImages/Mackey_diskImages/$i/
		fiwalk.xml /media/bcadmin/New\ Volume/digitalArchives/diskImages/Mackey_diskImages/$i/$i.E01
		
		done
		
5. **SAVE** the file and close it. 

	*If you do not save the file, the script will not run correctly*

6. Open a terminal window but right-clicking anywhere on the Desktop and selecting **Open Terminal**.
7. In the terminal, navigate to the Desktop using

::


	cd Desktop


8. Type **bash fiwalk.bash** and hit **enter**
	
------------------
Review fiwalk.xml:
------------------
9. Once you've run the command listed above, you should find a **fiwalk.xml** file in the same folder as your disk image. Open **fiwalk.xml**.
10. For each file listed in **fiwalk.xml**, review the ``<clamav_infected>`` tags. As long as the file is not infected with any viruses, their contents will be ``0``. If you notice that one or more files are contaminated, consult the digital archivist.

**Time-saving tip:** A quick way to search the XML file is to hit **Ctrl+F** on the keyboard and type in **"clamav_infected>"** and hit enter. You can then type **1** after the end **>** to see if any infected files appear. 


  
