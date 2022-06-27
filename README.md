# Ansible-UpdateUpgradeDebian

Ansible Automation to update Debian Installed packages

have a bunch of servers powered by Ubuntu and Debian Linux. 

How do I update all of them using the apt module of Ansible? How can I use Ansible for system updates and reboot the box when kernel upgrades took place?

Keeping your system up to date and applying all security patches is an essential task for sysadmins and developers. One can use the apt module of Ansible to manages apt packages for Debian/Ubuntu-based Linux distros. 

This module can either use aptitude or apt-get command on the remote server for package management. 

# What is this ?

- update_cache=yes – Run the equivalent of apt-get update command on all servers
- force_apt_get=yes – Do not use the aptitude command, instead use the apt-get command on Debian/Ubuntu boxes
- cache_valid_time=3600 – Update the apt cache if its older than the cache_valid_time. This option is set in seconds. In this examples, it is set to 3600 seconds.
- upgrade=dist – Run the equivalent of ‘apt-get upgrade’ command on all Ubuntu or Debian Linux servers. In other words, upgrade all packages to latest version.
- force_apt_get=yes – Use apt-get instead of aptitude.
- register: reboot_required_file – The ‘register’ keyword decides what variable to save a result in and we are going to use it as follows to reboot the box.
- stat: path=/var/run/reboot-required – Determine if a path (/var/run/reboot-required) exists
- get_md5=no – Algorithm to determine checksum of file. In this example, I am using md5, but you can use sha1, sha224, sha256, sha384, and sha512.

# How to use ?
first, you need to edit hosts file, that compatible with your existing infrastructure

next run this script with ansible.

ansible-playbook -i hosts debian.yml
