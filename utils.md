# Utilis


---
### Console

* How to change the default font size of XTerm?
    * https://askubuntu.com/questions/161652/how-to-change-the-default-font-size-of-xterm
    * You can add the following as an example to your ~/.Xresources file:

```
! Use a truetype font and size.
xterm*faceName: Monospace
xterm*faceSize: 14
```

Then run the following:
```
xrdb -merge ~/.Xresources
```

---
### Network

Please follow this to setup TAP interface

* Getting Started — Neoverse Reference Design Platform Software  documentation 
  * https://neoverse-reference-design.docs.arm.com/en/latest/user_guides/getting_started.html#enable-network-for-fvp-s-optional

```
./distro.sh -p rdn2 -d ${WORKDIR}/../images/ubuntu.satadisk -n true -a "--parameter board.virtio_net.transport=modern --parameter disable_visualisation=true"
```
