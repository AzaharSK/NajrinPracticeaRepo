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
01-hello-world-rest-api$ mvn azure-webapp:config
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
Enter index to use: 1
Define value for appName(Default: 01-hello-world-rest-api-1771053610324): 
Define value for resourceGroup(Default: 01-hello-world-rest-api-1771053610324-rg): 
Define value for region(Default: southindia): 
Define value for pricingTier(Default: P1v2): 
1. b1
2. b2
3. b3
4. d1
5. f1
6. p1v2 [*]
7. p2v2
8. p3v2
9. s1
10. s2
11. s3
Enter index to use: 5
Please confirm webapp properties
AppName : 01-hello-world-rest-api-1771053610324
ResourceGroup : 01-hello-world-rest-api-1771053610324-rg
Region : southindia
PricingTier : Free_F1
OS : Linux
RuntimeStack : JAVA 8-jre8
Deploy to slot : false
Confirm (Y/N)? : Y
[INFO] Saving configuration to pom.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  04:28 min
[INFO] Finished at: 2026-02-14T13:15:17+05:30
[INFO] ------------------------------------------------------------------------
Feb 14, 2026 1:15:17 PM com.microsoft.applicationinsights.core.dependencies.http.impl.execchain.RetryExec execute
INFO: I/O exception (java.net.SocketException) caught when processing request to {s}->https://dc.services.visualstudio.com:443: Socket closed
Feb 14, 2026 1:15:17 PM com.microsoft.applicationinsights.core.dependencies.http.impl.execchain.RetryExec execute
INFO: I/O exception (java.net.SocketException) caught when processing request to {s}->https://rt.services.visualstudio.com:443: Socket closed
Feb 14, 2026 1:15:17 PM com.microsoft.applicationinsights.core.dependencies.http.impl.execchain.RetryExec execute
INFO: I/O exception (java.net.SocketException) caught when processing request to {s}->https://dc.services.visualstudio.com:443: Socket closed
```
