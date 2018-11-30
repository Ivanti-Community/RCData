# RCData
You can download three zip files containing screenshot: 

* https://s3.amazonaws.com/rc-ml-sampledata/Win10.zip
* https://s3.amazonaws.com/rc-ml-sampledata/Win7.zip
* https://s3.amazonaws.com/rc-ml-sampledata/Win8.1.zip
 

There is one file for the each OS we gathered information from. The zip files contain a collection of screenshots in bmp format collected every 5 seconds along with a corresponding json file describing the top-level windows at the time of each screenshot.  The BMP file and the corresponding JSON file have identical filenames except for the file extension.  You can use the filename as an indication of the time when the snapshot was taken.

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

