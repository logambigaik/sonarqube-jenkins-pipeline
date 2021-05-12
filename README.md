# sonarqube-setup

# Prerequisite:

        # Install Java
        # Install sonarqube
            wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.0.43852.zip
                  

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

