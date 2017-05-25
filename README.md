Raspberry Pi
=============

Sets up a Raspberry Pi (Raspbian) disk image for wifi and ssh
(intended to make headless installs easier)

## setup

I'm testing on Mac OSX Sierra with a raspbian jessie lite image.

* install Ansible (2.x) on your host machine
* vagrant (we need a VM to mount the ext4 filesystem on the image)
* a raspbiam image (from https://www.raspberrypi.org/downloads/raspbian/ )

## boot the VM

This VM only exists to mount the image so we can mess with it.
I'm using *boxcutter/centos72*, anything that can use yum should
work.

  vagrant up

Verify boot with:

  ansible -i hosts -m ping all

## enter your settings

All settings are in *group_vars/all*  for simplicity.
Edit with your:

* wifi SSID
* wifi passphrase
* path to an SSH public key _(NB: Raspbian sshd doesn't trust DSA keys)_

## time for Ansible

This should set the appropriate wifi config, etc.

    ansible -i hosts prep.yml

You can verify by 'vagrant ssh' and poking around under /ras**

### BUGS

Oh, I expect so. Log an issue / PR if you notice any.
