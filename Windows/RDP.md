# Enable Remote Desktop (RDP) with Microsoft Account Sign-In
When using Windows account to logon (Windows Hello), there is a need to run the following command (cmdlet) 
to enable the account on the device. It needs the Microsoft account's password (not the Windows account password).
```powershell
# replace 'username@example.com' with your account
runas /u:MicrosoftAccount\username@example.com winver.exe
 ```
This command runs the “winver” program under the credentials of the user account specified. It sounds (and is) 
pretty simple, but what it does in the background is caches your Microsoft Account credentials. Since your local 
user account had no password, it wasn’t eligible for RDP use even if it has appropriate permissions otherwise. 
After supplying the password and pressing Enter, you’ll know it worked if you see the About Windows dialog 
box open. Go ahead and close it and the terminal window — you’re all done.

# Create an RDP Config File
Change the values for `full address:s:` and `username:s:` as well as `selectedmonitors:s:` with desired monitor numbers. Then, save the following configuration in a `.rdp` file extension.
**Note:** To find the monitor numbers, user the command `mstsc /l`.

```config
screen mode id:i:2
use multimon:i:1
selectedmonitors:s:0,2
desktopwidth:i:1920
desktopheight:i:1080
full address:s:192.168.10.10
username:s:MicrosoftAccount\username@example.com
session bpp:i:32
winposstr:s:0,1,2548,285,3118,809
compression:i:1
keyboardhook:i:2
audiocapturemode:i:1
videoplaybackmode:i:1
connection type:i:7
networkautodetect:i:1
bandwidthautodetect:i:1
displayconnectionbar:i:1
enableworkspacereconnect:i:0
disable wallpaper:i:0
allow font smoothing:i:0
allow desktop composition:i:0
disable full window drag:i:1
disable menu anims:i:1
disable themes:i:0
disable cursor setting:i:0
bitmapcachepersistenable:i:1
audiomode:i:0
redirectprinters:i:1
redirectcomports:i:1
redirectsmartcards:i:1
redirectwebauthn:i:1
redirectclipboard:i:1
redirectposdevices:i:0
autoreconnection enabled:i:1
authentication level:i:0
prompt for credentials:i:0
negotiate security layer:i:1
remoteapplicationmode:i:0
alternate shell:s:
shell working directory:s:
gatewayhostname:s:
gatewayusagemethod:i:4
gatewaycredentialssource:i:4
gatewayprofileusagemethod:i:0
promptcredentialonce:i:0
gatewaybrokeringtype:i:0
use redirection server name:i:0
rdgiskdcproxy:i:0
kdcproxyname:s:
enablerdsaadauth:i:0
camerastoredirect:s:*
devicestoredirect:s:*
drivestoredirect:s:*
use multimon:i:1
```
