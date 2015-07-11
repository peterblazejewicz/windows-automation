# Windows automation

A short compendium of tools and articles used in one-day automation workshop we used @work - so it can be expanded in future.

Recently during a one-day long workshop at work we succesfully automated entire process of Windows OS image creation, installation and provisioning, from the very fresh `.iso` installation file up to typing `vagrant rdp` to automatically log into fully provisioned system. The list of usefull tools and readings used during that workshop will be included here.
In the future the list will be updated, as we will be using and adding our own PowerShell provisioning scripts.

## Tools

### Packer

> Packer is a tool for creating machine and container images for multiple platforms from a single source configuration.

We used Packer to create machine image based on `Windows Server 2012R2` for development virtualization using `Virtual Box`.

https://packer.io/

> Hint: We used `headless: false` in Packer configuration file for builder to be able to get accustomed with Packer image creation.

## Author

Peter Blazejewicz
@peterblazejewicz
