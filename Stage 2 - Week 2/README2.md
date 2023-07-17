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
  > - ***private key*** diletakan pada user ***Credentials***
  <br/><br/>
  
  ![7  credentials](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/0fef2926-58c5-4c2e-b403-fb36a1560adf)<br/><br/>![8  Global credentials](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/9d0e5dd9-d9f3-45ac-9c39-838480108d39)<br/><br/>![9  Global credentials](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/3e04b6d6-b6fc-43a2-a62a-c707143c949e)<br/><br/>![10  ssh id rsa](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/fb21c5b9-d620-40d6-aa81-c35e9fafa39b)<br/><br/>
- Kemudian tambahkan plugin ssh pada jenkins agar bisa menggunakan koneksi ssh.<br/><br/>![SSH Agent Plugin](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/3c4a8c40-88d9-4492-b4da-3ca3dc2fc8e5)
<br/><br/>

## Membuat Jenkinsfile Frontend dan Backend

- Untuk membuat pipeline di butuhkan file bernama Jenkinsfile

**Jenkinsfile wasyhub-frontend**<br/>
```
def branch = "main"
def repo = "git@github.com:DitoIhkam/wayshub-frontend.git"
def cred = "wayshub"
def dir = "~/wayshub-frontend"
def server = "app-server@103.172.204.253"
def imagename = "wayshub-fe"
def dockerusername = "kelompok2"

pipeline {
    agent any

    stages {
        stage('Pull From Repository') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        git remote add origin ${repo} || git remote set-url origin ${repo}
                        git pull origin ${branch}
                        exit
                        EOF
                    """
                }
            }
        }

    stage('Dockerize') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker build -t ${imagename}:latest .
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Deploy Docker') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        docker run -d -p 3000:3000 --name="${imagename}"  ${imagename}:latest
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
               sshagent([cred]) {
			    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
				    docker tag ${imagename}:latest ${dockerusername}/${imagename}:latest
				    docker image push ${dockerusername}/${imagename}:latest
				    docker image rm ${dockerusername}/${imagename}:latest
				    docker image rm ${imagename}:latest
				    exit
                    EOF
			"""
		        }
            }
        }
    }
}
```
**Jenkinsfile wayshub-backend**
```
def branch = "main"
def repo = "git@github.com:DitoIhkam/wayshub-backend.git"
def cred = "wayshub"
def dir = "~/wayshub-backend"
def server = "app-server@103.172.204.253"
def imagename = "wayshub-be"
def dockerusername = "kelompok2"

pipeline {
    agent any

    stages {
        stage('Pull From Repository') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        git remote add origin ${repo} || git remote set-url origin ${repo}
                        git pull origin ${branch}
                        exit
                        EOF
                    """
                }
            }
        }

    stage('Dockerize') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker build -t ${imagename}:latest .
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Deploy Docker') {
            steps {
                sshagent([cred]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                        cd ${dir}
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        docker run -d -p 3000:3000 --name="${imagename}"  ${imagename}:latest
                        docker container stop ${imagename}
                        docker container rm ${imagename}
                        exit
                        EOF
                    """
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
               sshagent([cred]) {
			    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
				    docker tag ${imagename}:latest ${dockerusername}/${imagename}:latest
				    docker image push ${dockerusername}/${imagename}:latest
				    docker image rm ${dockerusername}/${imagename}:latest
				    docker image rm ${imagename}:latest
				    exit
                    EOF
			"""
		        }
            }
        }
    }
}
```
<br/><br/>
## Membuat Pipeline 

- Pilih Pipeline dan beri nama sesuai aplikasi.
- Masukkan ssh url github, branch dan dll. Hal ini dikarenakan setiap mengalami perubahan, penambahan pada Jenkinsfile harus di add, commit dan push ke akun github yang sudah di setting di server.
- Kemudian save. Jika Jenkinsfile sudah di tambahkan ke dalam repository. bisa langsung menekan build now. ketika di build bisa melihat error di bagian logs sesuai dengan stage yg di jalankan.<br/><br/>
![11  Buat Pipeline](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/2e09f777-8df2-41ec-b7cc-6c71b730d74a)<br/>![12  General](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/24e04a63-52be-488c-974b-b2c69c10a545)<br/>![13  Configurasi Pipeline](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/0f9d8b00-2e87-4ee6-86fd-5c6303103742)<br/><br/>![14  Result Pipeline](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/79b7af57-aed1-4058-b847-9105f5f40f29)<br/><br/>
- Berikut Result aplikasi wayshub-frontend dan wayshub-backend yang telah berhasil di push ke docker hub.<br/><br/>![17  hub docker](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/4433ada8-9356-42e0-86a8-9c7289d446ba)<br/><br/>

## Konfigurasi Reverse Proxy
- Membuat Reverse Proxy dan serta certbot sertifikasi pada aplikasi Jenkins.<br/><br/>![15  cloudflare](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/c8635e77-2b73-4cc0-bd82-6e7d187b1aa0)<br/>![16  cat jenkins conf](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/dfe8c571-6d41-4086-b85a-d74737539779)




  



























