# Docker
## Kelompok 2
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
  ![17  git clone backend](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/5e68826e-4300-4026-a2d0-8252b8e5631a)<br/><br/>
  
- Lalu integrasikan Backend dan Database, setelah itu membuat Dockerfile.<br/><br/>
![18  nano config json](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/d2786684-68c2-4586-bec4-d20fa8d8c62c)<br/>![19  config json](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/f97b07bb-cb3a-4228-a872-45942ad40bd5)<br/>![20  nano Dockerfile backend](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/26841dde-a6dd-42a5-ab44-a0febdf0e372)<br/><br/>
### Docker Compose
- Membuat dan menjalankan Docker compose<br/><br/>
![21  nano docker-compose](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/f510beb9-1b9a-4cc6-90e9-da18d8611700)<br/><br/>
- Lalu perintahkan command berikut :
  ```
  docker compose up -d
  ```
  ![22  docker compose up -d](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/f1675940-9b7a-4efe-b60e-c439560f0d5f)

### Docker Push Images
- Lakukan login Docker.Hub didalam terminal dengan perintah berikut :
  ```
  docker login
  ```
  ![23  Docker login](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/358ec8d2-ab99-4f11-b9d5-fe8e9b8339b3) 

- Kemudian memberikan tag dan push pada image.
  ```
  docker tag app-server-frontend erwinrommel97/wayshub-frontend
  ```
  ```
  docker push erwinrommel97/wayshub-frontend
  ```
  ![24  docker push](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/2bfed7c4-d1e2-460d-b543-5c78fee7f086)<br/>![25  Result docker push](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/59edac12-1493-49dc-ba4f-5b339acf04cf)

### Konfigurasi Reverse Proxy<br/><br/>

- Membuat Reverse Proxy dan serta Certbot Sertifikasi pada aplikasi wayshub-frontend dan wayshub-backend.<br/><br/>
![26  Cat Reverse Proxy](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/526f4398-f087-4457-a94b-189ce47c46e0)<br/>![27  dns cloudflare](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/1fbac4a7-918b-4c80-8e3c-7b8d1bcdda98)<br/>![28  SS Frontend](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/acb189a9-64ad-49a5-8296-4acedd6d7022)<br/>![29  SS Login](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/98ee04f1-ff96-43cf-8294-d731d6985a20)<br/>![30  SS Backend](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/d76b8fd1-e0db-46be-bb1f-35f4fbeafee7)










































  
