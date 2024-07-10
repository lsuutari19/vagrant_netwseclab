### About:
This repository contains the barebones version of the network security platform, but instead of using Terraform, this uses Vagrant to initialize and configure the virtual machines.
Kali Linux has also been omitted from this version, students are expected to use the host machine to complete the tasks that were previously done on the Kali machine.

This is highly W.I.P. and as it stands is just to see how the initialization/configuration process compares to the Terraform version.
The Terraform version can be found at https://github.com/lsuutari19/network_sec_platform

Requires:
- VirtualBox
- Vagrant
- Git LFS

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

### Custom VM images
Create the VMs in VirtualBox as you would normally, then run the following commands in a new directory for the VM:
```
VBoxManage export <VM-name> <VM-name>.ova
```  

Then create a metadata.json that contains
```
{
  "provider": "virtualbox"
}

```
Then create a Vagrantfile, you can use the ones in the existing directories as a reference and run:
```
vagrant package --base <vm-name> --output <vm-name>.box --vagrantfile <path-to-your-vagrantfile>
```   



### TO-DO:
- Configure Vagrant to not automatically connect the ubuntu VM to NAT (it should be only connected to the internal network), this can be verified from the VirtualBox settings on that particular VM. Following image shows that the Adapter 1 is NAT and Enabled, this should be Disabled or completely absent after the initialization.

![image](https://github.com/lsuutari19/vagrant_netwseclab/assets/55877405/ca84bf4d-e3b8-4c61-ae03-b5431e83c826)
- Make sure the network-up.service in /etc/systemd/system/network-up.service works on the Vagrant network
![image](https://github.com/lsuutari19/vagrant_netwseclab/assets/55877405/520628fc-7048-4c9a-96fb-a12c4d3676b9)

- Verify that the tasks in the 2024 Terraform version of the course still work with the Vagrant version
- Test the performance on university laboratory
- Test the performance on native Windows
- Create a script that does the initialization in one step
