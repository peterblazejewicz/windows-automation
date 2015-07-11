# Windows automation

A short compendium of tools and articles used in one-day automation workshop we used @work - so it can be expanded in future.

Recently during a one-day long workshop at work we succesfully automated entire process of Windows OS image creation, installation and provisioning, from the very fresh `.iso` installation file up to typing `vagrant rdp` to automatically log into fully provisioned system. The list of usefull tools and readings used during that workshop will be included here.
In the future the list will be updated, as we will be using and adding our own PowerShell provisioning scripts.

## Tools

### Packer

> Packer is a tool for creating machine and container images for multiple platforms from a single source configuration.

We used Packer to create machine image based on `Windows Server 2012R2` for development virtualization using `Virtual Box`.

[https://packer.io/](https://packer.io/)

> Hint: We used `headless: false` in Packer configuration file for builder to be able to get accustomed with Packer image creation.

### Windows Packer Templates

> Windows templates that can be used to create boxes for Vagrant using Packer

[https://github.com/joefitzgerald/packer-windows](https://github.com/joefitzgerald/packer-windows)

We have used `windows_2012_r2` template when creating Packer machine image.

### Vagrant

> Vagrant provides easy to configure, reproducible, and portable work environments built on top of industry-standard technology and controlled by a single consistent workflow to help maximize the productivity and flexibility of you and your team.

[https://www.vagrantup.com/](https://www.vagrantup.com/)

The machine image created with `Packer` was then registered as `Vagrant` box and installed and run on local development machine with `Windows 8.1` host system.

## Author

Peter Blazejewicz
@peterblazejewicz
