# HTSP VLC Module

Trying to revive the code in order to integrate it natively in VLC, VLC for iOS/tvOS and VLCKit Applications.

After watching the FC Bayern vs. Real Madrid soccer game on 4/19/17 and experience the difference in quality 
between http (vlc) and htsp (kodi) streaming I decided to pursue this project.

Thank you, BtbN for the awesome work so far.

## Building & Installation

The following steps were tested with Ubuntu 20.04 LTS focal.

**1. Install required dependencies**

    sudo apt install cmake libvlccore-dev

**2. Build plugin**

    cmake .
    make

On successful build you should find a `libhtsp_plugin.so` in the root directory.

**3. Install the plugin (system-wide)**

    sudo install -t /usr/lib/x86_64-linux-gnu/vlc/plugins/ --group root --owner root libhtsp_plugin.so

After that, you should be able to

* spot a _Tvheadend HTSP_ entry in the Playlist view in the _Local Network_ node
* be able to configure your HTSP source in the VLC preferences view (Show settings: All) at _Input / Codec > Access modules > HTSP Protocol_



-------------------------------------
## Legacy Notes.

Compile using make and put resulting libhtsp_plugin.so somewhere VLC finds it.

Some settings are available for the service discovery. Filter advanced settings for HTS to easily find them.

URL format is htsp://{username{:password}@}server{:port}/channelId

The Service Discovery module is listed under LAN and grabs the channel list from TVH.
