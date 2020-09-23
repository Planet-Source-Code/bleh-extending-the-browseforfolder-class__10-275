<div align="center">

## Extending The BrowseForFolder Class


</div>

### Description

Simply adding a few more options to the BrowseForFolder class submitted by Chris Anderson.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[bleh](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/bleh.md)
**Level**          |Beginner
**User Rating**    |4.7 (47 globes from 10 users)
**Compatibility**  |C\#
**Category**       |[GUIs](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/guis__10-30.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/bleh-extending-the-browseforfolder-class__10-275/archive/master.zip)





### Source Code

<font face="Verdana" size="2">
<div align="center"><b>Extending The Browse For Folder Dialog Class</b></div>
<p>This code is simpily extending the Browse For Folder Dialog class that was on posted on PSC by Chris Andersen. After using his code, I was interested in knowing if there was any additional options available aside from just being able to set the title. I consulted the MSDN and this is what I came up with.
The above screen shot is showing the Browse For Folder dialog with StartLocation set to "MyDocuments" and Style set to "BrowseForEverything"</p>
<p><b>.StartLocation</b><br>
<hr width="100%" size="1" color="#000000">
The directory in which the browse dialog will start at. (duh) I haven't found a way to specifiy a certain path, like C:\PSC or something of that nature, but there are a number of members that we can use. They are:
<ul>
	<li>Desktop</li>
	<li>Favorites</li>
	<li>MyComputer</li>
	<li>MyDocuments</li>
	<li>MyPictures</li>
	<li>NetAndDialUpConnections</li>
	<li>NetworkNeighborhood</li>
	<li>Printers</li>
	<li>Recent</li>
	<li>SendTo</li>
	<li>StartMenu</li>
	<li>Templates</li>
</ul>
<p><b>.Style</b><br>
<hr width="100%" size="1" color="#000000">
They style of the browse dialog. We have a few different options to choose from.
<ul>
	<li>BrowseForComputer</li>
	<li>BrowseForEverything</li>
	<li>BrowseForPrinter</li>
	<li>RestrictToDomain</li>
	<li>RestrictToFilesystem</li>
	<li>RestrictToSubfolders</li>
	<li>ShowTextBox</li>
</ul>
</p>
<p><b>The Code</b><br>
<hr width="100%" size="1" color="#000000">
Here's an example of how to use the above methods in the Browse For Folder dialog.
<pre><font size="2">
using System;
using System.Windows.Forms;
using System.Windows.Forms.Design;
public class BrowseForFolder : FolderNameEditor
{
	FolderNameEditor.FolderBrowser bDialog;
	public BrowseForFolder()
	{
		bDialog = new FolderNameEditor.FolderBrowser();
	}
	public string browseDialog(string sTitle)
	{
		bDialog.Description = sTitle;<font color="green">
		bDialog.StartLocation = FolderNameEditor.FolderBrowserFolder.MyComputer;
		bDialog.Style = FolderNameEditor.FolderBrowserStyles.RestrictToDomain;</font>
		bDialog.ShowDialog();
		return bDialog.DirectoryPath;
	}
	~BrowseForFolder()
	{
		bDialog.Dispose();
	}
}
</font></pre>
</p>
<p><b>Useage:</b><br>
<hr width="100%" size="1" color="#000000">
To use this class, make sure you <b>add a reference to System.Design.DLL</b>. Call the class like so:
<pre><font size="2">
BrowseForFolder myDialog = new BrowseForFolder();
MessageBox.Show(myDialog.browseDialog("Dialog Title Goes Here");
</pre>
It's pretty simple. Thanks again to Chris Anderson for the original code.

