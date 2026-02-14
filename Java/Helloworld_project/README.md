## This My Hello World Project 
- Ref: https://github.com/in28minutes/deploy-spring-boot-to-azure
  
```bash
sudo snap install eclipse --classic
sudo apt install default-jre
```
```bash
mkdir javaproject
cd javaproject/
~/javaproject$ git clone https://github.com/in28minutes/deploy-spring-boot-to-azure.git
~/javaproject$ cd deploy-spring-boot-to-azure/
~/javaproject/deploy-spring-boot-to-azure$ ls -l
total 44
drwxrwxr-x 3 azahask domainusers  4096 Feb 13 23:27 01-hello-world-rest-api
drwxrwxr-x 3 azahask domainusers  4096 Feb 13 23:27 02-todo-web-application-h2
drwxrwxr-x 3 azahask domainusers  4096 Feb 13 23:27 03-todo-web-application-mysql
drwxrwxr-x 4 azahask domainusers  4096 Feb 13 23:27 04-spring-boot-react-full-stack-h2
drwxrwxr-x 3 azahask domainusers  4096 Feb 13 23:27 05-todo-rest-api-h2-containerized
drwxrwxr-x 4 azahask domainusers  4096 Feb 13 23:27 06-todo-rest-api-mysql-containerized
drwxrwxr-x 3 azahask domainusers  4096 Feb 13 23:27 07-hello-world-rest-api
-rw-rw-r-- 1 azahask domainusers 15849 Feb 13 23:27 README.md
```
# Eclipise --> File --> import ---> maven --> existing maven projects
<img width="1808" height="954" alt="image" src="https://github.com/user-attachments/assets/ccea0b68-0efa-4086-a18f-9c84bdc61f16" />


<img width="1833" height="1071" alt="image" src="https://github.com/user-attachments/assets/1811e955-5c76-4ee3-86b4-6c4e3021e7e3" />

pom.xml--> rightClick--->n  mavenbuild
<img width="1808" height="954" alt="image" src="https://github.com/user-attachments/assets/263310e3-b33d-4f3b-9e29-4fa3227a88fd" />
<img width="1794" height="1127" alt="image" src="https://github.com/user-attachments/assets/31815fd2-7690-42dc-915f-e245c307c402" />
<img width="1374" height="1161" alt="image" src="https://github.com/user-attachments/assets/c02bcb06-85ca-4292-bb39-bcc2cb731b3b" />

```bash
/01-hello-world-rest-api$ mvn azure-webapp:config
[INFO] Scanning for projects...
[INFO] 
[INFO] ------< com.in28minutes.rest.webservices:01-hello-world-rest-api >------
[INFO] Building hello-world-rest-api 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- azure-webapp-maven-plugin:1.7.0:config (default-cli) @ 01-hello-world-rest-api ---
Please choose which part to config
1. Application
2. Runtime
3. DeploymentSlot
Enter index to use: 
Invalid index.
Enter index to use: 1   
Define value for appName(Default: 01-hello-world-rest-api-Najrin-1771053610324): 
Define value for resourceGroup(Default: 01-hello-world-rest-api-1771053610324-rg): 
Define value for region(Default: southindia): 
Define value for pricingTier(Default: F1): 
1. b1
2. b2
3. b3
4. d1
5. f1 [*]
6. p1v2
7. p2v2
8. p3v2
9. s1
10. s2
11. s3
Enter index to use: 
Please confirm webapp properties
AppName : 01-hello-world-rest-api-Najrin-1771053610324
ResourceGroup : 01-hello-world-rest-api-1771053610324-rg
Region : southindia
PricingTier : Free_F1
OS : Linux
RuntimeStack : JAVA 11-java11
Deploy to slot : false
Confirm (Y/N)? : Y
[INFO] Saving configuration to pom.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  29.903 s
[INFO] Finished at: 2026-02-14T13:32:21+05:30
[INFO] ------------------------------------------------------------------------
Feb 14, 2026 1:32:21 PM com.microsoft.applicationinsights.core.dependencies.http.impl.execchain.RetryExec execute
INFO: I/O exception (java.net.SocketException) caught when processing request to {s}->https://dc.services.visualstudio.com:443: Socket closed
Feb 14, 2026 1:32:21 PM com.microsoft.applicationinsights.core.dependencies.http.impl.execchain.RetryExec execute
INFO: I/O exception (java.net.SocketException) caught when processing request to {s}->https://rt.services.visualstudio.com:443: Socket closed
Feb 14, 2026 1:32:21 PM com.microsoft.applicationinsights.core.dependencies.http.impl.execchain.RetryExec execute
INFO: I/O exception (java.net.SocketException) caught when processing request to {s}->https://dc.services.visualstudio.com:443: Socket closed

```

```bash
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
```bash
 az --version
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
```


```bash
az login --use-device-code
To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code I7DBYCUC9 to authenticate.

```

<img width="1425" height="786" alt="image" src="https://github.com/user-attachments/assets/9af24a63-ec27-4e5a-9ed9-be66a7cb08f5" />

```bash
az account show
{
  "environmentName": "AzureCloud",
  "homeTenantId": "049c681e-8862-4679-80f0-02ec174c200b",
  "id": "d8489a1f-c93d-42ee-8068-72ae05f9915b",
  "isDefault": true,
  "managedByTenants": [],
  "name": "Azure subscription 1",
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
