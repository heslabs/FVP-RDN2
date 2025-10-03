# Remote access to Raspberry Pi 5

#### Remote access to Raspberry Pi 5 in the cloud
```
ssh rx72@122.116.228.96 -X
Password: xxxx
```

### Running Vision AI inference on CA76

#### Yolov8
```
cd ~/rpi5cpu
make det | pos | seg
```

#### MediaPipe
```
cd ~/rpi5cpu
make md-hand
```

#### IPCamera
```
cd ~/rpi5cpu
make ipcam
```
