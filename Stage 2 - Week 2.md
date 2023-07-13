# Kelompok 2
- Arif Prastiyo
- Mochamad Yusuf Haidar
- Ihkam Audito

### Server Requirements <br/><br/>
![appserver](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/1f19b03f-67fc-48cd-8a9a-dddc8d665e97)<br/>
![gateway](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/6525a585-43c9-4138-962c-14224f5958c2)<br/><br/>

### Install Docker <br/><br/>
- Pertama-tama, setelah membuat servernya install Docker dengan perintah berikut<br/><br/>
  ```
  sudo apt-get update
  sudo apt-get install ca-certificates curl gnupg
  ```
  <img width="590" alt="1  Sudo apt update" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/6346258c-3248-41bb-a65f-07172fcef17a"><br/>
  <img width="659" alt="2  sudo apt-get install ca-certificates" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/387862a3-7b74-40ca-9fde-79dcd7487f15"><br/><br/>
  ```
  sudo install -m 0755 -d /etc/apt/keyrings
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
  sudo chmod a+r /etc/apt/keyrings/docker.gpg
  ```
  <img width="1026" alt="3  sudo install keyrings" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/a9ef201d-c965-41a6-8647-b9a145086ac9">


