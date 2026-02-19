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



// OR Manually :

sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -sLS https://packages.microsoft.com/keys/microsoft.asc |
  gpg --dearmor | sudo tee /etc/apt/keyrings/microsoft.gpg > /dev/null
sudo chmod go+r /etc/apt/keyrings/microsoft.gpg

AZ_DIST=$(lsb_release -cs)
echo "Types: deb
URIs: https://packages.microsoft.com/repos/azure-cli/
Suites: ${AZ_DIST}
Components: main
Architectures: $(dpkg --print-architecture)
Signed-by: /etc/apt/keyrings/microsoft.gpg" | sudo tee /etc/apt/sources.list.d/azure-cli.sources

sudo apt-get update
sudo apt-get install azure-cli
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

```

## 3) Login to Azure
```bash
$ az login
```
➡ Opens browser → login → returns subscription list

```bash
[
  {
    "cloudName": "AzureCloud",
    "tenantId": "4f2a-xxxx-xxxx",
    "id": "1234-5678-9012",
    "isDefault": true,
    "name": "Pay-As-You-Go",
    "state": "Enabled",
    "user": {
      "name": "user@gmail.com",
      "type": "user"
    }
  }
]
```

## Login from Server:
```bash
$ az login --use-device-code

To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code I7DBYCUC9 to authenticate.

```
- ➡ Opens browser ➡ Open __https://microsoft.com/devicelogin__ , provide credntial
- <img width="1425" height="786" alt="image" src="https://github.com/user-attachments/assets/c55b61c4-fb9a-45c0-930d-d6b5494965a8" />


## Account & Subscription

### List subscriptions
```bash
$ az account list -o table

Output:

Name             CloudName    State    IsDefault
---------------  ----------   ------   ---------
Pay-As-You-Go    AzureCloud   Enabled  True
Azure-subscription-1  AzureCloud   d8489a1f-c93d-42ee-8068-72ae05f9915b  049c681e-8862-4679-80f0-02ec174c200b  Enabled  True

```

## Set subscription
```
$ az account set --subscription "Azure-subscription-1"
```

## SHow Login Account details:
```bash
$ az account show

//Output:
{
  "environmentName": "AzureCloud",
  "homeTenantId": "049c681e-8862-4679-80f0-02ec174c200b",
  "id": "d8489a1f-c93d-42ee-8068-72ae05f9915b",
  "isDefault": true,
  "managedByTenants": [],
  "name": "Azure-subscription-1",
  "state": "Enabled",
  "tenantDefaultDomain": "azaharsk2025gmail.onmicrosoft.com",
  "tenantDisplayName": "Default Directory",
  "tenantId": "049c681e-8862-4679-80f0-02ec174c200b",
  "user": {
    "name": "azahar.sk.2025@gmail.com",
    "type": "user"
  }
}
```

## Where used (Interview Tip):
-  Azure CLI commands are Used inside VM, SSH, CI/CD servers.



## What is a Resource Group in Azure?

_ A Resource Group in Microsoft Azure is a logical container (Grouping of releated resources) that holds related cloud resources such as:

- Virtual Machines
- Storage Accounts
- Databases
- Web Apps
- Networking components

- A resource group is used to manage, monitor, and deploy related Azure resources together as a single unit.
- Instead of managing 50 resources separately, you manage them together.


__Key Benefits of using Resource Group:__

- Lifecycle management (create/delete together) for example- Deleting a Resource Group deletes ALL resources inside it.
- Access control (RBAC permissions)
- Billing grouping
- Easy automation & deployment
- Environment separation (Dev / Test / Prod)

<img width="1769" height="973" alt="image" src="https://github.com/user-attachments/assets/82fa42bb-455f-43cd-bf4d-09a0c95a50b1" />

## Why Azure CLI used in DevOps?

- CMD line Automation script recipes
- Infrastructure as Code (IAC)
- GitLab and github CI/CD pipelines
- Docker/Kubernetes deployments
- Remote server management
