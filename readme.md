# RSyncCStation

A simple RSync wrapper script

## Purpose

While going through college and beyond, I've had a collection of files I want
available on all of my machines. In the beginning, I used Dropbox for this
purpose, since it was well supported on Linux at the time. The issue was, I
kept running out of space.

From there, I moved to my dad's DiskStation with Synology CloudStation. That was
more than enough storage, but I couldn't tell it to perform a sync on demand,
and frequently my laptop in class wouldn't send the files I had changed before
I closed the lid and went back to my desktop. I had a bunch of duplicates from
file sync conflicts. Clearly something else was needed.

It was around this time that I found some alternatives. RSync seemed like the
simplest and easiest to use from a technical standpoint, the only catch was that
it required a lot of manually entered parameters to function properly.

Deciding that this was worth a shot anyhow, I spun up a Raspberry Pi with a
sizable SD card (and eventually an external disk) and attached it to the campus
network. I then proceeded to write a small shell script to sync my files. This
was rsynccstation, as in rsync the cloudstation directory. I eventually
shortened this to rscs.

## Script Change History

Version 1, as I used it, ran rsync twice incrementally on a single folder,
reporting errors as they came up. This worked OK, but became slow after the
first couple gigabytes of files accumulated.

This prompted me to rewrite the script in Python, with a list of target
directories that could be synced by just specifying the target you wanted to
sync. This was version 2, so to speak. Since it's a different script entirely,
it has its own repository.

Long story short, I've learned a lot more shell since I last touched this script
and decided to bring it up to feature parity with the new version. This is the
current state of rsynccstation.

## New Features

This new version of rsynccstation has one important difference over rscs2- the
targets exist outside of the script body. This means that they can be specified
without changing the source of rsynccstation itself. Before long the server
settings will probably work the same way. Otherwise, all the features of rscs2
exist here. See rsynccstation -h for more information.

## Useage

Taken from rsynccstation -h

    USEAGE: rsynccstation [options] [targets]
    
    options:
      -h            | Show this help screen
      -t            | Show list of targets
      -up           | Only upload files, not download
      -dn           | Only download files, not upload
      -s (server)   | Specify a server
      -p (port)     | Specify a port
      -u (username) | Specify a username
      
In order to use the script, a targets file must exist in your home directory.
This should be formatted like this:

    target;;;;;/absolute/path/to/directory
    
This format allows for spaces in the path name and other odd characters, since 5
semicolons in a row is an unusual thing to have in a path. This is similar to
another of my scripts, fswap, which uses the same format.

