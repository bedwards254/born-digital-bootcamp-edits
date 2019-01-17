.. _creatingBags:

========================================================
Packaging disk images and supplemental files using BagIt
========================================================

-----------------
Before you begin:
-----------------

* This workflow uses tools stored in BitCurator. If necessary, restart the Digital Archives Lab workstation and boot to the BitCurator hard drive. You can find instructions on how to do this :ref:`here <BC_Windows>`.
* Ensure that the Digital Archives Lab workstation is not connected to the Internet by unplugging the ethernet cable.

---------------
Create folders:
---------------

1. Ensure that the Digital Archives hard drive dock is powered on. 
2. Ensure that the Digital Archives hard drive is mounted inside BitCurator. If necessary, double-click the **New Volume** icon in the toolbar on the left-hand side of the screen. Once the Digital Archives hard drive is mounted, a **New Volume** icon will appear on the Desktop.
3. Double-click the **New Volume** icon on the Desktop and navigate to the **Mackey_diskImages** folder.
4. Create a new folder inside the **Mackey_diskImages** folder. Name the folder using your netID or name.
5. Move into the folder created at step 4.

**NOTE:** Before beginning the process of creating bags, each forensically packaged disk image (.E01) must be placed with any supplemental files inside a folder named using the MSSnumber_ID (e.g., 1297_01). There are two ways to create these folders:
	
	
a. Type the following command to create all 20 folders at once and hit **enter**:

::

	mkdir 1297_{[ID]..[ID]}
	
*For example*::

	mkdir 1297_{150..170}
	
6. Each folder needs to contain the following files:
	a. The forensically packaged disk image (.E01)
	b. The ``imgMD5.txt`` file created during migration from a ``.img`` file to a ``.E01`` file
	c. The ``verify[MSSnumber_ID].txt`` file also created during migration from a ``.img`` file to a ``.E01`` file (e.g., ``verify1297_24.txt``)
	d. The ``fiwalk.xml`` file
	
7. On the desktop, look for *copy.bash* and click on it to open. 

The file should look like this:
	
::
	
	for i in [MSSnumber]_{[ID]..[ID]}
		do
		cp ./[MSSnumber_ID]_$i/*.E01 ./[MSSnumber_ID]_$i/*.txt ./[MSSnumber_ID]_$i/*.xml 
		./[new netID folder]/[MSSnumber_ID]_$i
		done
		
8. Edit the information in brackets [ ] above to match your collection information. The ID numbers should equal
the folder numbers you are wanting to copy. 
		
*For example*::

	for i in 123_{01..05}
		do
		cp ./123_$i/*.E01 ./123_$i/*.xml ./123_$i/*.txt ./bedwa/$i
		done
		
9. In the terminal window, navigate to the desktop using 

:: 

	cd Desktop

10. Type in **bash copy.bash** and hit **enter**

------------
Create a Bag:
------------

11. On the Desktop, locate the file **bagger.bash** and click to open it.

The file should look like this: 

::
	
	cd /media/bcadmin/New\ Volume1/digitalArchives/diskImages/[collectionName]_diskImages/[netID]
	
	for i in [MSSnumber]_{[ID]..[ID]}
		do
		
		bagit.py --md5 --sha1 --contact-name=[netID] ./$i
		bagit.py --validate ./$i
		echo
		
		done
		
*For example*::

	for i in 123_{01..05}
		do
		
		bagit.py --md5 --sha1 --contact-name=bedwa24 ./$i
		bagit.py --validate ./$i
		echo
		
		done

12. Edit the information located in the brackets [] to match your collection information. The ID numbers should equal the folder numbers you are wanting to bag. 
		
13. **SAVE** the file and close it.
	*If you do not save the file, it will not run correctly.* 
	
14. In the terminal window, type in **bash bagger.bash** and hit **enter**
