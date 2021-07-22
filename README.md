# GitHub-Jenkins-integrations
github to jenkins integration by webhook

# Install jenkins on CentOs
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo <br />
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key <br />
sudo yum upgrade <br />
sudo yum install jenkins java-11-openjdk-devel<br />
sudo systemctl daemon-reload<br />
sudo systemctl start jenkins<br />
sudo systemctl status jenkins<br />
sudo yum install git<br />

firewall settings………..<br />
YOURPORT=8080<br />
PERM="--permanent"<br />
SERV="$PERM --service=jenkins"<br />

firewall-cmd $PERM --new-service=jenkins<br />
firewall-cmd $SERV --set-short="Jenkins ports"<br />
firewall-cmd $SERV --set-description="Jenkins port exceptions"<br />
firewall-cmd $SERV --add-port=$YOURPORT/tcp<br />
firewall-cmd $PERM --add-service=jenkins<br />
firewall-cmd --zone=public --add-service=http --permanent<br/>
firewall-cmd –reload<br/>

## Configure Jenkins
### (1). go to browser and search hostip:8080 <br/>

![image](https://user-images.githubusercontent.com/63436839/126533977-459509d8-2fb3-4d6a-9a74-89d6930dc032.png)<br/>
### (2). cat /var/lib/jenkins/secrets/initialAdminPassword<br/>
###      copy key: ff8fb74c86bd4d03bf143c60e5dc9367<br/>

![image](https://user-images.githubusercontent.com/63436839/126535047-d2e7a4d5-9c3d-4987-98d5-b83a4255db3b.png)<br/>
### (3). select install suggested plugins<br/>
![image](https://user-images.githubusercontent.com/63436839/126535797-ed76b3fe-bbec-48ab-b86c-0150700baedf.png)<br/>
### (4). Enter basic details<br/>

![image](https://user-images.githubusercontent.com/63436839/126536146-3b26d039-79b4-4928-9357-82530c1f6f7a.png)<br/>
### (5). save and finish.
![image](https://user-images.githubusercontent.com/63436839/126536416-e52ae100-f96f-4c32-8b04-dcea905fedcc.png)<br/>
![image](https://user-images.githubusercontent.com/63436839/126536470-53af5362-9ab0-44ec-868f-430ed63f98b0.png)<br/>

     
# Generate Token.

### (1). Click you name (upper-right corner).<br/>
![image](https://user-images.githubusercontent.com/63436839/126586454-a082a0e7-9a9b-4ec6-8b5d-5c69796f9f3e.png)<br/>
### (2). Click Configure (left-side menu).<br/>
![image](https://user-images.githubusercontent.com/63436839/126586611-59c9176f-8a79-448c-af8c-bbe5070adf3f.png)<br/>
### (3). Use "Add new Token" button to generate a new one then name it.<br/>
![image](https://user-images.githubusercontent.com/63436839/126586633-d5c67810-aaa0-4365-98ab-55d11bc53a38.png)<br/>
### (4). You must copy the token when you generate it as you cannot view the token afterwards.<br/>
![image](https://user-images.githubusercontent.com/63436839/126586731-222e782a-15f1-4dbd-b3d9-56f43629584a.png)<br/>
### (5). Revoke old tokens when no longer needed.<br/>
![image](https://user-images.githubusercontent.com/63436839/126586796-e123c876-76c1-453a-89d6-dee3964ed5a2.png)<br/>
### (6). Token save on notpad<br/>
![image](https://user-images.githubusercontent.com/63436839/126586812-8d944ea0-5378-4dec-913c-25c43791b635.png)<br/>

# New Build Job in Jenkins

### 1) Login to Jenkins.
![image](https://user-images.githubusercontent.com/63436839/126587614-aa781e57-a8e8-473b-92e3-5dbac28bd7d2.png)
### 2) Create New Item.
![image](https://user-images.githubusercontent.com/63436839/126587635-76b42239-2859-4428-8ef8-16916e764a45.png)

### 3) Enter Item details.
![image](https://user-images.githubusercontent.com/63436839/126587661-a94d4493-c38b-4b03-8ee2-4c1a890617c5.png)

### 4) Enter Project details.
![image](https://user-images.githubusercontent.com/63436839/126587672-9ccc46ab-9753-4f89-b9fe-e548d51434f0.png)

### 5) Enter repository URL.
![image](https://user-images.githubusercontent.com/63436839/126587680-1a9f8f78-91e4-4a11-b1e0-f6f82f40407a.png)

####   Under Source Code Management, Enter your repository URL. We have a test repository located at Github.
### 6) Tweak the settings.
####   Click on "Add build step"
### 7) Build Triggers.
####    Select [ GitHub hook trigger for GITScm polling.]
![image](https://user-images.githubusercontent.com/63436839/126588369-3c4901d0-a275-4ae1-8dcf-e65def0cbd91.png)

### 8) Save the project.
####    When you have entered all the data,
####    Click Apply
####    Save the project.
### 9) Build Source code.
![image](https://user-images.githubusercontent.com/63436839/126587799-9576fd5e-c73d-4fcd-8c17-9cf91aa0a354.png)

### 10) Check the status.
![image](https://user-images.githubusercontent.com/63436839/126587824-8f23b4ee-19af-4f03-a035-3321facaab75.png)

### 11) See the console output.
![image](https://user-images.githubusercontent.com/63436839/126587857-ef5fd0ae-edc4-4f2c-8253-8e7932fe03c2.png)


# GitHub Configuration
On Github repository config to Jenkins
Set token and webhook , web trigger hook

### (1). click on repository.<br/>
![image](https://user-images.githubusercontent.com/63436839/126588828-a7e7fd3e-e960-4258-aff6-c8ca89137d57.png)
### (2). Click on repository Settings
![image](https://user-images.githubusercontent.com/63436839/126589150-ab6836bd-4d68-4e74-ad97-fc2985c70f99.png)
### (3). click on WebHook and Add webhook.
![image](https://user-images.githubusercontent.com/63436839/126589896-e72d527e-d141-4a33-b610-afbf885ffd7f.png)
### (4). payload URL:  http://{jenkins_URL}/github-webhook/
###      Contant type: application/json
###      Secret: type jenkins Token
###      Add WebHook
![image](https://user-images.githubusercontent.com/63436839/126590228-3f484ca7-6e85-4117-a892-cbb5c946a163.png)



