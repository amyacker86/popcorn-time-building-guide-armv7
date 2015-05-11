# Popcorn time building tutorial for ARMv7 (Odroid-U3|Ubuntu 14.04.2)

This is an experimental build for Odroid-U3. I never tried on other devices, so I would really appreciate feedback!

Some videos/audios can't be decoded yet due to lack of codecs on nwjs. 

### Instalation guide
https://git.popcorntime.io/laslaul/popcorn-time-installation-guide-armv7

### Building guide
For building Popcorn time you will need to install a webserver first. The webserver is needed for delivery of nwjs during the installation. Nginx or apache2 servers are recommended.

#####Setup server:
  - download nwjs-v0.12.0-linux-arm.tar.gz
  - publish it on the following path: http://localhost/nw/v0.12.0/nwjs-v0.12.0-linux-arm.tar.gz

#####Clone git repository
Execute in terminal:
  - cd ~
  - git clone git@git.popcorntime.io:popcorntime/desktop.git -b v0.3.7.2 desktop
  - cd desktop
  - sudo npm install -g grunt-cli bower
  - sudo npm install

#####Change building script and node-webkit-builder
  - download files: Gruntfile.js and node_webkit_builder.js
  - override files ~/desktop/Gruntfile.js and ~/desktop/node_modules/grunt-node-webkit-builder/tasks/node_webkit_builder.js with downloaded files

#####Build and run application
Execute in terminal:
  - grunt build
  - grunt start