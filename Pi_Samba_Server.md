<html>

<h4>You will need:</h4>
<p>A storage medium (i.e. flash drive, sd card or ssd/hd), Raspberry pi, and a computer. Keyboard and wifi optional.</p>
<hr/>
<p>Download Raspberry Pi Imager from their website or from your package manager. Plug in your storage medium and boot up RPI-Imager.</p>
<p>Download, configure (The gear button on the bottom right) making sure to enable SSH (Unless you have a keyboard and monitor) and install Raspberry Pi OS, No Desktop, 32 bit to your storage medium.</p>

<h6>If you don't have a keyboard and monitor attached to the pi:</h6>
<p>Download nmap by running ```sudo apt install nmap | sudo pacman -S nmap```</p> 
<p>Next run ```ip a``` and make note of your ip address (0.0.0.0-255.255.255.255) then run ```nmap x.x.x.0/24``` replacing x's with your ip address.</p>
<p>Make note of the last few digits of each ip, or leave it on your terminal and dont clear it.<p>
<p>Plug in your storage medium to the pi and/or reboot. The pi will run a few programs then reboot twice.</p>
<p>Run the same nmap command again, the new address should be your Pi.</p>
<p>SSH into the pi by running ```ssh pi@x.x.x.x``` where x is the pi's address you just discovered</p>
<h6>If you do:</h6>
<p>Connect everything and boot up. It will reboot twice and then prompt you for login.</p>
<br/>
<p>Next run:</p>
```sudo apt update ; sudo apt upgrade ; sudo apt autoclean ; sudo apt autoremove ```
<p>Once that is done run:</p>
```sudo apt install samba```
<p>While that is running, open a new tab and run:</p>
```mkdir ~/shared && sudo nano /etc/samba/smb.conf```
<p>Scroll to the bottom and add:</p>
```[sharedfolder]
comment = Shared folder
path = ~/shared
Valid users = <username>
guest ok = no
writable = yes
privatable = no
browsable = yes```
<p>Next run:</p>
```smbpasswd -a <username>```
<p>And set a password</p>
<p>Last run: ```sudo service smbd restart && sudo systemctl enable smbd```

<p>You can now unplug any monitors or keyboards and find a comfey place in your house to set the pi up at. Any time you need you can go to "Browse Network" in your file manager and access your samba server.</p>
</html>