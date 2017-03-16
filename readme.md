#RBPMediaCenter || Inn0

##Installation of Chromium To install Chromium you only need a few command line commands

> $ sudo apt-get update  
After this has completed installing your updates type:  

> $ sudo apt-get upgrade  
After your upgrade you can install Chromium  

> $ sudo apt-get install chromium-browser x11-xserver-utils unclutter  

##Installation of the script ###1. Setting up the RBP3B First of all you want to create a Desktop Entry on the PI that automatically starts Chromium in Kiosk mode on boot. Make sure you are running this command directly on the RBP since using a SSH connection won't let you create this file. fire up a terminal and type:

> $ sudo nano ~/.config/autostart/autoChromium.desktop  
When you've opened up the .desktop file paste the following inside the file:

> $ [Desktop Entry]
> $ Type=Application
> $ Exec=/usr/bin/chromium-browser --noerrdialogs --disable-session-crashed-bubble --disable-infobars --kiosk /home/pi/rbpmediacenter/index.html
> $ Hidden=false
> $ X-GNOME-Autostart-enabled=true
> $ Name[en_US]=AutoChromium
> $ Name=AutoChromium
> $ Comment=Start Chromium when GNOME starts

Now press Ctrl+O, Enter, Ctrl+X (this writes out and exits nano)

Once you've done this you can start adding this script to your local files

###2. Downloading the script Navigate to your /home/pi/ directory using the terminal

> $ cd /home/pi
Make a new directory called rbpmediacenter  

> $ mkdir rbpmediacenter
Navigate to your new directory  

> $ cd rbpmediacenter
Initiate Git

> $ git init
Add this repository as a remote

> $ git remote add origin https://github.com/Inn0/rbpmediacenter.git
Fill in the account credentials if prompted.

Pull this repository

> $ git pull origin master
Now check if the repository has downloaded.

###3. Making sure the monitor is always on OFcourse we don't want our monitor to just blank after 15 minutes, that's why we're disabling the screensaver

Open your lightdm configuration using the terminal

> $ sudo nano /etc/lightdm/lightdm.conf
Below [SeatDefaults] add

xserver-command=X -s 0 -dpms

Don't put and # in front of this command since this will comment it out!

Now hit Ctrl+O, Enter, Ctrl+X
