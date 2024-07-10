### About:
This repository contains the barebones version of the network security platform, but instead of using Terraform, this uses vagrant to initialize and configure the virtual machines.
Kali Linux has also been omitted from this version, students are expected to use the host machine to complete the tasks that were previously done on the Kali machine.

This is highly W.I.P. and as it stands is just to see how the initialization/configuration process compares to the Terraform version.
The Terraform version can be found at https://github.com/lsuutari19/network_sec_platform

Requires:
VirtualBox
Vagrant

### Initialization:
1. Go into pfSense folder and run 
```
vagrant box add pfSense pfSense.box
vagrant up
```

2. Go into pfSense folder and run 
```
vagrant box add ubuntu ubuntu.box
vagrant up
```

### TO-DO:
- Configure Vagrant to not automatically connect the ubuntu VM to NAT (it should be only connected to the internal network), this can be verified from the VirtualBox settings on that particular VM. Following image shows that the Adapter 1 is NAT and Enabled, this should be Disabled or completely absent after the initialization.

![image](https://github.com/lsuutari19/vagrant_netwseclab/assets/55877405/ca84bf4d-e3b8-4c61-ae03-b5431e83c826)
- Verify that the tasks in the 2024 Terraform version of the course still work with the Vagrant version
- Test the performance on university laboratory
- Test the performance on native Windows
- Create a script that does the initialization in one step
