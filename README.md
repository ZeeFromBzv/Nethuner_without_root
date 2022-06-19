# Nethuner_without_root
Here, we have an updated version of my nethunter installation process without root (the last one could be obsolete now...)

user=kali password=kali (to log as custom user, you'll need to add the custom user and then modify the login scripts)

this is an installation process using a little script to install nethunter without root in termux using the minimal armhf or arm64 tar.xz image

So, follow the steps to install nethunter in your phone using termux...



1) open termux (obvious)

2) setup termux

```
termux-setup-storage
```

```
apt update
```

```
apt upgrade
```

```
apt install wget proot tar
```

3) download and setup the localinstall script

```
wget https://raw.githubusercontent.com/ZeeFromBzv/offline_termux_nethunter_install/main/localinstall
```

```
chmod +x localinstall
```

4) verify your aarch (the following steps will depend on this)

```
getprop ro.product.cpu.abi
```

4) download the minimal nethunter image

1-verify your aarch

```
getprop ro.product.cpu.abi
```

2-download the image depending on your aarch

*for armhf (armeabi or armeabi-v7a)

```
wget https://kali.download/nethunter-images/current/rootfs/kalifs-armhf-minimal.tar.xz
```

*for arm64 (arm64-v8a)

```
wget https://kali.download/nethunter-images/current/rootfs/kalifs-arm64-minimal.tar.xz
```

5) install the nethunter's minimal image

```
./localinstall
```

6) start nethunter

by

```
nethunter
```

or

```
nh
```

7) update and upgrade apt

```
apt update
```

```
apt upgrade
```

8) install xcfe4 and remove it's power manager plugins

by

```
sudo apt install kali-desktop-xfce
```

and

```
sudo apt-get remove xfce4-power-manager-plugins
```


9) install tightvncserver

```
sudo apt install tightvncserver
```

#start a vnc session, for the first time, it'll ask you to enter a password, this password will be your vnc password so, don't forget it and dont use a weak password

```
tightvncserver -geometry (x)x(y)
```

(x)x(y) will be replaced by the resolution of your screen eg: 2220x1080

#you can also start a vnc session with tightvncserver's default resolution

```
tightvncservser
```

# If your vnc-session display is a gray screen with x cursor, follow the steps bellow

1)stop the vnc-session

```
tightvncserver -kill :n
```

replace "n" by the session number (default: n=1)

#open the vnc startup file with nano to edit it

     nano ~/.vnc/xstartup

delete the text and replace it by :
```

#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
startxfce4 &

```



#now, you have kali nethunter and it's desktop environement installed in your termux, so... enjoy !

# to login in nethunter

use

```
nethunter
```

or

```
nh
```

# to logout, use
     
```
exit
```

# to start a vnc session in nethunter

```
tightvncserver -geometry (x)x(y)
```

or

```
tightvncserver
```
