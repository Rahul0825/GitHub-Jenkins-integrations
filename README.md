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

     

