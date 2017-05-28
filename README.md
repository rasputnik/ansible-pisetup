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
Enter your:

* wifi SSID, passphrase etc:  the *network.x* dict
* _(optionally)_ image versions, etc. : the *raspbian_version* and *img_url* vars 

## time for Ansible

The play should run with:

    ansible -i hosts prep.yml

If you want to setup the 'pi' user for RSA (passwordless) logins, run:
 
    ansible -i hosts prep.yml -e pubkey=/full/path/to/your/publickey

where the file */full/path/to/your/publickey* has an RSA public key
_(DSA keys are not supported in recent Jessie versions)_.

When it's done, youll have a .img in the *imgs/* folder, with your SSID in the filename.

dd that to an SD card and boot it, you should have a working pi.

### BUGS

Oh, I expect so. Log an issue / PR if you notice any.
