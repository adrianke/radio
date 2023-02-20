A cloud config file tested on DigitalOcean to set up an icecast2 streaming server.

# Features
 * Streams music from `/home/radio/music` 24/7 in the `/stream` mount. 
 * When you connect to the source `/talk`, music is stopped and the `/stream` mount is now seamlessly mirroring `/talk`.
 * Automatic OpenVPN setup so that you'll not have to send passwords in the clear.
 * Generates a strong password for the icecast installation.

# Installation
 * Create a new DigitalOcean dropplet with Ubuntu 14.04.
 * Select the `User Data` option and paste in the contents of `cloud-config.yaml`
  * You should update the script as needed. Note the icecast2 settings.
  * **ALWAYS CHANGE THE SSH KEY IN `cloud-config.yaml`**
 * Add optional SSH keys on the DigitalOcean website
 * Immediately connect to the server over ssh
  * Username: radio
  * Use your own SSH key
* After a while, you'll see a music directory in the home folder
  * Upload some mp3's
  * Run `~/new_music.sh`
* After three to five minutes, you'll get a message in the terminal saying `Ready for reboot`.
  * Reboot if the music upload is complete, and you've run `~/new_music.sh`

# Broadcasting
If you're using Windows or OS X, simply download [butt](http://danielnoethen.de/).

## Server configuration in butt
If you're using the provided VPN setup:
  * Address: 10.8.0.1
  * Port: 8000
  * Type: Icecast
  * Mountpoint: talk
  * User: source
  * Password: Located in /home/radio/icecast_password.txt

# License
MIT License
