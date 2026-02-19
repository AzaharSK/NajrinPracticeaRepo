## What is Azure CLI?

Azure CLI (az) is a cross-platform command line tool used to manage Azure resources from terminal (Linux, macOS, Windows).

__👉 Alternative to:__

- Azure Portal (GUI)
- PowerShell
- REST API

__Key Point (Interview):__
- Azure CLI is mainly used for automation, DevOps pipelines, scripting and remote server management.


## Install Azure CLI (Linux – Ubuntu):

```bash
$ curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash

OR

```

## Check installation: or Version check:
```bash
$ az version

//output:
{
  "azure-cli": "2.61.0",
  "core": "2.61.0",
  "extensions": {}
}
