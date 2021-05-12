# sonarqube-setup

# Prerequisite:

        # Install Java
        # Install sonarqube
            wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.0.43852.zip
        # Install Jenkins
            wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo && sudo rpm --import http://pkg.jenkins.io/redhat-stable/jenkins.io.key  && sudo yum install jenkins -y && sudo service jenkins start

                  

# Check the log if its failed, change the owner with R option (-R is for chaging ownership to all directories under sonarqube)

```  chown ec2-user:ec2-user sonarqube-8.9.0.43852 -R ```

![image](https://user-images.githubusercontent.com/54719289/118014256-e8d29a00-b34a-11eb-87d6-9daf888a6952.png)

![image](https://user-images.githubusercontent.com/54719289/118013738-5b8f4580-b34a-11eb-90ad-6b2d1390baa5.png)

![image](https://user-images.githubusercontent.com/54719289/118017606-baef5480-b34e-11eb-81c4-0c5aa6e7f75f.png)


# Update RUN_AS_USER =ec2-user in sonar.sh

![image](https://user-images.githubusercontent.com/54719289/118020740-5afaad00-b352-11eb-93cd-652246db8cb9.png)

![image](https://user-images.githubusercontent.com/54719289/118024004-1709a700-b356-11eb-9589-317e25708162.png)

# Default username & Password:

```
        USername : admin
        Password : admin
```


# Jenkins Setup:

![image](https://user-images.githubusercontent.com/54719289/118026408-a7e18200-b358-11eb-8c2d-100fa0416c7b.png)

# Change Password as admin123

# Create Pipeline project:

# Add Maven script with tools -pipeline syntax:

![image](https://user-images.githubusercontent.com/54719289/118027992-779ae300-b35a-11eb-871b-1fe5f090a044.png)

Pipeline Syntax:
===============
```
tool name: 'maven', type: 'maven'
```

Script:
======
```
node {
    def MAVEN_HOME = tool name: 'maven', type: 'maven'
    def MAVEN_CMD = "${MAVEN_HOME}/bin/mvn"
}

```
