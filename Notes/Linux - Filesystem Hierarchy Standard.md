---
tags:
  - Linux
---
[Red Hat Reference](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/s1-filesystem-fhs)
[Unix Cheat Sheet](https://github.com/ttaylordev/cheat-sheets-etc/blob/master/filesystem-hierarchy.md)
[Ubuntu Cheat Sheet](https://cheatography.com/adam-hendry/cheat-sheets/linux-fhs/)
[In Depth Reference](https://www.pathname.com/fhs/pub/fhs-2.3.html)

The [Filesystem Hierarchy Standard (FHS)](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) is a common used standard for organizing the Unix-like file systems. While not required, it should be enforced.

TLDR - The standard provides a framework for how the file system directory should be structured.

From **Unix Cheat Sheet** linked above:
## Unix Filesystem Hierarchy Standard

```
/              Root dir
/bin           Binaries
/dev           Devices
/etc           Host-specific system-wide config
/etc/opt       Add-on config
/etc/X11       X window system config
/home          User home dir
/lib           Libraries for binaries
/media         Removable media
/mnt           Temporary fs's
/opt           Optional apps
/proc          Virtual fs for process & kernel
/root          Home dir of root user
/sbin          Essential system binaries
/srv           Site-specific data served by system
/tmp           Temporary files
/usr           Secondary hierarcy for read-only user data
/usr/bin       Non-essential binaries for all users
/usr/include   Standard include files
/usr/local     Tertiary hierarchy for local data
/usr/sbin      Non-essential system binaries (daemons)
/share         Architecture independent shared data
/src           Source code
/var           Variable files
/var/cache     Application cache data
/var/lib       State information. Used by db's and the like.
/var/lock      Lock files. Which resources are used.
/var/log       Log files
/var/mail      Mailboxes
/var/opt       Variable data from `/opt/`
/var/run       Information about running system since boot
/var/spool     Tasks waiting to be processed
/var/tmp       Temp files preserved between boots
```

## Node Module Filesystem Hierarchy

```
bin              -> executable
docs             -> documentation
lib              -> source files
test             -> tests
```

## Project Filesystem Hierarchy

```
bin              -> executable
docs             -> documentation
lib              -> source files
pkg              -> packages (local modules)
sh               -> shell scripts
test             -> integration tests
```

## Personal filesystem hierarchy

Or, how to structure your personal documents well. If you want. It's a way that works.

```
etc/              other
  pwd/            `pass(1)` password files
lib/              resources that can be consumed
log/              scanned materials, sorted by date (2011, 2012, etc.)
media/            media
  cam/            img from camera
  read/           books, articles and the like
  screen/         screenshots
  tmp/            images that don't belong in any of the above
  vid/            movies, gifs
  wall/           wallpapers
  write/          stories, notes, posts
tmp/              temporary files
src/              source code
usr/              personal files, sorted by topics
  accounts/       account info & restoration files
  img/            avatar pictures
```

