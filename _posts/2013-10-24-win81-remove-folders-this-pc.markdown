---
layout: post
title: "Removing 'Folders' from 'This PC' on Windows 8.1"
date: 2013-10-24 12:22:00
tags:
 - windows
---

When I upgrade to Windows 8.1 I noticed that there now exists a 'Folders' group in what is now called 'This PC' (formerly 'My Computer').

![Folders in This PC](/assets/2013-10-24-win81-remove-folders-this-pc/Win81FoldersThisPC.png)

I didn't want this change because I like for the drives to be listed at the top, and all of the displayed folders were already easily accessible from the sidebar of the explorer window.

###Removing the Folders

Removing the folders was a simple registry edit that I gleaned from the [HowToGeek][] website by using a simple google search for 'windows 8.1 folders my computer'.  There it talks about which registry keys to remove and how to only remove select entries.

For my purposes, I wanted to remove them all, and I also wanted to remove them from the Open/Save dialogs of applications which their article does not cover.  However, the solution did exist in the comments of their article, which was to remove another set of registry keys for 64-bit computers. 

I have put together a set of `.reg` files for 32-bit and 64-bit systems to remove the folders from 'This PC' in Explorer and the Open/Save dialogs, which can be downloaded here:

[Click here to download the .zip file containing the registry fixes][download]

Once these changes are applied, the 'This PC' in Explorer and the Open/Save dialogs will look like this:

![This PC without folders](/assets/2013-10-24-win81-remove-folders-this-pc/Win81FoldersRemovedThisPC.png)

![Open dialog without folders](/assets/2013-10-24-win81-remove-folders-this-pc/Win81FoldersRemovedOpenDialog.png)

[HowToGeek]:http://www.howtogeek.com/168081/how-to-remove-the-folders-from-my-computer-in-windows-8.1/ 
[download]:/assets/2013-10-24-win81-remove-folders-this-pc/Win8.1RemoveFoldersRegKeys.zip