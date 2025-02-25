# PI-TIMOLO [![Mentioned in Awesome <INSERT LIST NAME>](https://awesome.re/mentioned-badge.svg)](https://github.com/thibmaek/awesome-raspberry-pi)
### Raspberry (Pi)camera, (Ti)melapse, (Mo)tion, (Lo)wlight 
For Details See [Program Features](https://github.com/pageauc/pi-timolo/wiki/Introduction#program-features) and [Wiki Instructions](https://github.com/pageauc/pi-timolo/wiki) and [YouTube Videos](https://www.youtube.com/playlist?list=PLLXJw_uJtQLa11A4qjVpn2D2T0pgfaSG0)

### PI-TIMOLO2 Update
PI-TIMOLO2 using libcamera and picamera2 on Bullseye, Bookworm or later is Now Available at https://github.com/pageauc/pi-timolo2
 
## Requirements
Requires a [***Raspberry Pi computer***](https://www.raspberrypi.org/documentation/setup/) and a 
[***RPI camera module installed***](https://www.raspberrypi.org/documentation/usage/camera/).
Make sure hardware is tested and works. Most [RPI models](https://www.raspberrypi.org/products/) will work OK. 
A quad core RPI will greatly improve performance due to threading. A recent version of 
[Raspberry Pi OS, Bullseye or earlier](https://www.raspberrypi.org/downloads/raspbian/) is Recommended.
 
## Quick Install or Upgrade
**IMPORTANT** - It is suggested you do a Raspbian ***sudo apt-get update*** and ***sudo apt-get upgrade***
before curl install, since it is **No longer** performed by the pi-timolo-install.sh script

***Step 1*** With mouse left button highlight curl command in code box below. Right click mouse in **highlighted** area and Copy.     
***Step 2*** On RPI putty SSH or terminal session right click, select paste then Enter to download and run script.     

    curl -L https://raw.github.com/pageauc/pi-timolo/master/source/pi-timolo-install.sh | bash

The command above will download and Run the GitHub ***pi-timolo-install.sh*** script. 
An upgrade will not overwrite configuration files.   

* ***NOTICE*** gdrive is no longer installed with pi-timolo-install.sh, I have been testing
rclone and it is Now the Default. Some ***rclone-*** samples are included. Make a copy of one, rename and edit for
your own needs.  See [Wiki - How to Setup Rclone](https://github.com/pageauc/pi-timolo/wiki/How-to-Setup-rclone).
Note: If a ***/usr/local/bin/gdrive*** File Exists, It Will Remain. Older files are still available on this GitHub Repo.   

## Test Install
To Test Run default config.py - motion track(HD image) plus timelapse(5 min interval). 
 
    cd ~/pi-timolo
    ./pi-timolo.py

### For More Details see [Basic Trouble Shooting](https://github.com/pageauc/pi-timolo/wiki/Basic-Trouble-Shooting) or [pi-timolo Wiki](https://github.com/pageauc/pi-timolo/wiki)

## Description
PI-TIMOLO is primarily designed for ***headless operation*** and includes rclone that
can securely synchronize specified media folders and files with a users remote storage service of choice. This works well for remote security and monitoring
cameras. Camera config.py and conf settings can be easily administered remotely from a designated sync directory using ***watch-app.sh***
script using a crontab entry to periodically check for updates between the pi-timolo camera and a users remote storage rclone service name. 

pi-timolo is python 2/3 compatible and can take timelapse and/or motion tracking images/videos, separately or together. Will take
long exposure Night (lowlight) images for Time Lapse and/or Motion. Has relatively smooth twilight transitions based on a threshold light
setting, so a real time clock is not required. Customization settings are saved in a ***config.py*** and conf files and optional special
purpose plugin config files. Optional plugin feature allows overlaying config.py settings with custom settings for specific tasks.  

Includes ***makevideo.sh*** to create timelapse or motion lapse videos from images, ***convid.sh*** to convert/combine 
h264 to mp4 format, a simple minumum or no setup web server to view images or videos and ***menubox.sh*** 
to admin settings and stop start pi-timolo and webserver as background tasks. 
       
For more Details see [Github Wiki](https://github.com/pageauc/pi-timolo/wiki)   

## Minimal Upgrade
If you are just interested in a minimal upgrade (must have pi-timolo previously installed)
from a logged in ssh or terminal session execute the following commands.  

    cd ~/pi-timolo
    sudo apt-get install python-opencv
    cp config.py config.py.old
    cp pi-timolo.py pi-timolo.py.old
    wget -O config.py https://raw.github.com/pageauc/pi-timolo/master/source/config.py
    wget -O pi-timolo.py https://raw.github.com/pageauc/pi-timolo/master/source/pi-timolo.py    

To implement webserver3.py (Buster or Later) perform the following

    cp webserver.py webserver2.py
    cp webserver3.py webserver.py

    
Edit config.py to transfer any customized settings from config.py.old  
    
## Manual Install or Upgrade  
From logged in RPI SSH session or console terminal perform the following. You can review
the pi-timolo-install.sh script code before executing.

    cd ~
    wget https://raw.github.com/pageauc/pi-timolo/master/source/pi-timolo-install.sh
    more pi-timolo-install.sh    # Review code if required
    chmod +x pi-timolo-install.sh
    ./pi-timolo-install.sh
    
## Menubox
pi-timolo has a whiptail administration menu system. The menu's allow
start/stop of pi-timolo.py and/or webserver.py as background tasks, as well as
editing configuration files, making timelapse videos from jpg images, converting or joining mp4 files Etc.    

To run menubox.sh from ssh console or terminal session execute commands below.

    cd ~/pi-timolo
    ./menubox.sh

![menubox main menu](menubox.png)
 
## Webserver
I have also written a standalone LAN based webserver.py to allow easy access to pi-timolo image and video files
on the Raspberry from another LAN computer web browser.  There is no setup required but the display
settings can be customized via variables in the config.py file or via menubox admin menuing.     
***NOTE:*** webserver.py is normally run in background using menubox.sh, webserver.sh or from /etc/rc.local     
To Test Run from ssh console or terminal session. 
    
    cd ~/pi-timolo
    ./webserver.py

![webserver browser screen shot](webserver.jpg)

## shutdown.py
This will safely halt the raspberry pi when a momentary switch is held for a specified number of seconds
for details see wiki [How to Use shutdown.py](https://github.com/pageauc/pi-timolo/wiki/How-to-use-shutdown.py)

## Reference Links 
[Detailed pi-timolo Wiki](https://github.com/pageauc/pi-timolo/wiki)  
[my pi-timolo and other YouTube Videos playlist](https://www.youtube.com/playlist?list=PLLXJw_uJtQLa11A4qjVpn2D2T0pgfaSG0)    
[MagPi Object Recognition using pi-timolo](https://magpi.raspberrypi.org/articles/wildlife-camera-object-recognition)    
[makezine night vision project using pi-timolo](https://makezine.com/2016/05/26/spy-on-garden-critters-with-raspberry-pi-powered-night-vision/)    
[hackster facial recognition using pi-timolo](https://www.hackster.io/gr1m/raspberry-pi-facial-recognition-16e34e)    
[Neverending project timelapse using pi-timolo](https://www.theneverendingprojectslist.com/raspberrypiprojects/timelapse/)       
[hedgehog camera using pi-timolo](http://www.sconemad.com/blog/hedgeycam/) and [step by step](https://oraclefrontovik.com/2016/08/28/a-step-by-step-guide-to-building-a-raspberry-pi-hedgehog-camera/)    
[Museum Insect activity monitoring using pi-timolo](https://www.vam.ac.uk/blog/caring-for-our-collections/making-a-simple-insect-activity-monitor-using-a-raspberry-pi)    
[Brett Beeson timelapse cloud project using pi-timolo](https://brettbeeson.com.au/timelapse-cloud/)     
[Bird and Squirrel Detector](https://magpi.raspberrypi.org/articles/ml-based-bird-and-squirrel-detector)  
	
Good Luck
Claude Pageau 
