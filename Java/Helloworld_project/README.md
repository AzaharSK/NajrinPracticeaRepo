## This My Hello World Project 
- Ref: https://github.com/in28minutes/deploy-spring-boot-to-azure
  

## Setup Azure CLI:

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

## Set up Eclipise Development IDE

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
<img width="1856" height="1146" alt="image" src="https://github.com/user-attachments/assets/3e8d315d-ee4a-495e-9f14-ed6713591d49" />

### __Maven plugin config:__
- groupId: com.microsoft.azure
- artifactId: azure-webapp-maven-plugin
- version: 2.13.0

### __Azure cloud config:__
- resourceGroup: helloworldnajrin-rg
- appName: helloworldnajrin
  
- pricingTier: B1
- region: westeurope
- server.port=80

### __Runtime config:__
- os:  Linux
- javaVersion: 17
- webContainer: Java SE
  
```xml
      <plugin> 
        <groupId>com.microsoft.azure</groupId>  
        <artifactId>azure-webapp-maven-plugin</artifactId>  
        <version>2.13.0</version>
          <configuration>
              <schemaVersion>V2</schemaVersion>
              <resourceGroup>helloworldnajrin-rg</resourceGroup>
              <appName>helloworldnajrin</appName>
              <pricingTier>B1</pricingTier>
              <region>westeurope</region>
              <appSettings>
                  <property>
                      <name>JAVA_OPTS</name>
                      <value>-Dserver.port=80</value>
                  </property>
              </appSettings>
              <runtime>
                  <os>Linux</os>
                  <javaVersion>Java 17</javaVersion>
                  <webContainer>Java SE</webContainer>
              </runtime>
              <deployment>
                  <resources>
                      <resource>
                          <directory>${project.basedir}/target</directory>
                          <includes>
                              <include>*.jar</include>
                          </includes>
                      </resource>
                  </resources>
              </deployment>
          </configuration>
      </plugin>
```

## By default spring does not add swagger API docs , you need to enable it
- Modern Springdoc — recommended - Spring Boot 3+
- Add dependency:
```xml
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.5.0</version>
</dependency>
```
- open src/main/resources/application.properties
- Add below lines:

```java
logging.level.org.springframework = debug

server.port=${PORT:8080}
server.forward-headers-strategy=framework
```

`pom.xml--> rightClick---> Run as mavenbuild`
<img width="1808" height="954" alt="image" src="https://github.com/user-attachments/assets/263310e3-b33d-4f3b-9e29-4fa3227a88fd" />

```bash

mvn azure-webapp:config
[INFO] Scanning for projects...
[INFO] 
[INFO] ------< com.in28minutes.rest.webservices:01-hello-world-rest-api >------
[INFO] Building hello-world-rest-api 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- azure-webapp-maven-plugin:2.13.0:config (default-cli) @ 01-hello-world-rest-api ---
Please choose which part to config [Application]:
* 1: Application
  2: Runtime
  3: DeploymentSlot
Enter your choice: 1
Define value for appName [helloworldnajrin]: 
Define value for resourceGroup [helloworldnajrin-rg]: 
Define value for region [westeurope]: 
Define value for pricingTier [B1]:
   1: D1
   2: B3
   3: P1v2
   4: P1v3
   5: P2v2
   6: P2v3
   7: P3v2
   8: P3v3
*  9: B1
  10: B2
  11: F1
  12: S1
  13: S2
  14: S3
  15: EP3
  16: EP2
  17: EP1
  18: Y1
  19: FC1
Enter your choice: 
Please confirm webapp properties
AppName : helloworldnajrin
ResourceGroup : helloworldnajrin-rg
Region : westeurope
PricingTier : B1
OS : Linux
Java Version: Java 17
Web server stack: Java SE
Deploy to slot : false
Confirm (Y/N) [Y]: Y
[INFO] Saving configuration to pom.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  19.085 s
[INFO] Finished at: 2026-02-14T15:25:25+05:30
[INFO] ------------------------------------------------------------------------
```
```bash
01-hello-world-rest-api$ mvn azure-webapp:config
[INFO] Scanning for projects...
[INFO] 
[INFO] ------< com.in28minutes.rest.webservices:01-hello-world-rest-api >------
[INFO] Building hello-world-rest-api 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- azure-webapp-maven-plugin:2.13.0:config (default-cli) @ 01-hello-world-rest-api ---
Please choose which part to config [Application]:
* 1: Application
  2: Runtime
  3: DeploymentSlot
Enter your choice: 2
[WARNING] The plugin may not work if you change the os of an existing webapp.
Define value for OS [Linux]:
  1: Windows
* 2: Linux
  3: Docker
Enter your choice: 
Define value for javaVersion [Java 17]:
* 1: Java 17
  2: Java 11
  3: Java 8
Enter your choice: 
[INFO] Skip web container selection for "jar" project.
Please confirm webapp properties
AppName : helloworldnajrin
ResourceGroup : helloworldnajrin-rg
Region : westeurope
PricingTier : B1
OS : Linux
Java Version: Java 17
Web server stack: Java SE
Deploy to slot : false
Confirm (Y/N) [Y]: Y
[INFO] Saving configuration to pom.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  14.606 s
[INFO] Finished at: 2026-02-14T15:26:09+05:30
[INFO] ------------------------------------------------------------------------
```

