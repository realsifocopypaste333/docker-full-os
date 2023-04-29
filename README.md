SIMPLE DOCKER FULL OS

=========

i create create very simple docker full os buat it needs very complex steps


1. install gnu linux for host os
ex= debian stable

============

2. install docker in host os

sudo apt install docker* docker-compose*

============


3. pull docker gnu linux os for docker linux os

ex= kali linux rolling 

sudo docker pull kalilinux/kali-rolling

==============


3. make audio fix (pulse audio fix) before start the dcoker image

a. create file named pulseaudio.socket in /home/user/pulse

b. in that file write this text and save

default-server = unix://home/user/pulse/pulseaudio.socket
# Prevent a server running in the container
autospawn = no
daemon-binary = /bin/true
# Prevent the use of shared memory
enable-shm = false
Share socket and config file with docker and set environment variables PULSE_SERVER and PULSE_COOKIE. Container user must be same as on host:


c. run this comman in terminal 

pactl load-module module-native-protocol-unix socket=/home/realsifo/Downloads/pulse/pulseaudio.socket


=============


4. run the docker image with 

a. check the docker image that we pull

sudo docker images



b. run it with this commmand


docker run  -ti   --device=/dev/dri:/dev/dri       --privileged   --cap-add=ALL   --device /dev/snd   --volume /dev:/dev   -v /dev:/dev   --group-add audio   -v /var/run/docker.sock:/host/var/run/doc   -v /:/media/prime   --env PULSE_SERVER=unix:/home/user/pulse/pulseaudio.socket   --env PULSE_COOKIE=/home/user/pulse/pulseaudio.cookie   --volume /home/user/pulse/pulseaudio.socket:/home/user/pulse/pulseaudio.socket  --volume /home/user/pulse/pulseaudio.client.conf  --publish=0.0.0.0:3351:3351       --publish=0.0.0.0:51:51   --group-add video   --volume="/tmp/.X11-unix:/tmp/.X11-unix"  --env="DISPLAY" -e XAUTHORITY=/root/.Xauthority  --name dockerfullos-001   imageid



c. and the kali linux docker bash terminal with appears


================

5. install apps that we need 

a. apt update 

b. apt full-upgrade -y

c. apt install nano pulseaudio* neofetch vlc* smplayer* wget uget    cairo-dock*   alsa-utils*  network-manager   net-tools*   cairo-dock-plug-ins*  dbus dbus-x11  thunar* chromium* rofi* terminator*  sudo kate* kwrite*   geany*  geany-plugin-addons*    aptitude*     qt5-style-kvantum-themes qt5-style-kvantum-l10n  qt5-style-kvantum   libreoffice   krita* gimp* kdenlive* handbrake* yt-dlp*   isomaster* k3b*  apt-utils* git htop* compiz* compiz-boxmenu*  compiz-plugins*  compizconfig-settings-manager*  emerald* emerald-themes* fusion-icon* simple-ccsm*   usbutils*   lxqt*  bleachbit* nmap* xrpd* openssh-server openssh-client -y


------------------

for intel gpu 

a. dpkg --add-architecture i386 && sudo apt update


b. apt  install libvulkan1 libvulkan1:i386 mesa-vulkan-drivers mesa-vulkan-drivers:i386 vulkan-tools*   -y


c. apt install wine64 lutris*


---------------------

===============


6. add root password

passwd




===================

7. add user

adduser username


usermod -aG sudo username


========================

8. to save the container into image 

a. open new terminal 


b. check the container id 

sudo docker ps -a

c. save the container into docker image 


sudo docker container commit --pause=false  id-container   nama-image:label

example 

sudo docker container commit --pause=false  c092aa5afec0  kali-linux:kali-linux-docker-full-os


================

it is very complex steps and needs long time :)

so please make official full os for us .thanks :)


===============

simple use case for docker full os
============================

A. docker full os can make better gaming expirence

because  docker full os kali linux rolling (debian testing) have newer mesa driver than debian stable , so it make game in docker full os better 


the step are

1. run the  ali-linux-docker-full-os


