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

  vagrant up

Verify boot with:

  ansible -i vagrant -m ping all

## time for Ansible

You can verify connectivity by running:

    ansible -i hosts all -m ping

and you should see lots of lovely facts about your pi flowing back.

Run the main play with:

    ansible-playbook -i hosts site.yml

## vars

* role-specific vars live in $rolename/defaults/main.yml
* 'globals' _(e.g. ansible_ssh_user)_ live in 'hosts'

### BUGS

Oh, I expect so. Log an issue / PR if you notice any.
