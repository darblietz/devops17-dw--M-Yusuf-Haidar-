# CI/CD : Jenkins

### Jenkins on Top Docker<br/><br/>
- Pertama install terlebih dahulu Docker di server Jenkins dan membuat user root commander docker.<br/><br/>
  ```
  sudo usermod -aG docker (user)
  sudo su (user)
  docker version
  ```
  <img width="1118" alt="1  docker version" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/c69d3b78-c65e-45a3-b7d8-f7fe26a2b814"><br/><br/>

- Lalu membuat Docker-compose dan menjalakannya.<br/><br/>
  ```
  version: '3.8'
  services:
     jenkins:
        image: jenkins/jenkins:lts-jdk11
        container_name: jenkins
        restart: always
        privileged: true
        user: root
        ports:
           - 8080:8080
           - 50000:50000 
        volumes:
           - ~/jenkins:/var/jenkins_home
  ```
  ```
  docker compose up -d
  ```
  ![docker -compose](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/64e44265-e02f-4863-a185-5b47b13159c3)<br/><br/>