sudo docker run  -ti   --device=/dev/dri:/dev/dri       --privileged   --cap-add=ALL   --device /dev/snd   --volume /dev:/dev   -v /dev:/dev   --group-add audio   -v /var/run/docker.sock:/host/var/run/doc   -v /:/media/prime   --env PULSE_SERVER=unix:/home/user/pulse/pulseaudio.socket   --env PULSE_COOKIE=/home/user/pulse/pulseaudio.cookie   --volume /home/user/pulse/pulseaudio.socket:/home/user/pulse/pulseaudio.socket  --volume /home/user/pulse/pulseaudio.client.conf  --publish=0.0.0.0:3351:3351       --publish=0.0.0.0:51:51   --group-add video   --volume="/tmp/.X11-unix:/tmp/.X11-unix"  --env="DISPLAY" -e XAUTHORITY=/root/.Xauthority  --name dockerfullos-001   imageid



2. tipe lutris


3. lutris will run in host os 


4. setting the lutris and play the game :)






==================


c. docker full os can sutitude the vm

because docker full os is a native os like chroot so it has a native performanc like the host 


how to do it ?

it very imple 


method A

acces all docker full os apps fro host 

1. run the immage 

sudo docker run  -ti   --device=/dev/dri:/dev/dri       --privileged   --cap-add=ALL   --device /dev/snd   --volume /dev:/dev   -v /dev:/dev   --group-add audio   -v /var/run/docker.sock:/host/var/run/doc   -v /:/media/prime   --env PULSE_SERVER=unix:/home/user/pulse/pulseaudio.socket   --env PULSE_COOKIE=/home/user/pulse/pulseaudio.cookie   --volume /home/user/pulse/pulseaudio.socket:/home/user/pulse/pulseaudio.socket  --volume /home/user/pulse/pulseaudio.client.conf  --publish=0.0.0.0:3351:3351       --publish=0.0.0.0:51:51   --group-add video   --volume="/tmp/.X11-unix:/tmp/.X11-unix"  --env="DISPLAY" -e XAUTHORITY=/root/.Xauthority  --name dockerfullos-001   imageid


2. we can use rofi or cairo-dock to lunch the docker full os apps

***********
using rofi

1. type rofi --show run 

2. select the apps 

ex =vlc

3. vlc docker full os apps  with run directly the host os 

4. play some move / videos / audio with that vlc :)

*******************

using cairo-dock

1. type cairo-dock

2. cairo-dcok will launch to host os

3. launch docker full os apps fro cairo-dock menu :)

*********************************

=========

method B

using xrpd

we can access full gui of docker full os via xrdp 


how to do it 

1. run the docker image 


sudo docker run  -ti   --device=/dev/dri:/dev/dri       --privileged   --cap-add=ALL   --device /dev/snd   --volume /dev:/dev   -v /dev:/dev   --group-add audio   -v /var/run/docker.sock:/host/var/run/doc   -v /:/media/prime   --env PULSE_SERVER=unix:/home/user/pulse/pulseaudio.socket   --env PULSE_COOKIE=/home/user/pulse/pulseaudio.cookie   --volume /home/user/pulse/pulseaudio.socket:/home/user/pulse/pulseaudio.socket  --volume /home/user/pulse/pulseaudio.client.conf  --publish=0.0.0.0:3351:3351       --publish=0.0.0.0:51:51   --group-add video   --volume="/tmp/.X11-unix:/tmp/.X11-unix"  --env="DISPLAY" -e XAUTHORITY=/root/.Xauthority  --name dockerfullos-001   imageid


2. edit the xrpd config in that docker full os

nano /etc/xrdp/xrdp.ini

change to port to the open port 3351

it will make the xrdp ip 127.0.0.1:3351

3. restart xrdp server 

service xrdp restart


4. install kdrc (rdp client) in host os

5. conect the xrdp using kdrc with the xrpd ip


********
krdc setting

a. screen setting = 1024x800

b. audio = in this omputer --- pulse audio

c 32bit color :)

**************


6. enjoy :) we can use docker full os with full gui in krdc :)


=====================

C. docker full os can use for simple cloud computing / cloud gaming 


how to do it ?

it very easy

1. run the docker image 

we can run multiple docker full image in single server

a. terminal 1


