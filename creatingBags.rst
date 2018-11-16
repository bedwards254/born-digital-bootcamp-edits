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

*Option 1 (easy but tedious)* 
	a. Create each folder one-by-one by right-clicking and selecting **New Folder**. 
	b. Name each folder using the MSSnumber_ID.

*Option 2 (fast but requires the command line)*
	a. Launch a terminal window.
	b. Navigate to the folder created at step 4 by typing the following command:

::

	cd ../../media/bcadmin/New\ Volume/digitalArchives/diskImages/
	Mackey_diskImages/[your new folder]
	
	
c. Type the following command to create all 20 folders at once and hit **enter**:

::

	mkdir 1297_{[ID]..[ID]}
	
*For example*::

	mkdir 1297_{150..170}
	
6. Each folder needs to contain the following files:
	a. The forensically packaged disk image (.E01)
	b. The ``imgMD5.txt`` file created during migration from a ``.img`` file to a ``.E01`` file
	c. The ``verify[MSSnumber_ID].txt`` file also created during migration from a ``.img`` file to a ``.E01`` file (e.g., ``verify1297_24.txt``)
	d. The ``fiwalk.xml`` file
	
You can either copy and paste the relevant files into their folder or use the command line to move files (instructions forthcoming).

------------
Create a Bag:
------------

7. Launch a terminal window, if you don't already have one open.
8. Type the following command into the terminal window in order to package your first disk image folder as a Bag and hit **enter**:

::

	bagit.py --md5 --sha1 --contact-name=[your netID] 	
	./[MSSnumber_ID]
	
*For example*::

	bagit.py --md5 --sha1 --contact-name=netID 	
	./1297_173
	
9. Wait for terminal prompt ($) to reappear.

-----------------
Validate the Bag:
-----------------

10. Type the following command in order to ensure that the newly created Bag is valid and hit **enter**:

::

	bagit.py --validate ./[MSSnumber_ID]
	
*For example*::

	bagit.py --validate ./1297_150
	
11. Wait for a confirmation message that the Bag is valid.

-----------------------------
Repeat for remaining folders:
-----------------------------

12. For all remaining folders, repeat from step 8.

**Time-saving tip:** Use the up arrow to page through commands that you have previously run in the terminal window. Once you have found the correct command, you can edit it as needed before running it again.