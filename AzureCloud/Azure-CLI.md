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
  "azure-cli": "2.83.0",
  "azure-cli-core": "2.83.0",
  "azure-cli-telemetry": "1.1.0",
  "extensions": {}
}


$ az --version

//output:

azure-cli                         2.83.0
core                              2.83.0
telemetry                          1.1.0

Dependencies:
msal                            1.35.0b1
azure-mgmt-resource               23.3.0

Python location '/opt/az/bin/python3'
Config directory '/lhome/azahask/.azure'
Extensions directory '/lhome/azahask/.azure/cliextensions'

Python (Linux) 3.13.11 (main, Jan 27 2026, 07:21:51) [GCC 11.4.0]

Legal docs and information: aka.ms/AzureCliLegal


Your CLI is up-to-date