sudo docker run  -ti   --device=/dev/dri:/dev/dri       --privileged   --cap-add=ALL   --device /dev/snd   --volume /dev:/dev   -v /dev:/dev   --group-add audio   -v /var/run/docker.sock:/host/var/run/doc   -v /:/media/prime   --env PULSE_SERVER=unix:/home/user/pulse/pulseaudio.socket   --env PULSE_COOKIE=/home/user/pulse/pulseaudio.cookie   --volume /home/user/pulse/pulseaudio.socket:/home/user/pulse/pulseaudio.socket  --volume /home/user/pulse/pulseaudio.client.conf  --publish=0.0.0.0:3351:3351       --publish=0.0.0.0:51:51   --group-add video   --volume="/tmp/.X11-unix:/tmp/.X11-unix"  --env="DISPLAY" -e XAUTHORITY=/root/.Xauthority  --name dockerfullos-001   imageid


change xrdp and ssh port accordingly :)

********

how to change ssh port 

1. nano /etc/ssh/sshd_config

2. change the port to 51

************

-------------------


b. terminal 2


sudo docker run  -ti   --device=/dev/dri:/dev/dri       --privileged   --cap-add=ALL   --device /dev/snd   --volume /dev:/dev   -v /dev:/dev   --group-add audio   -v /var/run/docker.sock:/host/var/run/doc   -v /:/media/prime   --env PULSE_SERVER=unix:/home/user/pulse/pulseaudio.socket   --env PULSE_COOKIE=/home/user/pulse/pulseaudio.cookie   --volume /home/user/pulse/pulseaudio.socket:/home/user/pulse/pulseaudio.socket  --volume /home/user/pulse/pulseaudio.client.conf  --publish=0.0.0.0:3352:3352       --publish=0.0.0.0:52:52   --group-add video   --volume="/tmp/.X11-unix:/tmp/.X11-unix"  --env="DISPLAY" -e XAUTHORITY=/root/.Xauthority  --name dockerfullos-002   imageid


change xrdp and ssh port accordingly :)

-------------------

c. terminal 3


sudo docker run  -ti   --device=/dev/dri:/dev/dri       --privileged   --cap-add=ALL   --device /dev/snd   --volume /dev:/dev   -v /dev:/dev   --group-add audio   -v /var/run/docker.sock:/host/var/run/doc   -v /:/media/prime   --env PULSE_SERVER=unix:/home/user/pulse/pulseaudio.socket   --env PULSE_COOKIE=/home/user/pulse/pulseaudio.cookie   --volume /home/user/pulse/pulseaudio.socket:/home/user/pulse/pulseaudio.socket  --volume /home/user/pulse/pulseaudio.client.conf  --publish=0.0.0.0:3353:3353       --publish=0.0.0.0:53:53   --group-add video   --volume="/tmp/.X11-unix:/tmp/.X11-unix"  --env="DISPLAY" -e XAUTHORITY=/root/.Xauthority  --name dockerfullos-002   imageid


change xrdp and ssh port accordingly :)

-------------------


each docker full os will run natively and independenly



-------------

3. we can acces it from the ost os with ip localhost:xrdp post (127.0.0.1:3351) with kdrc client :)


4. we can also accest in from diffierent gnu linux computer in the same lan / wifi local network with the ip from host os that give by the router explampe 192.168.43.1  etc and xrdp port :) with kdrc


exaample xrdp 

dockerfullos-001 = 192.168.43.1:3351


dockerfullos-002 = 192.168.43.1:3352


dockerfullos-003 = 192.168.43.1:3353



example of ssh 

dockerfullos-001 = 192.168.43.1:51


dockerfullos-002 = 192.168.43.1:52


dockerfullos-003 = 192.168.43.1:53



===========

5. enjoy the docker full os for cloud computing :)

all the apps fro docker full os will run natively in kdrc in the client compuputer :)



6. for gaming 

we can use emulator (ps1, ps2, psp, mame etc) , steam , lutris, wine etc :)





************

wine /lutris fix


wine / lutris sometime will error in docker full os 

how to fix it 

1. open lutris 

2. setting the game with lutris

3. in the game menu , select wine regristry

4. edit the  hcu  -------> wine

5. add key  X11 DRIVER

6. add string "UseXVidMode"="N"

7. add string UseXVidMode  -------> edit the VALUE to N

8. close wine 



==================

thanks :)

===================
This text use creative commone license

==========================
