# Provision cloud images in a Proxmox environment

Default cloud image is **debian-buster**. You can change it in cli with ex.:
**-e default_vm_name=ubuntu-bionic**.

Currently supported cloud images:

- Debian Buster (**debian-buster**)
- Ubuntu Bionic (**ubuntu-bionic**)
- Arch Linux (**archlinux**)
- feel free to extend, see pve_vm_create_vm_images variable in [main.yml](roles/pve_vm_create/defaults/main.yml)

The role creates a custom user cloud-config, downloads the default cloud image,
creates a default VM in Proxmox, imports the cloud image, attachs as a disk,
updates boot options, resizes VM disk, then cleans up.

1. Edit [hosts](hosts) file.
2. Edit [vaults](group_vars/all/vaults) secret file, then encrypt if you mind.
3. ansible-playbook --ask-vault-pass playbook.yml
