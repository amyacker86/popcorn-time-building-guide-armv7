# Popcorn time building tutorial for ARMv7 (Ubuntu 14.04.2)

This is an experimental build for Odroid-U3. I only tried it on Odroid U3 and XU4!

Some videos/audios can't be decoded yet due to lack of codecs on nwjs.

### Why is Popcorn Time not available for ARMv7 linux?
The main reason why Popcorn Time is not supported officially is because it's framework called nw.js is not released officially for ARMv7 architecture. Anyway some unofficial builds are available on forums over the internet. The following tutorial explains how you can build Popcorn Time for linux ARMv7 architecture.

### Instalation guide
https://github.com/LeonardLaszlo/popcorn-time-installation-guide-armv7

### Building guide

#### Clone git repository
Execute in terminal:
  - `cd ~`
  - `sudo apt-get update`
  - `sudo apt-get install nodejs-legacy`
  - `sudo apt-get install npm`
  - `mkdir workspace`
  - download and copy `make_popcorn.sh` to workspace directory
  - `cd workspace`
  - execute `./make_popcorn.sh '-b v0.3.7.2 https://git.popcorntime.io/popcorntime/desktop.git'` and accept default settings
  - `cd popcorn-app`

#### Change building script and node-webkit-builder
  - download files: `Gruntfile.js` and `node_webkit_builder.js`
  - override files `~/workspace/popcorn-app/Gruntfile.js` and `~/workspace/popcorn-app/node_modules/grunt-node-webkit-builder/tasks/node_webkit_builder.js` with downloaded files

#### Build and run application
Execute in terminal:
  - in popcorn-app directory run: `grunt build --force`
  - `grunt start`
