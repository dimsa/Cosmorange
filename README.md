# Cosmorange
Analog of Astroberry Server using Orange Pi and open-source technologies


#0) For this you need Orange Pi 4 LTS with at least 16 gb of MMC.
#0.1) Orange PI 4 LTS is very demanding to Power Supply. The best UX I goo using Xiaomi Powerbank with Quick Charge.

#1) Make MicroSD Card with last Orange Pi Ubuntu Desktop or Armbian Desktop. It works both, but I used original Orange Pi OS

#2) Insert to Orange PI, setup languages and etc. I use for login root and password orangepi. You can create your account

#2*) You can also install all what you want. When you will be on the paragraph 4, all your work will be flashed on emmc

#3) Now it's better to use SSH. Install Putty for Windows. Find the IP of OrangePI (I used Router Page for this) and make connection to it.

#4) Flash emmc. Go to Linux Terminal and then do the following command (Here is video https://www.youtube.com/watch?v=t8IkQBq34WA)
sudo /usr/sbin/nand-sata-install
#Select Boot from Emmc - sytem on emmc
#Then - yes
#Then select ext4 filesystem
#Switch device off.

#6) Switch device On and use Putty to connect through SSH

#7) Update repository. Run in terminal following commands. Press Y on every question
sudo apt-get update
sudo apt-get upgrade

#8) Add Linux Repository for Indi. Press enter on the confirmation https://www.indilib.org/download.html
sudo apt-add-repository ppa:mutlaqja/ppa
sudo apt-get update

#9) Install full indi and kstars with ekos. Press Y on every question
sudo apt-get install indi-full gsc kstars-bleeding 

#10) Install PHD2 To install PHD2 you can use the following command line or use the equivalent function in the Ubuntu GUI installer:
sudo add-apt-repository ppa:pch/phd2
sudo apt-get update
sudo apt-get install phd2 phdlogview

#11) #Installing ser-player
sudo apt-get install ser-player

#12) Install Astrometry.net solver

sudo apt-get install astrometry.net

#13) Download offline indexes for astrometry
cd /home
mkdir astrometry 
cd astrometry
mkdir data
cd data
wget http://data.astrometry.net/4200/wget.sh
sudo chmod +x wget.sh
./wget.sh

#14) Setup hotspot. You should be connected using Ethernet Cabel. Otherwise it will not work.
orangepi-config

#15) Install VNC Server
sudo apt-get install tightvncserver

#16) Dowload Windows client for vnc - TightVncViewer https://www.tightvnc.com/download.php also there are android analogs.

#17) Run VNC server with parameter of you screen, or other. On the first run you will be asked to create the password. 
vncserver -depth 24 -geometry 1920x1080

#18)  To make Astrometry work fine you need to set up date after the logging into the Orange Pi. UI of Ubuntu doesn't provide any functionality to make this using UI, so try the command 
sudo date -s “YYYY-MM-DD HH:MM:SS” 

#19) Open vnc connection from viewer on the client device (Windows in my case). Use the following address <IP of Orange Pi>:5901
192.168.31.42:5901

#20) Use KStars, then open Ekos, check the connection to devices with Indi

#21) To make PHD2 work correct you need first to run Ekos with the PHD2 for Guiding. Otherwise Indi drivers will not be loaded.

#22) Check the lessons of how to use Ekos 
