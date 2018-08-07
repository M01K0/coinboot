![Logo of Coinboot](coinboot.png)

This repository contains everything to get a Docker container up and running with all services needed to get Coinboot up and running in your environment.

## Requierments 

Docker

Docker Compose

## Preparations

### RootFS and Kernel

Put the Coinboot RootFS (`initramfs`) and Kernel (`vmlinuz`) into the directory `./tftpboot`.

### Plugins

You Coinboot plugins should be  placed into  the directory `./plugins`

### DHCP configuration

Put your own `dnsmasq` DHCP server configuration in `./conf/dnsmasq/` or edit the existing configuration file `./conf/dnsmasq/coinboot.conf`.

## Usage

Clone this repository one the host where you want to execute the Coinboot Docker container.

Just bring the Coinboot Docker container up with `docker-compose`.

```
$ docker-compose up -d
```

## Test and development environment

There is Vagrant environment for developing purposes.
It consists of two Vagrant machines: One with the the Coinboot Docker container and one acting as client, which boots over PXE.

To spin up the Vagrant machines execute:

```
$ vagrant up
```

## Pack your own Coinboot plugins

All you need to create your own plugins is:

* Boot the Coinboot base image

* Execute `$ create_plugin start`

* Do your changes to the system - e.g. install packages and edit configuration files.

* When your are done: Execute `$ create_plugin finish <name-of-your-plugin>`

* Place the created plugin archive into `./plugins` on the host where you run the Coinboot Docker container

Up on the next boot the changes your made in your plugin are ready to be used on your Coinboot machines!

Creation of plugins can also be scripted. Just do whatever you want to do between the lines `$ create_plugin start` and `$ create_plugin finish <name-of-your-plugin>`.

## License

GNU GPLv3 

## Author

Gunter Miegel 
gm@coinboot.io

## Contribution

Fork this repo. Use the test- and development enviroment provided.
Make a pull request to this repo. 
