# Development machine - ElementaryOS Vagrant Box

[![GitHub license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/fbertola/dev-box/blob/master/LICENSE)

**Current ElementaryOS Version Used**: 0.4

## Requirements

The following software must be installed on your local machine before you can use Packer to build the Vagrant box file:

  - [Packer](http://www.packer.io/)
  - [Vagrant](http://vagrantup.com/)
  - [VirtualBox](https://www.virtualbox.org/)
  - [Ansible](http://docs.ansible.com/intro_installation.html)

## Usage

Make sure all the required software (listed above) is installed, then `cd` to the root directory and run:

```bash
packer build elementaryos-0.4-amd64.json
```

After a few minutes, Packer should tell you the box was generated successfully.

## Provisioning with Vagrant

There's an included Vagrantfile that allows to provision the built Vagrant box. I used Ansible for provisioning, using roles from [Ansible-Galaxy](https://galaxy.ansible.com). From this same directory of the Vagrantfile, run the following command for downloading the necessary roles:

```bash
ansible-galaxy install -r requirements.yml
```

Then, run these commands for provisioning the machine (you may want to edit the file `provisioning/vars/main.yml`):

```bash
vagrant box add ./build/elementaryos-0.4-amd64.box fbertola/elementaryos-0.4-amd64 -f
vagrant up virtualbox --provider=virtualbox
```
