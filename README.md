# RCData
You can download three zip files containing screenshot: 

* https://s3.amazonaws.com/rc-ml-sampledata/Win10.zip
* https://s3.amazonaws.com/rc-ml-sampledata/Win7.zip
* https://s3.amazonaws.com/rc-ml-sampledata/Win8.1.zip

UPDATE:
Two new files are available now:
https://s3.amazonaws.com/rc-ml-sampledata/Screenshots-With-Controls.zip 
https://s3.amazonaws.com/rc-ml-sampledata/snapshooter.zip 

The first file includes a few snapshots taken at 1024x768 resolution, and in addition to the BMP and JSON files, there's a third file with a .TXT extension.  This file contains a list of the controls visible on the foreground window (as returned by the Windows API GetForegroundWindow()).  Not all controls are actually listed, just these:


enum OutputClasses {
	OC_COMBOBOX,
	OC_STATIC,
	OC_SCROLLBAR,
	OC_EDIT,
	OC_DEFPUSHBUTTON,
	OC_PUSHBUTTON,
	OC_CHECKBOX,
	OC_CHECKBOX_CHECKED,
	OC_RADIOBUTTON,
	OC_RADIOBUTTON_CHECKED,
	OC_UNKNOWN
};

So in that TXT file, a 0 in the first column means it's a Combo Box, a 1 in that column means it's a Static control, and so forth.  The remaining columns are the bounding box of the control specified in <x>, <y>, <width>, and <height> order.  The values are all scaled between 0.0 and 1.0 in proportion to the width and height of the screen. 

There is one file for the each OS we gathered information from. The zip files contain a collection of screenshots in bmp format collected every 5 seconds along with a corresponding json file describing the top-level windows at the time of each screenshot.  The BMP file and the corresponding JSON file have identical filenames except for the file extension.  You can use the filename as an indication of the time when the snapshot was taken.

The "snapshooter.zip" file is a utility that allows you to create more snapshots quickly.  No promises on that file.  If it works, great.  If not... let us know, but we're not responsible for any trouble you might encounter.

The format of a bitmap can be found here - https://en.wikipedia.org/wiki/BMP_file_format.

The json file is an array of top-level windows, and you will see these attributes for each window:

* handle:  value to reference a specific window
* class:  See https://docs.microsoft.com/en-us/windows/desktop/winmsg/about-window-classes.  You will see some common window classes.

  * Shell_TrayWnd – the Windows task bar
  * SnapShooter App – the screen grabber app that we used to gather all the bitmaps
  * ApplicationFrameWindow - container for windows store applications
  
* title:  title of the window
* style:  Attributes of a window like the border or is it minimized.  See https://docs.microsoft.com/en-us/windows/desktop/winmsg/window-styles
* extstyle:  Extended windows attributes.  See https://docs.microsoft.com/en-us/windows/desktop/winmsg/extended-window-styles
* left, top, right, bottom:  dimensions and position of window on the screen

