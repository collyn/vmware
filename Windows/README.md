# Create a script for Windows to auto expand your partition after you increase your virtual drive size

----
## Create script commands file
1. In the directory `C:\Windows\Setup` create a subdirectory called `Scripts` if it doesn’t already exist.
2. Enter the following commands into a new blank text file:
```
select disk 0
select partition 2
extend
```
3. Save and close the file `diskpart.txt` in the directory `C:\Windows\Setup\Scripts`
----
## Create executable batch file
Next we create an executable batch file, that will automatically run the script on every boot and apply the script.
1. Add the following commands to a new text file:
```
@echo off
diskpart /s C:\Windows\Setup\Scripts\diskpart.txt
del /Q /F C:\Windows\System32\Sysprep\unattend.xml
del /Q /F C:\Windows\Panther\unattend.xml
```
2. Save the file with filename `DiskExtension.bat` in the directory: 
`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`
(Depending on the text editor you are using, ensure that for `Save as type` you select as `All Files` and not `Text Documents (*.txt)`)
----
## Disable warning pop-up alerts
If you wish to disable the warning pop-up alerts that run on every boot up of the server (i.e. “Are you sure to run this script?”), please follow the steps below:
1. Go to `Control Panel -> User -> Change User Account Control settings`
2. Move the scroll bar to the bottom position labelled `Never notify me`
<img src="https://farm5.staticflickr.com/4262/35176689370_41428049f3_o.png">
