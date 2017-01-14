
# MusicBot Ansible

This Ansible playbook is used to install the excellent 
<a href="https://github.com/Just-Some-Bots/MusicBot">MusicBot bot for Discord</a> onto a machine
running Ubuntu 16.04.  Ubuntu 14.04 is also supported, with some issues.


## Prerequisites (if using Vagrant)

If you want to set up a VM in <a href="https://www.vagrantup.com/">Vagrant</a>, you'll need to have that installed first.
Once Vagrant is installed, run `vagrant up` to spin up a set of Ubuntu 16.04 and 14.04 VMs.


## Prerequisites 

Whether you're using Vagrant or not, here's what you'll need to take care of in order to use this Playbook:

- Make sure Ansible is installed.
- Copy `inventory.example` to `inventory` and your hosts under `[production]`
- Copy `roles/musicbot-config/files/example_options.ini` to `roles/musicbot-config/files/options.ini`
- <a href="https://github.com/Just-Some-Bots/MusicBot/wiki/Configuration">Edit options.ini accordingly</a>
- Copy `roles/musicbot-config/files/example_permissions.ini` to `roles/musicbot-config/files/permissions.ini`
- <a href="https://github.com/Just-Some-Bots/MusicBot/wiki/Permissions">Edit permissions.ini accordingly</a>


## Running Ansible

Now you're ready to run Ansible! 

First, test that you can talk to all of your hosts:

`ansible-playbook ./ping.yaml`

You will need SSH access to talk to those hosts.  If the `ping` playbook fails, you'll 
need to troubleshoot your connection, SSH keys, etc.


At this point, you should be good to run the `musicbot` playbook:

`ansible-playbook ./musicbot.yaml`

This will take a few minutes to run.  


When complete, Musicbot will be installed as a service under systemd on Ubuntu 16.04.  It will
start when the machine starts and respawn if it crashes (or the process is killed).  Running a service
is not supported under Ubuntu 14.04 at this time, because...


## Known Issues

- Ubuntu 14.04 will not work out the box, because the `requirements.txt` file in 
Python does not parse correctly under that version of Pip.  
I have <a href="https://github.com/Just-Some-Bots/MusicBot/issues/831">filed a bug</a>
with the maintainers of MusicBot and will revisit this when it is fixed.


## Authors

Just me: Douglas Muth.  I can be reached via email (doug.muth AT gmail DOT com), and
can also be found <a href="http://twitter.com/dmuth">on Twitter</a>, 
<a href="http://facebook.com/dmuth">Facebook</a>, 
and <a href="https://www.linkedin.com/in/dmuth">LinkedIn</a>


