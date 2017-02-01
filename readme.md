#RSyncCStation

A simple RSync wrapper script

##Purpose

As a university student with a lot of computers which I use for schoolwork, I started noticing a problem. I was using my dad's DiskStation in order to use the CloudStation sync service. Unfortunately, when there was a system update or the network went down, that caused problems. When he finally decided to upgrade our aging DiskStation to a newer model, I had to re-enter my credentials on every computer I used.

This prompted me to come up with my own solution. I booted a Raspberry Pi on the local network, and used SSH with RSync to keep my work in sync across my computers over the campus network. It required no external internet connection, and if something happened I wouldn't have to reenter credentials because the credentials I needed were SSH keys. Those don't change unless you change them.

This is the evolution of that original script.

##Useage

In order to use RSyncCStation, it is a good idea to create a ~/bin folder, and a ~/SyncMe folder. Everything you want synced will go in the ~/SyncMe folder. Add a line to your bashrc to add ~/bin to your path.

Copy rsynccstation into your bin folder, and rsyncexcludes.txt into your SyncMe folder, and then enter in the full path for your SyncMe folder, whatever folder you put SyncMe in, and the path to the rsyncexcludes.txt file.

Assuming you have SSH and rsync installed, a working network connection, and all the variables set right, you should now be able to sync your local directory over SSH to another computer. This will allow for quick an efficient online backup, as well as data mirroring without the need of a flash drive or online sync service.
