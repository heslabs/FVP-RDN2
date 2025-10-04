# Build FVP-RDN2 and running Ubuntu Linux OS

---
### Linux Distro Boot
https://neoverse-reference-design.docs.arm.com/en/latest/features/boot/distro_boot.html

* Neoverse Reference Design (RD) platform software stack supports boot of various linux distributions such as Debian, Ubuntu or Fedora.
* This can be achieved either by using a pre-installed (raw) image of the distribution or performing an installation from an iso image.
* The prefered method is to **use the pre-installed images** as greatly reduces the time needed to validate that the software stack can boot into Linux.
* An installation from an iso image can take several hours, and will vary greatly with the hardware used, but even on modern hardware can be around 8 hours.
* Regardless of the approach selected, the common step is to build the software stack as mentioned below in Build the platform software.


---
### Build the platform software

This section describes the procedure to build the platform firmware required to boot or install a linux distribution on Neoverse RD platforms.
To build the RD software stack, the command to be used is
```
./build-scripts/build-test-uefi.sh -p <platform name> <command>
```

Using RD-N2 as an example: \
Command to clean, build and package the software stack:
```
./build-scripts/build-test-uefi.sh -p rdn2 all
```

Command to remove the generated outputs (binaries):
```
./build-scripts/build-test-uefi.sh -p rdn2 clean
```

If using incremental builds, use target command build followed by package, so the output binaries are correctly generated. \
Command to perform an incremental build of the software stack:
```
./build-scripts/build-test-uefi.sh -p rdn2 build
./build-scripts/build-test-uefi.sh -p rdn2 package
```

 
---
### Install a Linux Distribution

After the build of the platform software stack is complete, a distribution can be installed into a SATA disk image. Before beginning the installation process, download the CD iso image of the required distribution version. See below Linux distributions downloads pages:

Linux distributions downloads pages
* Ubuntu: https://ubuntu.com/download/server/arm
* Debian: https://www.debian.org/distrib/netinst
* Fedora: https://alt.fedoraproject.org/alt



---

<img width="800" height="700" alt="image" src="https://github.com/user-attachments/assets/07b9e9d8-7bd7-4a3d-8d8b-93596bc60186" />

---

Select an image for the aarch64 architecture. Which can also be named arm64. 
```
### ubuntu-24.04.3-live-server-arm64.iso
wget https://cdimage.ubuntu.com/releases/24.04/release/ubuntu-24.04.3-live-server-arm64.iso?_gl=1*20wu8u*_gcl_au*MTQ5NjY2NzAyMy4xNzU1MDk4MTc5
```

The generic command to perform the installation is:
```
./distro.sh -p <platform name> -i <abs_iso_image_path> -s <disk size> -a <additional_params> -n [true|false]
```

As an example:
```
export MODEL=<absolute/path/to/FVP/binary>
cd model-scripts/rdinfra && ./distro.sh -p rdn2 -i <absolute/path/to/iso> -s 16
```


---
### Example boot script
```
export MODEL=$(WORKDIR)/FVP_RD_N2/models/Linux64_GCC-9.3/FVP_RD_N2 
cd model-scripts/rdinfra && ./distro.sh -p rdn2 -i ${WORKDIR}/images/ubuntu-24.04.3-live-server-arm64.iso -s 16
```

```
Login: ubuntu
Password: ubuntu
```

* This command creates a 16GB SATA disk image, boots the selected platform software stack and starts the installation process.
* From here on, follow the instructions of the chosen distribution installer. For more information about the installation procedure, refer online installation manuals of the chosen distribution.
* After the installation is complete, a disk image with a random name <number>.satadisk will be created in ```model-scripts/rdinfra/``` folder. Use this disk image for booting the installed distribution.


---
### Example boot script

* Boot from an existing installed disk image
```
export MODEL=$(WORKDIR)/FVP_RD_N2/models/Linux64_GCC-9.3/FVP_RD_N2
cd model-scripts/rdinfra && ./distro.sh -p rdn2 -d ubuntu.satadisk.rdn2

Login: root
Password: root
```
* Boot from an existing installed disk image

 
---
### Network

Please follow this to setup TAP interface

* Getting Started — Neoverse Reference Design Platform Software  documentation 
  * https://neoverse-reference-design.docs.arm.com/en/latest/user_guides/getting_started.html#enable-network-for-fvp-s-optional

```
./distro.sh -p rdn2 -d ${WORKDIR}/../images/ubuntu.satadisk -n true -a "--parameter board.virtio_net.transport=modern --parameter disable_visualisation=true"
```

---
### RD-INFRA-2024.12.20 | Ubuntu 24.04.3 LTS 

<img width="800" height="940" alt="image" src="https://github.com/user-attachments/assets/a35b5c86-f7b9-4c22-8851-3ba5e42b5638" />


---

<img width="800" height="940" alt="image" src="https://github.com/user-attachments/assets/41e5293c-cdac-4679-967e-e69bbfb549a6" />

---
<img width="800" height="940" alt="image" src="https://github.com/user-attachments/assets/750a2442-1aa1-4f02-9166-39f11fd68e6a" />


---
<img width="800" height="911" alt="image" src="https://github.com/user-attachments/assets/c2196819-8274-46ad-a400-105875a19d4c" />


---
<img width="800" height="911" alt="image" src="https://github.com/user-attachments/assets/b68a0786-951f-4468-b231-947434f0746e" />

---
<img width="800" height="911" alt="image" src="https://github.com/user-attachments/assets/6a6a95e1-f895-48be-887a-e4065f722518" />


---
<img width="800" height="940" alt="image" src="https://github.com/user-attachments/assets/6d63e355-0242-4ce0-b150-325158afda9b" />


---
<img width="800" height="940" alt="image" src="https://github.com/user-attachments/assets/983e53e8-b4b7-41ea-a8d3-53d497c21fe2" />

---
<img width="800" height="1588" alt="image" src="https://github.com/user-attachments/assets/3c3ece18-dd3c-4cea-a0f9-920d3cf37987" />

---
<img width="1000" height="932" alt="image" src="https://github.com/user-attachments/assets/4b6de5fa-5000-4662-bf19-f7cd2e480fb3" />




