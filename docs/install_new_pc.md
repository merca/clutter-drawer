# Setup a new PC

I love powershell and before continuing, this is what I set up first

```sh
# get powershell and some styling for it

winget install --id=Microsoft.PowerShell  -e;

```

Now, it’s time to saunter over to PowerShell and doll it up a bit 🖌️

```sh
winget install --id=Starship.Starship  -e;

# settings on starship
# [read config documentations](https://starship.rs/config/)

mkdir $HOME/.config
New-Item $HOME/.config/starship.toml
notepad $HOME/.config/starship.toml #(after installing visual studio code: use code $HOME....)

New-Item $profile;
Add-Content $profile -Value 'Invoke-Expression (&starship init powershell)';
Add-Content $profile -Value 'Import-Module -Name Terminal-Icons';
```

With that, let’s venture forth and install a cornucopia of tools. My toolbox is akin to Aladdin's cave.
I pluck my winget IDs from the treasure trove that is [wininstall](https://winstall.app)

```sh
winget install --id=VivaldiTechnologies.Vivaldi -e;
winget install --id=Git.Git -e;
winget install --id=PuTTY.PuTTY -e;
winget install --id=GnuPG.Gpg4win -e;
winget install --id=Postman.Postman -e;
winget install --id=Microsoft.VisualStudio.2022.Community -e;
winget install --id=Microsoft.AzureCLI -e;
winget install --id=Microsoft.Azure.StorageExplorer -e;
winget install --id=Microsoft.AzureDataStudio.Insiders -e;
winget install --id=Microsoft.AzureFunctionsCoreTools -e;
winget install --id=Obsidian.Obsidian -e;
winget install --id=Google.GoogleDrive -e;
winget install --id=Axosoft.GitKraken -e;
winget install --id=GitHub.cli -e;
winget install --id=Amazon.AWSCLI -e;
winget install --id=Google.CloudSDK -e;
winget install --id 7zip.7zip -e;
winget install --id=OpenJS.NodeJS -e;
winget install --id=Python.Python.3.12  -e;
winget install --id=Pulumi.Pulumi  -e;
winget install --id=Hashicorp.Terraform  -e;
winget install -e --id=Kubernetes.kubectl
```

Onward to setting up GitHub!

```sh
#Set up github
git config --global user.name "<Full Name>"
git config --global user.email <githubusername>@users.noreply.github.com
git config --global commit.gpgsign true
```

While some configuration is yet to be done, like cloud authentication and environment variable setup,
I prefer to keep the latter, especially secrets, in a neat little PowerShell script tucked away in my vault.

```sh
#set scope ::User user
[Environment]::SetEnvironmentVariable("var-name",
    'var-value',
    [System.EnvironmentVariableTarget]::Machine)

#or append
[Environment]::SetEnvironmentVariable("Path",
    [Environment]::GetEnvironmentVariable("Path", [EnvironmentVariableTarget]::Machine) + ";C:\bin",
    [EnvironmentVariableTarget]::Machine)
```

Also I need Linux subsystem for windows (yeah i know)

```sh
#Linux subsustem for windows
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
wsl --install --no-distribution
```

> A pit stop for a restart is warranted at this juncture.