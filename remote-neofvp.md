# Remote access to Linux PC for running FVP


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

```
rdn2 login: root
Password: root
```

Test the Eternet connection

<img width="550" height="524" alt="image" src="https://github.com/user-attachments/assets/6788aba8-ec16-452b-ae29-cfdc8080e284" />

<img width="650" height="331" alt="image" src="https://github.com/user-attachments/assets/be293ee3-5877-40c6-bf72-48cf0888338d" />


---
### FVP console ouptut

<img width="800" height="1062" alt="image" src="https://github.com/user-attachments/assets/1816fe99-268c-41e3-8fb6-8b644958a45f" />
 
<img width="800" height="1062" alt="image" src="https://github.com/user-attachments/assets/abfb50e4-f6a3-4c2e-9c8b-b7392de5e937" />
