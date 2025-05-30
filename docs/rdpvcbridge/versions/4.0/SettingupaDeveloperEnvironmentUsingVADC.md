---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# Setting up a Developer Environment Using VADC

You can quickly set up an environment to test the RDPVCBridge SDK at a small scale by using Horizon Agent Direct Connect (also known as VADC). VADC allows you to connect Horizon Client to the Horizon server without going through Horizon Connection Server.

## Prerequisites 

Install VMware Workstation.

## Procedure

1.  Start VMware Workstation.

1.  Create a virtual machine (VM) running a version of Windows that supports Horizon Agent. For the list of supported operating systems, see the Omnissa Knowledge Base (KB) articles [https://kb.omnissa.com/s/article/78714](https://kb.omnissa.com/s/article/78714) and [https://kb.omnissa.com/s/article/78715](https://kb.omnissa.com/s/article/78715).

    Select hardware version 8 when prompted. Select bridged networking when prompted so that the VM has its own IP address.

1.  Install VMware Tools.

    If you use the wizard to set up the VM from an ISO image file, this step is not necessary.

1.  Shut down the VM.

1.  Find the VMX file for the VM and open it in a text editor.

1.  Add the following line to the file and save it.
    ```
    machine.id = "vdi.broker.asmanaged=1"
    ```

1.  Power on the VM.

1.  Install Horizon Agent.

1.  Install the VADC plug-in.

1.  (Optional) Shut down the VM and create a snapshot.

    The snapshot allows you to roll back your changes.

1. Connect the Horizon client to the VM using the VM's IP address.

You now have a VM that is a Horizon desktop. The Horizon desktop is running with the PCoIP or Blast protocol. A Horizon client can connect to it directly over PCoIP or Blast. 

You can use the RDPVCBridge SDK to implement RDPVCBridge in this VM. With this setup, you do not need to deploy: 

- Active Directory and DNS servers
- VMware vSphere
- Horizon Connection Server