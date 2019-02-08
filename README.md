# hots
A short wiki for running HoTS on Arch


#### Step 1 
Install Dependencies. 

##### Note: I used Lutris to initialize the Wine prefix, but didn't use it for much else as it failed to launch Battle.net with a "file not found". Download here instead: https://www.battle.net/download/getInstallerForGame?os=win&version=LIVE&gameProgram=BATTLENET_APP

##### Install `yay` or replace yay commands with your preferred AUR client.

##### Note: Tested with Wine Staging v 4.1: `wine-4.1 (Staging)`
##### Note: I also blew away `~/.local/share/lutris`, `~/.cache/lutris`, `~/.config/lutris`, `~/Games/heroes*` before starting. 

```
$ yay -S lutris wine-staging nvidia nvidia-utils lib32-nvidia-utils nvidia-settings lib32-lcms2 lib32-giflib lib32-libpng lib32-gnutls lib32-gst-plugins-base lib32-gst-plugins-good lib32-libxml2 lib32-mpg123 giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libxinerama ncurses lib32-ncurses opencl-icd-loader lib32-opencl-icd-loader libxslt lib32-libxslt libva lib32-libva gtk3 lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader cups samba
```

##### There may be a couple of duplicates in the above command and only some of the libs come from AUR. This is just a quick brain dump.

##### Step 2 
Install DXVK64 and run setup

```
$ yay -S dxvk-git
$ WINEPREFIX=${HOME}/Games/heroes-of-the-storm setup_dxvk64
```

##### Step 3 
Install Battle.net and then HoTS.

```
$ cd ~/Downloads
$ curl -L "https://www.battle.net/download/getInstallerForGame?os=win&version=LIVE&gameProgram=BATTLENET_APP" --output Battle.net-Setup.exe
$ export WINEARCH=win64
$ export WINEPREFIX=${HOME}/Games/heroes-of-the-storm
$ wine ~/Downloads/Battle.net-Setup.exe
```

##### Note: If above download doesn't work, use a browser! :-D

#### Step 4
Login to Battle.net, install HoTS etc.

#### Step 5 
Launch with this handy function:

```
hots(){
    export WINEARCH=win64
    export WINEPREFIX=${HOME}/Games/heroes-of-the-storm
    wine ${HOME}/Games/heroes-of-the-storm/drive_c/Program\ Files\ \(x86\)/Battle.net/Battle.net.exe
}
```

That should do it! 

##### Note: I tried launching HoTS directly, but was not successful. Launching `Battle.net.exe` directly allows me to run the game without issue.

##### Helpful Links:

- https://wiki.archlinux.org/index.php/Wine
- https://appdb.winehq.org/objectManager.php?sClass=version&iId=32232
- https://bbs.archlinux.org/viewtopic.php?id=109631
- https://github.com/lutris/lutris/wiki/Game:-Blizzard-App
- https://github.com/lutris/lutris/wiki/Wine-Dependencies

