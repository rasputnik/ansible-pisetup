Raspberry Pi
=============

Sets up a Raspberry Pi (Raspbian) disk image for wifi and ssh
(intended to make headless installs easier)

Tested on 

* Mac OSX Sierra 
* this Jessie lite image : http://downloads.raspberrypi.org/raspbian_lite/images/raspbian_lite-2017-04-10/2017-04-10-raspbian-jessie-lite.zip
* Ansible 2.x
* Vagrant ( I'm using *boxcutter/centos72* but anything yum-based should be fine)

## enter your settings

All settings are in *group_vars/all*  for simplicity.
Edit with your:

* wifi SSID, passphrase etc:  the network.x dict
* image versions, etc. : the raspbian_version and img_url vars 

If it's easier, you can override each var using the '-e key=value' syntax.

## time for Ansible

The play should run with:

    ansible -i hosts prep.yml

(barring any extra '-e' options as discussed)

When it's done, youll have a .img in the *imgs/* folder, with your SSID in the filename.

### BUGS

Oh, I expect so. Log an issue / PR if you notice any.
