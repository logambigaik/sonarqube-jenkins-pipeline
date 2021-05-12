# sonarqube-setup

# Prerequisite:

        # Install Java
        # Install sonarqube
            wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.0.43852.zip
        # Install Jenkins
            wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo && sudo rpm --import http://pkg.jenkins.io/redhat-stable/jenkins.io.key  && sudo yum install jenkins -y && sudo service jenkins start

                  
# Step 1: Sonarqube setup:

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


# Step 2: Jenkins Setup:

![image](https://user-images.githubusercontent.com/54719289/118026408-a7e18200-b358-11eb-8c2d-100fa0416c7b.png)

 >> Change Password as admin123



# Step 3: Install Maven 

# Step 4 Create Pipeline Project in jenkinsAdd Maven script with tools -pipeline syntax:

![image](https://user-images.githubusercontent.com/54719289/118027992-779ae300-b35a-11eb-871b-1fe5f090a044.png)

Pipeline Syntax:
===============
```
tool name: 'maven', type: 'maven'
```

Declarative pipeline
====================

pipeline{
    agent any
    stages{
        stage('SCM'){
            steps{
            }
         }
       }
    }

Scripted pipeline:
==================


Scripted pipeline is very useful when you play with paramter values.

![image](https://user-images.githubusercontent.com/54719289/118032399-8d5ed700-b35f-11eb-8e6a-f1906c65887c.png)

In this scenario, scripted pipeline helps lot.



```
node {
    def MAVEN_HOME = tool name: 'maven', type: 'maven'
    def MAVEN_CMD = "${MAVEN_HOME}/bin/mvn"
}

```
![image](https://user-images.githubusercontent.com/54719289/118029381-05c39900-b35c-11eb-987b-6b8cc12ad6a6.png)

```
node {
    def MAVEN_HOME = tool name: 'maven', type: 'maven'
    def MAVEN_CMD = "${MAVEN_HOME}/bin/mvn"
    
    stage('SCM'){
        git branch: 'main', url: 'https://github.com/logambigaik/springboo-without-db.git'
        
    }
    stage('Build Artifact'){
        sh "${MAVEN_CMD} clean package"
    }
}

```

![image](https://user-images.githubusercontent.com/54719289/118030653-7cad6180-b35d-11eb-89f0-10e35f34a7d4.png)

```


Pipelune
