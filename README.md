Good news! you can have syncthing on your anbenic device!
It takes a few steps! But nothing to hard as i highlighted everything here for my future self.
In order to use Syncthing, we will need to SSH into the device and instal it (it's a linux after all!)

The RG35XXH stock OS has the packages needed for SSH. But Anbernic doesn't provide any built-in settings for users to enable it. 
There is an App you can install onto the SD card that will allow you to enable SSH. 
It can be downloaded from the authors Github page here: 
https://github.com/exdial/anbernic-apps/tree/master


I've packaged it here as well for the sake of this tutorial.
Just drag and drop the content of the zip file at the root of your SD and merge everything, find the APP in settings and select EnableSSH. 
It takes a few seconds. 

Note: **make sure your wifi is on and note the IP address!**

Then with an SSH client (like Putty or the terminal on MacOs) connect to your devices IP address using username 'root' and password 'root'. 
Once in you are going to need to copy and paste the commands from the following website (specifically the section marked Install Syncthing on Ubuntu via Official Deb Repository) 
https://www.linuxbabe.com/ubuntu/install-syncthing-ubuntu-desktop-server

I will lay it down here for the sake of it - if you are not confirtable with the terminal app don't worry and just follow these 12 steps!
**In this example my IP is 192.168.8.186** (yours will be different!) :

1. First, type:
**ssh root@192.168.8.186 **
Press enter

2. It will ask for your password which is **root**
Press enter

3. Then type:
**apt-get install curl**
Press enter

4. Then type:
**curl -s https://syncthing.net/release-key.txt | apt-key add -**
Press enter

5. Then Type:
**echo "deb https://apt.syncthing.net/ syncthing stable" | tee /etc/apt/sources.list.d/syncthing.list**
Press enter

6. Then Type:
**7. apt-get install apt-transport-https**
Press enter

8. Then Type:
**apt-get update**
Press enter

9. Then Type:
apt-get install syncthing
Press enter

10. Then Type:
systemctl enable syncthing@root.service
Press enter

11. Then Type:
systemctl start syncthing@root.service
Press enter

12. Then Type:
systemctl status syncthing@root.service
Press enter

Once you have confirmed your service is working you need to allow external access to Syncthings webUI.
By default it's locked to localhost. 
To do this, go to your device and open the file manager App.
Go to **/root/.local/state/syncthing** and edit **config.xml** and **config.xml.v0**. 
In these files search for 127.0.0.1 and replace with 0.0.0.0 and save each file.

Everything should now be configured. 
Reboot your device and in a browser go to address **http://192.168.8.186:8384**

You may want to turn the lock screen timeout off in your device settings to avoid any interuption (at least for the initial sync)

Enjoy! 
**oh wait it's not over!** Now we need to configure Retroarch to set the saves and states to their respective core folders and move everything to the **Roms** Partition to make it easier to manage
coming soon...


All Credits where due!
Special thanks:
Reddit user **StampyDriver**: https://www.reddit.com/user/StampyDriver/
Reddit user **xGearbox**: https://www.reddit.com/user/xGearbox/ 
Github user **Exdial** and his repo: https://github.com/exdial/anbernic-apps/tree/master
