### About:
This repository contains the barebones version of the network security platform, but instead of using Terraform, this uses Vagrant to initialize and configure the virtual machines.
In addition to this it uses the VirtualBox as the virtualization technology instead of QEMU and KVM.
Kali Linux has also been omitted from this version, students are expected to use the host machine to complete the tasks that were previously done on the Kali machine.

This is highly W.I.P. and as it stands is just to see how the initialization/configuration process and performance compares to the Terraform version.
The Terraform version can be found at https://github.com/lsuutari19/network_sec_platform

Requires:
- VirtualBox
- Vagrant

### Initialization:
1. Download the following vagrang boxes and move them to their respective folders:


| NAME | LINK | SIZE |
|------|------|------|
| pfSense     |  [Download](https://drive.google.com/file/d/1odDI6BPAi3Lw0rg6NuHUI54DwiM-7Fbx/view?usp=drive_link)    | 558.9MB     |
|  Ubuntu    | [Download](https://drive.google.com/file/d/1Gdmc0gv7fUG19f9UyoCqm9icKnY_61Ru/view?usp=drive_link)     | 1.1GB     |
|  Kali    | [Download](https://cdimage.kali.org/kali-2024.2/kali-linux-2024.2-virtualbox-amd64.7z)     |  very big    |

2. Go into pfSense folder and run 
```
vagrant box add pfSense pfSense.box
vagrant up
```

3. Go into pfSense folder and run 
```
vagrant box add ubuntu ubuntu.box
vagrant up
```

### Custom vagrant boxes from VMs
Create the VMs in VirtualBox as you would normally, then run the following commands in a new directory for the VM:
```
VBoxManage export <VM-name> -o <VM-name>.ova
```  

Then create a metadata.json that contains
```
{
  "provider": "virtualbox"
}

```
Then create a Vagrantfile, you can use the ones in the existing directories as a reference and run:
```
vagrant package --base <vm-name> --output <vm-name>.box
```
Now you can follow the default instructions above to launch the Vagrant boxes.


### Nested Virtualization

#### Linux Host
TO-DO

#### Windows Host
Enable SVM on AMD CPU's (or Intel's equivalent) from the BIOS and disabling the following Windows services:
-Windows Hyper-V hypervisor
-Device Guard
-Credential Guard

You know that you have everything correct if when you create the first layer VM, the "Enable Nested VT-x/AMD-V" option is choosable:
![image](https://github.com/user-attachments/assets/93bbbb5c-b84e-410e-8f56-66f25cae5682)



### TO-DO:
- Make sure the network-up.service in the Ubuntu VM in /etc/systemd/system/network-up.service works on the Vagrant network
![image](https://github.com/lsuutari19/vagrant_netwseclab/assets/55877405/520628fc-7048-4c9a-96fb-a12c4d3676b9)

- Verify that the tasks in the 2024 Terraform version of the course still work with the Vagrant version
- Test the performance on university laboratory (Not doable currently as running this VirtualBox in VirtualBox solution requires Administrator permissions to get the VirtualBox nested virtualization technology enabled)
- Create a script that does the initialization in one step
