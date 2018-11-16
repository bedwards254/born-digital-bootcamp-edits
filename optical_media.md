# Optical Media

## REVIEW OPTICAL DISC CONTENT:

1. Launch IsoBuster from the Desktop (Windows side).
2. Insert disc. After a few seconds, the disc’s file tree should load in the IsoBuster window.
3. Review the file tree to identify the contents of the disc:
    1. If the disc contains audiovisual data only, it should be re-routed through the AV workflow;
    2. If the disc contains non-audiovisual data only (e.g., documents, digital photographs), image using Guymager;
    3. If the disc contains mixed-mode data (both audiovisual and filesystem data), image using IsoBuster.

*NOTE*:	For more information about the Rose Library’s approach to optical discs, see the Capturing Data from Optical Discs policy.

## CAPTURE DISK IMAGE USING GUYMAGER:

1.	Press the F12 key as the Digital Archives workstation boots up.
2.	At the first boot page, press the enter key.
3.	At the second boot page, use the arrow key to scroll up to BitCurator. Press enter.
4.	Log-in to BitCurator as usual. 
5.	Right-click anywhere on the Desktop to create a new folder. Name it collectionName_diskImages_cds (e.g., Cleage_diskImages_cds).
6.	Insert disc, if not already loaded.
7.	Double-click the Imaging Tools folder on the Desktop.
8.	Double-click Guymager.
9.	Select the CD/DVD drive from the list.
10.	Right-click and select Acquire image.
11.	In the Acquire image window, complete the following:
    1.	Select Linux dd raw image;
    2.	De-select Split image files;
    3.	Use the browse button (…) to the right of Image directory to navigate to the folder created at step 5;
        1.	*NOTE*: Go media/bcadmin/New Volume/ to reach the hard drive properly
    4.	Enter an Image filename. Use MSS#_ID (e.g., 1000_01).
    5.	Check every box underneath Hash calculation / verification (Calculate MD5, Calculate SHA-1, Calculate SHA-256, Re-read source after acquisition for verifications (takes twice as long), and Verify image after acquisition (take twice as long))
12.	Hit Start. 

*NOTE*: You can check the progress of disk imaging by scrolling to the right in the Guymager window.

13.	In the folder created at step 4, right-click the disk image file and select Rename.
14.	Change the file extension from .dd to .iso.

*NOTE*:	You can review the disk image contents by right-clicking the object and selecting **Scripts > Mount Disk Image**. The disk image will be mounted on the Desktop. Double-click to open it and view files.
*NOTE*:	If you are doing multiple CDs at once, after you load the CD into the drive, hit “Rescan” in the top left corner of Guymager to have it appear in the list. 

## CAPTURE DISK IMAGE USING ISOBUSTER:

1.	If necessary, press the F12 key as the Digital Archives workstation boots up.
2.	At the first boot page, press the enter key.
3.	At the second boot page, use the arrow key to scroll down to Windows. Press enter.
4.	Power on the hard drive dock (DA Backup) and create a new folder in the diskImages directory, named collectionName_diskImages (e.g., Cleage_diskImages).
5.	Launch IsoBuster.
4.	Insert disc, if not already loaded. After a few seconds, the disc’s file tree should load in the IsoBuster window.
6.	Select the disc and right-click to open the Extraction menu.
7.	Select Extract CD <Image> > RAW (*.bin, *.iso).
8.	Navigate to the directory created at step 4 and enter a file name for the disk image. Use MSS#_ID (e.g., 1000_01).
9.	From the dropdown menu, change the Save as type to *.bin.
10.	Hit Save.

### NOTE:	If IsoBuster encounters an unreadable sector, an error message will ask if you want to 
retry imaging, select one of four options and proceed with imaging, or quit. One selection will be checked by default (probably Replace with User Data All Zeroes). Leave the default selection checked and hit Selection.
An Error(s) occurred during reading window will ask if you want to delete the file. Click No.
	Click Save on the next window that appears, saving it as a *.cue file. 

