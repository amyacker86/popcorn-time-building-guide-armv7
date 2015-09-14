# Popcorn time building guide for ARMv7

This is an experimental build for Odroid-U3 and Odroid-XU4!

Some videos/audios can't be decoded yet due to lack of codecs on nw.js.

### Why is Popcorn Time not available for ARMv7 linux?
The main reason why Popcorn Time is not supported officially is because it's framework called nw.js is not released officially for ARMv7 architecture. Anyway some unofficial builds are available on forums over the internet. The following tutorial explains how you can build Popcorn Time for linux ARMv7 architecture.

### Instalation guide
https://github.com/LeonardLaszlo/popcorn-time-installation-guide-armv7

### Building guide

#### Clone git repository
Execute in terminal:
  - `cd ~`
  - `sudo apt-get update`
  - `sudo apt-get install nodejs-legacy npm`
  - `mkdir workspace`
  - after cloning the repository copy `make_popcorn.sh` to workspace directory
  - `cd workspace`
  - `chmod +x make_popcorn.sh`
  - execute `./make_popcorn.sh '-b v0.3.8-5 https://git.popcorntime.io/popcorntime/desktop.git'` and accept default settings
  - `cd popcorn-app`

#### Change building script and node-webkit-builder
  - override files `~/workspace/popcorn-app/Gruntfile.js` and `~/workspace/popcorn-app/node_modules/grunt-node-webkit-builder/tasks/node_webkit_builder.js`

#### Build and run application
Execute in terminal:
  - in popcorn-app directory run: `grunt build`
  - `grunt start`
  - optionally run `grunt package` to create a Package in your build directory.

### Kodi as External player
(Obviously you need a working kodi!)

To get it to work you first need to go into the popcorn time settings and set it to always stream on the same port. 
I chose 51234

Then create a file somewhere named stream.strm with the following in it.

`http://127.0.0.1:51234/`

For the next step there are two ways.

#####One (harder but better)
Recompile popcorntime with this 
```
        'kodi': {
            type: 'kodi',
            switches: '/LOCATION/OF/stream.strm',
            subswitch: '',
            fs: '',
        },
```
added to the players section of desktop.git/src/app/lib/device/ext-player.js

If you copy external-kodi-icon.png to desktop.git/src/app/images/icons/ you'll also have the correct icon.
Rebuild!

Then kodi appears in the list of external players.

#####Two (easier)
Choose one of the supported external players that you DON'T have on your system eg mpv, mplayer, vlc, smplayer
create a file with that name in /usr/local/bin, make it executable and put this in it

```
#!/bin/bash
/usr/lib/kodi/kodi.bin /LOCATION/OF/stream.strm
```

Obviously the wrong program name shows up in the list the second way.

I find the streams much more watchable in Kodi

### VPN just for pocorntime
If you want to use a different vpn than the integrated vpn.ht but have other programs still use the standard connection there is a great guide here.

https://schnouki.net/posts/2014/12/12/openvpn-for-a-single-application-on-linux/

(systemd only I think)

### Known issues
- It doesn't work on Chromebook!
- it does not load .torrent files.

### Link to article in Odroid Magazine:

http://magazine.odroid.com/assets/201507/pdf/ODROID-Magazine-201507.pdf

