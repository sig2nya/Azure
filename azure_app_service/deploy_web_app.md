1. 배포할 대상 dir 생성
```
starwalk7058 [ ~ ]$ ls -ltr
total 0
lrwxrwxrwx 1 starwalk7058 starwalk7058 22 Jul  3 00:00 clouddrive -> /usr/csuser/clouddrive
starwalk7058 [ ~ ]$ mkdir htmlapp
starwalk7058 [ ~ ]$ cd htmlapp
starwalk7058 [ ~/htmlapp ]$ pwd
/home/starwalk7058/htmlapp
```
![image](https://github.com/user-attachments/assets/80dec0e9-f908-4a21-8226-880d9e5d456b)


2. git repo clone 수행
```
starwalk7058 [ ~/htmlapp ]$ git clone https://github.com/Azure-Samples/html-docs-hello-world.git
Cloning into 'html-docs-hello-world'...
remote: Enumerating objects: 50, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 50 (delta 3), reused 2 (delta 2), pack-reused 40 (from 1)
Receiving objects: 100% (50/50), 342.85 KiB | 13.71 MiB/s, done.
Resolving deltas: 100% (9/9), done.
starwalk7058 [ ~/htmlapp ]$ ls -ltr
total 4
drwxr-xr-x 7 starwalk7058 starwalk7058 4096 Jul  3 00:01 html-docs-hello-world
```
![image](https://github.com/user-attachments/assets/b60a293d-ee82-4fb9-8256-61a3286461f4)

3. 리소스 Group 및 App Name 변수 설정
```
starwalk7058 [ ~/htmlapp ]$ resourceGroup=$(az group list --query "[].{id:name}" -o tsv)
starwalk7058 [ ~/htmlapp ]$ appName=az204app$RANDOM
```
![image](https://github.com/user-attachments/assets/6884665c-b949-4d7a-b5bf-a16a90dd446d)

4. 애플리케이션 배포
```
starwalk7058 [ ~/htmlapp ]$ cd html-docs-hello-world/
starwalk7058 [ ~/htmlapp/html-docs-hello-world ]$ az webapp up -g $resourceGroup -n $appName --html
The webapp 'az204app23756' doesn't exist
Creating AppServicePlan 'starwalk7058_asp_8450' or Updating if already exists
Creating webapp 'az204app23756' ...
Configuring default logging for the app, if not already enabled
Creating zip with contents of dir /home/starwalk7058/htmlapp/html-docs-hello-world ...
Getting scm site credentials for zip deployment
Starting zip deployment. This operation can take a while to complete ...
Deployment endpoint responded with status code 202
Polling the status of async deployment. Start Time: 2025-07-03 00:06:19.584813+00:00 UTC
You can launch the app at http://az204app23756.azurewebsites.net
Setting 'az webapp up' default arguments for current directory. Manage defaults with 'az configure --scope local'
--resource-group/-g default: learn-2dfe59ac-c876-487b-bd06-08f88249f8e6
--sku default: F1
--plan/-p default: starwalk7058_asp_8450
--location/-l default: canadacentral
--name/-n default: az204app23756
{
  "URL": "http://az204app23756.azurewebsites.net",
  "appserviceplan": "starwalk7058_asp_8450",
  "location": "canadacentral",
  "name": "az204app23756",
  "os": "Windows",
  "resourcegroup": "learn-2dfe59ac-c876-487b-bd06-08f88249f8e6",
  "runtime_version": "-",
  "runtime_version_detected": "-",
  "sku": "FREE",
  "src_path": "//home//starwalk7058//htmlapp//html-docs-hello-world"
}
```
![image](https://github.com/user-attachments/assets/f49ba2a3-308b-410c-9204-a44a57cf245e)
