# SSH and Syncthing on the RG35xx H (Stock Mod OS)

Good news! You can have Syncthing on your Anbernic device!
It takes a few steps, but nothing too hard, as I highlighted everything here for my future self.
In order to use Syncthing, we will need to SSH into the device and install it (it's a Linux after all!).

## Enable SSH

The RG35xx H stock OS has the packages needed for SSH, but Anbernic doesn't provide any built-in settings for users to enable it.
There is an app you can install onto the SD card that will allow you to enable SSH.

It can be downloaded from the author's GitHub page here:
https://github.com/exdial/anbernic-apps/tree/master

I've packaged it here as well for the sake of this tutorial.

**Note: if you have the Stock Mod OS, you already have an SSH app so you can skip this step. It's in Chinese, but we will just copy and paste stuff so it's not an issue!**

Just drag and drop the content of the zip file at the root of your SD card and merge everything, then find the app in Settings and select EnableSSH.
It takes a few seconds.

Note: **make sure your wifi is on and note the IP address!**

## Install Syncthing

Then with an SSH client (like PuTTY, or the terminal on macOS) connect to your device's IP address using username **root** and password **root**.
Once in, you are going to copy and paste the commands from the following website (specifically the section marked "Install Syncthing on Ubuntu via Official Deb Repository"):
https://www.linuxbabe.com/ubuntu/install-syncthing-ubuntu-desktop-server

I will lay it down here for the sake of it. If you are not comfortable with the terminal, don't worry and just follow these 11 steps.

**In this example my IP is 192.168.8.186** (yours will be different!):

1. First, type:

   > **ssh root@192.168.8.186**

   Press enter.

2. It will ask for your password, which is **root**.

   Press enter.

3. Then type:

   > **apt-get install curl**

   Press enter. You will be prompted to type "Y", just type **Y** and press enter.

4. Then type:

   > **curl -s https://syncthing.net/release-key.txt | apt-key add -**

   Press enter.

5. Then type:

   > **echo "deb https://apt.syncthing.net/ syncthing stable" | tee /etc/apt/sources.list.d/syncthing.list**

   Press enter.

6. Then type:

   > **apt-get install apt-transport-https**

   Press enter.

7. Then type:

   > **apt-get update**

   Press enter.

8. Then type:

   > **apt-get install syncthing**

   Press enter.

9. Then type:

   > **systemctl enable syncthing@root.service**

   Press enter.

10. Then type:

    > **systemctl start syncthing@root.service**

    Press enter.

11. Then type:

    > **systemctl status syncthing@root.service**

    Press enter.

## Allow external access to the web UI

Once you have confirmed your service is working, you need to allow external access to Syncthing's web UI.
By default it's locked to localhost.

To do this, go to your device and open the file manager app.
Go to **/root/.local/state/syncthing** and edit **config.xml** and **config.xml.v0**.
In these files search for 127.0.0.1, replace with 0.0.0.0, and save each file.

Everything should now be configured.
Reboot your device and in a browser go to **http://192.168.8.186:8384**

You may want to turn the lock screen timeout off in your device settings to avoid any interruption (at least for the initial sync).

Enjoy!

## Coming soon

Oh wait, it's not over!
Now we need to configure RetroArch to set the saves and states to their respective core folders, and move everything to the **Roms** partition to make it easier to manage.

This part is coming soon...

## Credits

All credits where due! Special thanks:

- Reddit user **StampyDriver**: https://www.reddit.com/user/StampyDriver/
- Reddit user **xGearbox**: https://www.reddit.com/user/xGearbox/
- GitHub user **Exdial** and his repo: https://github.com/exdial/anbernic-apps/tree/master

## Support

If this saved you time, you can support my work:

[<img src="https://storage.ko-fi.com/cdn/kofi2.png?v=6" alt="Buy Me a Coffee at ko-fi.com" height="36">](https://ko-fi.com/H2H81I6YY1)
