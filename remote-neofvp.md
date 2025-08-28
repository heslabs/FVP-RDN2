# Remote access to the FVP-RDN2


### Quick Start Guide

* Remote access the host server cx9
```
ssh neofvp@59.124.169.198 -X
Password:
```

* Launch RDN2 FVP and booting Ubuntu Linux
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

---
### Results


