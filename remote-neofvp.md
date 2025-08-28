# Remote access to run FVP-RDN2


### Quick Start Guide

Remote access the host server cx9
```
ssh neofvp@122.116.228.96 -X
Password:
```

Launch RDN2 FVP and booting Ubuntu Linux
```
cd ~/labs/infra/rdn2-ubuntu/
./run.sh
```

```
### run.sh
#!/bin/bash -f
export WORKDIR=${PWD}
export MODEL=${WORKDIR}/FVP_RD_N2/models/Linux64_GCC-9.3/FVP_RD_N2
cd model-scripts/rdinfra
./distro.sh -p rdn2 -d ${WORKDIR}/../images/ubuntu.satadisk.rdn2 -n true
```

It takes about 10-min to run upto the Linux login prompt

---
### FVP console ouptut

<img width="800" height="1062" alt="image" src="https://github.com/user-attachments/assets/1816fe99-268c-41e3-8fb6-8b644958a45f" />
 
