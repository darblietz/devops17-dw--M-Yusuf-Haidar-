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

- Pada saat pertama kali akan diminta password generate yang sudah disiapkan oleh Jenkins. letaknya di `Please use the following password to proceed to installation`.<br/><br/><img width="1120" alt="2   password jenkins" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/0b4c1ae1-f9d7-4b89-b6b5-9204ba1bc402"><br/><img width="1096" alt="3  password jenkins 2" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/27267954-a1f4-47f8-bcb5-11a55a769994"><br/><br/>

- Setelah memasukkan password, pada instalasi plugin pilih `recommend plugin`. Setelah plugin selesai maka akan diarahkan untuk `Create First Admin User` dan `Instance Configuration`.<br/><br/><img width="996" alt="4  getting started" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/a23050f0-d963-4daa-8aed-8055052b2436"><br/><img width="862" alt="5  Instance Configuration" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/6d29f7d3-11f6-4c88-8c3a-0bdf435e927f"><br/><br/>

- Jenkins siap digunakan<br/><br/>
<img width="1120" alt="6  welcome to jenkins" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/b0e66e81-2342-4cc9-bdd4-3b255d4b70e7"><br/><br/>


## Koneksikan Jenkins dengan Server
- Dengan mengkonfigurasi Manage Credentials dan koneksikan Jenkins dengan VPS server dengan menambahkan ssh-keygen.<br/><br/>
  > - ***public key*** dimasukan di dalam ***authorized keys***
  > - ***private key*** diletakan pada user ***Credentials***.<br/><br/>
  



























