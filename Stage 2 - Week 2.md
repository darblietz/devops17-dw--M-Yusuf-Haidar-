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
  <img width="1026" alt="3  sudo install keyrings" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/a9ef201d-c965-41a6-8647-b9a145086ac9"><br/><br/>
  ```
  echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  ```
  <img width="919" alt="4  echo " src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/4d1c676f-b815-4138-96ec-07966216e494"><br/><br/>
  ```
  sudo apt-get update
  ```
  <img width="604" alt="5  sudo apt-get update" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/8ed503a1-55c4-4bec-8514-94059875de48"><br/><br/>
  ```
  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```
  <img width="992" alt="6  sudo install container" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/f7efb9fe-4852-4c42-b2d2-6401e278b469"><br/><br/>

- Berikutnya melakukan Setup root commander docker untuk memberikan akses user untuk menjalankan perintah tanpa menggunakan "Sudo".<br/><br/>
  ```
  sudo usermod -aG docker (user)
  sudo su (user)
  docker version
  ```
  <img width="563" alt="7  sudo usermod" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/a5ae40f3-9464-4744-adf9-2f12d829dd2c"><br/><img width="499" alt="8  sudo su docker version" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/794e5ee2-4bb2-48f8-8273-5402fa615972"><br/><br/>

# Deploy Applikasi on Top Docker 

### Frontend
- git clone repository wayshub-frontend<br/><br/>
  ```
  git clone https://github.com/dumbwaysdev/wayshub-frontend
  ```
  <img width="736" alt="9  git clone frontend" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/4bbcfd3c-25bc-489a-8f8b-bb5172297847"><br/><br/>
- Lakukan integrasikan Frontend dan Backendnya, lalu membuat Dockerfile.<br/><br/>
  ```
  nano api.js
  nano Dockerfile
  ```
  <img width="548" alt="10  nano api js" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/a6159122-3a7b-4818-850c-a534fee68e2b"><br/>![11  nano Dockerfile](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/5edb5813-93de-4e80-8d62-6034637d3a76)<br/><br/><img width="745" alt="12  api js" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/58fbc7ca-1d50-4dac-bb0d-8394168f8294"><br/><br/>![13  cat Dockerfile](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/d3d2f222-e6ea-4520-b80b-6da8934dc512)

### Database mySQL
- Membuat dan menjalankan mySQL melalui Docker compose<br/><br/>
![14  nano compose-mysql](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/aab79ab1-347d-4803-be6b-d2d276b37fda)<br/><br/><img width="914" alt="15  docker compose -f" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/0ac163c7-9204-4285-bd87-2eeed7aa1b34"><br/><br/>
- Lalu membuat user database<br/><br/>
  <img width="617" alt="16  docker exec" src="https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/4ee99484-5f8d-4916-aaa3-5fab436b9ae5">

### Backend
- git clone repository wayshub-backend<br/><br/>
  ```
  git clone https://github.com/dumbwaysdev/wayshub-backend
  ```
  ![17  git clone backend](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/5e68826e-4300-4026-a2d0-8252b8e5631a)







































  




