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
	
	
a. In the folder you just created, right click and select **Open in Terminal**. 
b. Type the following command to create all 20 folders at once and hit **enter**:

::

	mkdir 1297_{[ID]..[ID]}
	
*For example*::

	mkdir 1297_{150..170}
	
6. Each folder needs to contain the following files:
	a. The forensically packaged disk image (.E01)
	b. The ``imgMD5.txt`` file created during migration from a ``.img`` file to a ``.E01`` file
	c. The ``verify[MSSnumber_ID].txt`` file also created during migration from a ``.img`` file to a ``.E01`` file (e.g., ``verify1297_24.txt``)
	d. The ``fiwalk.xml`` file
	
You can either copy and paste the relevant files into their folder or use the command line to move files.

a. Move to the main collection folder using ::

	cd ../
	
b. Use the command line to copy the files

*Command line way to move files*::

	cp [MSSnumber_ID]/*.E01 [MSSnumber_ID]/*.xml [MSSnumber_ID]/*.txt 
	[new netID folder]/[directory made folder]
	
*For example*::
	
	cp 123_01/*.E01 123_01/*.xml 123_01/*.txt bedwa/123_01
	
*To do all the files at once using a 'for' loop*::
	
	for i in {[ID]..[ID]}
		do
		cp ./[MSSnumber_ID]_$i/*.E01 ./[MSSnumber_ID]_$i/*.xml ./[MSSnumber_ID]_$i/*.txt 
		./[new netID folder]/[MSSnumber_ID]_$i
		done
		
*For example*::

	for i in {01..05}
		do
		cp ./123_$i/*.E01 ./123_$i/*.xml ./123_$i/*.txt ./bedwa/123_$i
		done

------------
Create a Bag:
------------

7. Launch a terminal window, if you don't already have one open.
8. Navigate back to the *NetID* folder, using

::

	cd [netID]
	
9. Type the following command into the terminal window in order to package your first disk image folder as a Bag and hit **enter**::

::
	
	for i in {[ID]..[ID]}
		do
		bagit.py --md5 --sha1 --contact-name=[netID] ./[MSSnumber]_$i
		done
		
*For example*::

	for i in {01..05}
		do
		bagit.py --md5 --sha1 --contact-name=bedwa24 ./123_$i
		done
	
10. Wait for terminal prompt ($) to reappear.

-----------------
Validate the Bag:
-----------------

11. Type the following command in order to ensure that the newly created Bag is valid and hit **enter**:

::
	
	for i in {[ID]..[ID]}
		do
		bagit.py --validate ./[MSSnumber]_$i
		done
		
*For example*::

	for i in {01..05}
		do
		bagit.py --validate ./123_$i
		done
	
12. Wait for a confirmation message that the Bag is valid.
