# Taglist
## Source code
https://github.com/vim-scripts/taglist.vim
## Description
The "Tag List" plugin is a source code browser plugin for Vim.
## [How to use](https://github.com/vim-scripts/taglist.vim)

### Keys for taglist window
|Key|Description|
|:------|:-------|
|\<CR\>|Jump to the location where the tag under cursor is defined.|
|o|Jump to the location where the tag under cursor is defined in a new window.|
|P|Jump to the tag in the previous (Ctrl-W_p) window.|
|p|Display the tag definition in the file window and keep the cursor in the taglist window itself.|
|t|Jump to the tag in a new tab. If the file is alread opened in a tab, move to that tab.|
|Ctrl-t|Jump to the tag in a new tab.|
|\<Space\>|Display the prototype of the tag under the cursor.  For file names, display the full path to the file, file type and the number of tags. For tag types, display the tag type and the number of tags.|
|u|Update the tags listed in the taglist window|
|s|Change the sort order of the tags (by name or by order)|
|d|Remove the tags for the file under the cursor|
|x|Zoom-in or Zoom-out the taglist window|
|+|Open a fold|
|-|Close a fold|
|*|Open all folds|
|=|Close all folds|
|[[|Jump to the beginning of the previous file|
|\<Backspace\>|Jump to the beginning of the previous file|
|]]|Jump to the beginning of the next file|
|\<Tab\>|Jump to the beginning of the next file|
|q|Close the taglist window|
|\<F1\>|Display help|

### Options

|Option|Description|
|-----|-----|
|Tlist_Auto_Highlight_Tag|Automatically highlight the current tag in the taglist.|
|Tlist_Auto_Open|Open the taglist window when Vim starts.|
|Tlist_Auto_Update|Automatically update the taglist to include newly edited files.|
|Tlist_Close_On_Select|Close the taglist window when a file or tag is selected.|
|Tlist_Compact_Format|Remove extra information and blank lines from the taglist window.|
|Tlist_Ctags_Cmd|Specifies the path to the ctags utility.|
|Tlist_Display_Prototype|Show prototypes and not tags in the taglist window.|
|Tlist_Display_Tag_Scope|Show tag scope next to the tag name.|
|Tlist_Enable_Fold_Column|Show the fold indicator column in the taglist window.|
|Tlist_Exit_OnlyWindow|Close Vim if the taglist is the only window.|
|Tlist_File_Fold_Auto_Close|Close tag folds for inactive buffers.|
|Tlist_GainFocus_On_ToggleOpen|Jump to taglist window on open.|
|Tlist_Highlight_Tag_On_BufEnter|On entering a buffer, automatically highlight the current tag.|
|Tlist_Inc_Winwidth|Increase the Vim window width to accommodate the taglist window.|
|Tlist_Max_Submenu_Items|Maximum number of items in a tags sub-menu.|
|Tlist_Max_Tag_Length|Maximum tag length used in a tag menu entry.|
|Tlist_Process_File_Always|Process files even when the taglist window is closed.|
|Tlist_Show_Menu|Display the tags menu.|
|Tlist_Show_One_File|Show tags for the current buffer only.|
|Tlist_Sort_Type|Sort method used for arranging the tags.|
|Tlist_Use_Horiz_Window|Use a horizontally split window for the taglist window.|
|Tlist_Use_Right_Window|Place the taglist window on the right side.|
|Tlist_Use_SingleClick|Single click on a tag jumps to it.|
|Tlist_WinHeight|Horizontally split taglist window height.|
|Tlist_WinWidth|Vertically split taglist window width.|


### Commands

|Command|Description|
|-----|-----|
|:TlistAddFiles|Add multiple files to the taglist.|
|:TlistAddFilesRecursive|Add files recursively to the taglist.|
|:TlistClose|Close the taglist window.|
|:TlistDebug|Start logging of taglist debug messages.|
|:TlistLock|Stop adding new files to the taglist.|
|:TlistMessages|Display the logged taglist plugin debug messages.|
|:TlistOpen|Open and jump to the taglist window.|
|:TlistSessionSave|Save the information about files and tags in the taglist to a session file.|
|:TlistSessionLoad|Load the information about files and tags stored in a session file to taglist.|
|:TlistShowPrototype|Display the prototype of the tag at or before the specified line number.|
|:TlistShowTag|Display the name of the tag defined at or before the specified line number.|
|:TlistHighlightTag|Highlight the current tag in the taglist window.|
|:TlistToggle|Open or close (toggle) the taglist window.|
|:TlistUndebug|Stop logging of taglist debug messages.|
|:TlistUnlock|Start adding new files to the taglist.|
|:TlistUpdate|Update the tags for the current buffer.|


### More details
Input 
````
:help taglist.txt
````
in vim to get more details.

[Back to Home](https://husthed.github.io) [Upper Level](/Vim/vim)