```bash

01-hello-world-rest-api$ mvn clean package

01-hello-world-rest-api$ az appservice plan list --output table
AsyncScalingEnabled    ElasticScaleEnabled    FreeOfferExpirationTime     HyperV    IsSpot    IsXenon    Kind    Location     MaximumElasticWorkerCount    MaximumNumberOfWorkers    Name                   NumberOfSites    NumberOfWorkers    PerSiteScaling    Reserved    ResourceGroup        Status    TargetWorkerCount    TargetWorkerSizeId    ZoneRedundant
---------------------  ---------------------  --------------------------  --------  --------  ---------  ------  -----------  ---------------------------  ------------------------  ---------------------  ---------------  -----------------  ----------------  ----------  -------------------  --------  -------------------  --------------------  ---------------
False                  False                  2026-03-16T09:14:49.166666  False     False     False      linux   West Europe  1                            3                         asp-helloworldnajrin   1                1                  False             True        helloworldnajrin-rg  Ready     0                    0                     False



mvn azure-webapp:deploy

```

```bash
01-hello-world-rest-api$ mvn azure-webapp:deploy
[INFO] Scanning for projects...
[INFO] 
[INFO] ------< com.in28minutes.rest.webservices:01-hello-world-rest-api >------
[INFO] Building hello-world-rest-api 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- azure-webapp-maven-plugin:2.13.0:deploy (default-cli) @ 01-hello-world-rest-api ---
Gtk-Message: 14:59:53.413: Failed to load module "appmenu-gtk-module"
[INFO] Auth type: AZURE_CLI
[INFO] Username: azahar.sk.2025@gmail.com
[INFO] Subscription: Azure subscription 1(d8489a1f-c93d-42ee-8068-72ae05f9915b)
[INFO] Start creating Web App(helloworldnajrin)...
[INFO] Web App(helloworldnajrin) is successfully created
[INFO] Trying to deploy external resources to helloworldnajrin...
[INFO] Successfully deployed the resources to helloworldnajrin
[INFO] Trying to deploy artifact to helloworldnajrin...
[INFO] Deploying (/lhome/azahask/javaproject/deploy-spring-boot-to-azure/01-hello-world-rest-api/target/hello-world-rest-api.jar)[jar]  ...

[INFO] Application url: https://helloworldnajrin.azurewebsites.net                                  
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  05:03 min
[INFO] Finished at: 2026-02-14T15:04:51+05:30
[INFO] ------------------------------------------------------------------------
```

## REST EndPOints available in src code:
<img width="1483" height="609" alt="image" src="https://github.com/user-attachments/assets/6ee6ed32-9a25-4e51-873b-c636d5c81114" />
<img width="696" height="95" alt="image" src="https://github.com/user-attachments/assets/d32e1e87-f61c-46fb-9163-7e15d9834ae7" />
<img width="623" height="199" alt="image" src="https://github.com/user-attachments/assets/98370267-72df-4d62-b2da-2edf7f252865" />
<img width="880" height="177" alt="image" src="https://github.com/user-attachments/assets/7e3b83e0-66b7-4415-82c4-e4abba3db1ac" />

## Azure
```
GET https://helloworldnajrin.azurewebsites.net/hello-world-bean
```

<img width="1845" height="952" alt="image" src="https://github.com/user-attachments/assets/2a9e813b-9ee9-4687-8e6b-eb302abc5419" />
<img width="1810" height="578" alt="image" src="https://github.com/user-attachments/assets/e17b8016-15be-4ef4-8f8d-88645cb94dff" />
<img width="1816" height="1112" alt="image" src="https://github.com/user-attachments/assets/d5b50780-54ec-4519-8d85-acd725a10096" />
<img width="1812" height="1062" alt="image" src="https://github.com/user-attachments/assets/0cd46a80-af0d-4845-aa6b-58618fc164c7" />
<img width="1809" height="977" alt="image" src="https://github.com/user-attachments/assets/b3bef271-bed2-405e-a1bb-4c7ac623ea71" />
<img width="1820" height="1118" alt="image" src="https://github.com/user-attachments/assets/8968e8e1-9943-4248-bb56-e2c5c6f775ac" />





