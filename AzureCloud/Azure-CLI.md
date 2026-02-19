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
```json
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
```json
$ az login
```
➡ Opens browser → login → returns subscription list

```json
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
```json
$ az login --use-device-code

To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code I7DBYCUC9 to authenticate.

```
- ➡ Opens browser ➡ Open __https://microsoft.com/devicelogin__ , provide credntial
- <img width="1425" height="786" alt="image" src="https://github.com/user-attachments/assets/c55b61c4-fb9a-45c0-930d-d6b5494965a8" />


## Account & Subscription

### List subscriptions
```json
$ az account list -o table

Output:

Name             CloudName    State    IsDefault
---------------  ----------   ------   ---------
Pay-As-You-Go    AzureCloud   Enabled  True
Azure-subscription-1  AzureCloud   d8489a1f-c93d-42ee-8068-72ae05f9915b  049c681e-8862-4679-80f0-02ec174c200b  Enabled  True

```

## Set subscription
```json
$ az account set --subscription "Azure-subscription-1"
```

## SHow Login Account details:
```json
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


## 1️⃣ Create Resource Group:

```json
$ az group create \
  --name Todo-Webapp-prod-rg \
  --location centralindia


// Output:
{
  "id": "/subscriptions/d8489a1f-c93d-42ee-8068-72ae05f9915b/resourceGroups/Todo-Webapp-prod-rg",
  "location": "centralindia",
  "managedBy": null,
  "name": "Todo-Webapp-prod-rg",
  "properties": {
    "provisioningState": "Succeeded"
  },
  "tags": null,
  "type": "Microsoft.Resources/resourceGroups"
}

```

<img width="944" height="387" alt="image" src="https://github.com/user-attachments/assets/77282828-6071-4160-baae-4ec7519cabcb" />





## 3️⃣ Create Virtual Network (Networking First)

```json
$ az network vnet create \
  --resource-group Todo-Webapp-prod-rg \
  --name todo-vnet \
  --subnet-name todo-subnet

// Output:
{
  "newVNet": {
    "name": "todo-vnet",
    "subnets": [
      { "name": "todo-subnet" }
    ]
  }
}


```

## 4️⃣ Create Storage Account (Images):

```json
az storage account create \
  --name todostorageprod12345 \
  --resource-group Todo-Webapp-prod-rg \
  --location centralindia \
  --sku Standard_LRS


//Output:

{
  "accessTier": "Hot",
  "allowBlobPublicAccess": false,
  "creationTime": "2026-02-19T08:41:22.123456+00:00",
  "enableHttpsTrafficOnly": true,
  "id": "/subscriptions/1a2b3c4d-xxxx-xxxx/resourceGroups/Todo-Webapp-prod-rg/providers/Microsoft.Storage/storageAccounts/todostorageprod12345",
  "kind": "StorageV2",
  "location": "centralindia",
  "minimumTlsVersion": "TLS1_2",
  "name": "todostorageprod12345",
  "primaryEndpoints": {
    "blob": "https://todostorageprod12345.blob.core.windows.net/",
    "dfs": "https://todostorageprod12345.dfs.core.windows.net/",
    "file": "https://todostorageprod12345.file.core.windows.net/",
    "queue": "https://todostorageprod12345.queue.core.windows.net/",
    "table": "https://todostorageprod12345.table.core.windows.net/"
  },
  "primaryLocation": "centralindia",
  "provisioningState": "Succeeded",
  "resourceGroup": "Todo-Webapp-prod-rg",
  "sku": {
    "name": "Standard_LRS",
    "tier": "Standard"
  },
  "statusOfPrimary": "available",
  "type": "Microsoft.Storage/storageAccounts"
}

```

<img width="942" height="555" alt="image" src="https://github.com/user-attachments/assets/d4f0ce21-eb2c-4412-9606-96ffe8f38497" />

## 5️⃣ Create SQL Database (Store Data):

### Create SQL Server

```json
$ az sql server create \
  --name todo-sql-server-prod \
  --resource-group Todo-Webapp-prod-rg \
  --location centralindia \
  --admin-user sqladmin \
  --admin-password StrongPass@123

{
  "administratorLogin": "sqladmin",
  "administratorLoginPassword": null,
  "fullyQualifiedDomainName": "todo-sql-server-prod.database.windows.net",
  "id": "/subscriptions/xxxx/resourceGroups/Todo-Webapp-prod-rg/providers/Microsoft.Sql/servers/todo-sql-server-prod",
  "kind": "v12.0",
  "location": "centralindia",
  "name": "todo-sql-server-prod",
  "publicNetworkAccess": "Enabled",
  "resourceGroup": "Todo-Webapp-prod-rg",
  "state": "Ready",
  "type": "Microsoft.Sql/servers",
  "version": "12.0"
}


```

<img width="859" height="402" alt="image" src="https://github.com/user-attachments/assets/e1240e30-7c9f-4dd0-92b3-92aad8fa78a8" />

### Create Database

```json

$ az sql db create \
  --resource-group Todo-Webapp-prod-rg \
  --server todo-sql-server-prod \
  --name todo-db \
  --service-objective S0


// Sample Output:

{
  "collation": "SQL_Latin1_General_CP1_CI_AS",
  "creationDate": "2026-02-19T09:02:11.45Z",
  "currentServiceObjectiveName": "S0",
  "databaseId": "c7c6c2e5-xxxx-xxxx",
  "defaultSecondaryLocation": null,
  "earliestRestoreDate": "2026-02-19T09:12:11.45Z",
  "id": "/subscriptions/xxxx/resourceGroups/Todo-Webapp-prod-rg/providers/Microsoft.Sql/servers/todo-sql-server-prod/databases/todo-db",
  "location": "centralindia",
  "maxSizeBytes": 268435456000,
  "name": "todo-db",
  "requestedServiceObjectiveName": "S0",
  "resourceGroup": "Todo-Webapp-prod-rg",
  "status": "Online",
  "type": "Microsoft.Sql/servers/databases"
}

```

<img width="900" height="282" alt="image" src="https://github.com/user-attachments/assets/bde3f8fe-0398-44e5-b7b7-5c02a877ddba" />


## 6️⃣ Create Backend VM (APIs):

```json
Create Backend VM (APIs)
az vm create \
  --resource-group Todo-Webapp-prod-rg \
  --name todo-backend-vm \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys \
  --vnet-name todo-vnet \
  --subnet todo-subnet

// Sample Output:

{
  "fqdns": "",
  "id": "/subscriptions/xxxx/resourceGroups/Todo-Webapp-prod-rg/providers/Microsoft.Compute/virtualMachines/todo-backend-vm",
  "location": "centralindia",
  "macAddress": "00-0D-3A-B1-2C-55",
  "powerState": "VM running",
  "privateIpAddress": "10.0.0.4",
  "publicIpAddress": "20.204.75.118",
  "resourceGroup": "Todo-Webapp-prod-rg",
  "zones": ""
}

```

- __After creation:__ `publicIpAddress:` 20.xx.xx.xx
- __Connect:__ ssh azureuser@20.xx.xx.xx


<img width="992" height="310" alt="image" src="https://github.com/user-attachments/assets/16a7717a-d570-4606-8914-73a30bf5b487" />

__When you run az vm create, Azure also automatically creates:__

- Network Interface (NIC)
- Public IP
- Network Security Group (NSG)
- OS Disk
- SSH Keys (in ~/.ssh)







## Why Azure CLI used in DevOps?

- CMD line Automation script recipes
- Infrastructure as Code (IAC)
- GitLab and github CI/CD pipelines
- Docker/Kubernetes deployments
- Remote server management

