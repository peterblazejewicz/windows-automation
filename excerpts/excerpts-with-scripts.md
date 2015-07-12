# Excerpts with scripts

These are some interesting scripts that could be used to modify your own image creation and box provisioning.


* Script the installation of the IIS web server and webdeploy

 ```
 Import-Module ServerManager
$features = @(
    "Web-WebServer",
    "Web-Static-Content",
    "Web-Http-Errors",
    "Web-Http-Redirect",
    "Web-Stat-Compression",
    "Web-Filtering",
    "Web-Asp-Net45",
    "Web-Net-Ext45",
    "Web-ISAPI-Ext",
    "Web-ISAPI-Filter",
    "Web-Mgmt-Console",
    "Web-Mgmt-Tools",
    "NET-Framework-45-ASPNET"
 )
 Add-WindowsFeature $features -Verbose
 iex ((new-object net.webclient).DownloadString
   ('https://chocolatey.org/install.ps1'))
 choco install webdeploy
 ```
 [Vagrant, Packer, and Chocolatey][1]


* Associate the installation script to the provision section of Vagrantfile
 ```
 config.vm.provision "shell", path: "provision-web.ps1"
 ```
 [Vagrant, Packer, and Chocolatey][1]

* Forward guest port 80 to host machine port 8080
 ```
 config.vm.network "forwarded_port", guest: 80, host: 8080, id: "iis-defaultsite"
 ```
 [Vagrant, Packer, and Chocolatey][1]

* Script the MS development tools installation
 ```PowerShell
 iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
 choco install VisualStudio2013Ultimate
 choco install MsSqlServer2012Express
 ```
 [Vagrant, Packer, and Chocolatey][1]

* RDP and start working on the development machine
 ```
 vagrant rdp
 ```

* Script the Visual Studio and Robomongo installation
 ```PowerShell
 iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
 choco install VisualStudio2013Ultimate
 choco install Robomongo
 ```
 [Vagrant, Packer, and Chocolatey][1]

* Associate the PowerShell `dev-tools.ps1` script to the `windows_2012_r2.json` template
 ```json
 {
   "type": "shell",
   "remote_path": "C:/Windows/Temp/dev-tools.ps1",
   "script": "./scripts/dev-tools.ps1",
   "execute_command": "Powershell.exe
      -executionpolicy unrestricted -File {{.Path}}"
 }
 ```
 [Vagrant, Packer, and Chocolatey][1]

* Validate the `windows_2012_r2.json` JSON configuration
 ```shell
 packer validate windows_2012_r2.json
 ```


[1]: http://www.developer.com/net/virtualize-your-windows-development-environments-with-vagrant-packer-and-chocolatey-part-2.html "Virtualize Your Windows Development Environments with Vagrant, Packer, and Chocolatey, Part 2"

