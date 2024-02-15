## Proxmox Cloud-init VM

This repository contains an Ansible role which will download the Debian and Ubuntu KVM (qcow2) images and create a QEMU/KVM Virtual Machine using these images.

It was created for a Proxmox cluster with no shared storage, only local storage, because the Telmate Proxmox Terraform provider ([Telmate Proxmox provider](https://registry.terraform.io/providers/Telmate/proxmox/latest/docs)) only supports VM creation through cloning of a VM Template and that requires shared storage to be able to clone to any node in the cluster.

The cloud-init templates included (under `playbooks/roles/proxmox-vm-cloudinit/templates/`) are basic, but can be filled out to perform more complex operations. They currently configure basic networking on boot as well as package updating/upgrading and the addition of a passwordless SSH and sudo access `ansible` account. See [Cloud config examples - cloud-init 23.4.3 documentation](https://cloudinit.readthedocs.io/en/latest/reference/examples.html) for more examples/information.

#### Download and Run

- Clone this repository with:
  
      `git clone https://github.com/NightsPaladin/proxmox-vm-cloudinit/`

- Copy the example playbook in `playbooks/example-playbook.yml` and edit to suit your needs. `hosts:` should be changed to the Proxmox node you wish to create the VM on.

- Edit the `inventory/proxmox` file to match your Proxmox cluster configuration.

- Run the playbook:
  
      `ansible-playbook yourplaybook.yml -k`

----

MIT License

Copyright (c) 2024 Chris G.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


