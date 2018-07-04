# Ansible Playbook Nvidia GPU Docker Demo

This playbook is to show off an easy method to install Docker with Nvidia GPU support on a supported linux host.
The playbook can run against a bare metal machine, virtual machine or cloud based machine. [Datadrivers GmbH](http://www.datadrivers.de "Datadrivers GmbH") is prefering to use it with an AWS EC2 instance from the P2-, P3- or G3-series.

## Requirements

* Ansible 2.1+
* SSH access and sudo permissions (login user!)
* target host with installed linux OS with systemd
* for nvidia-docker usage: a host with a compatible Nvidia graphic card
* Internet access to get the packages and gpg keys

## Supported platforms

* CentOS 7
* RedHat 7

## Usage

### Preparations

* open a terminal / console

* git clone the repository on your system and switch into the directory

* use ansible-galaxy to install the required role: `ansible-galaxy install -v -r requirements.yml`

* edit the inventory file `inventory/hosts` to match the target server

* edit the definition file for the role `group_vars/docker-host` to deactivate/activate Nvidia-GPU installation steps

### Run the playbook

Please use instead of user `centos`, the right user to get SSH access and sudo permissions on the target system.

* start the playbook run: `ansible-playbook demo.yml --user centos --diff -v`

* If you install the Nvidia-docker2 parts, please reboot the target system after the completion!

### Test the Docker environment

Log onto the target system and try to start an example Nvidia CUDA container: `sudo docker run --rm nvidia/cuda nvidia-smi`

## License

* MIT license (check file `LICENSE` for more details)

## Issue Tracker

Please use the [Github Repository Issue tracker](https://github.com/datadrivers/ansible-playbook-nvidia_gpu_docker_demo/issues) to report us bugs.

## Contributions

Feel free to clone the code, make a branch and to hack your stuff. After that make a pull request and we can check it. We are open for improvements.

## Author Information

* Markus Rekkenbeil - [(Datadrivers GmbH)](http://www.datadrivers.de "Datadrivers GmbH")
