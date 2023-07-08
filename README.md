# Task Cloud Computing

1. Buat VM untuk Appserver <br/><br/>![1](https://github.com/darblietz/ppt/assets/98991080/ac43818f-864f-4bbb-b4a1-5d184c469463)
<br/><br/>
2. lakukan sudo apt update terlebih dahulu <br/><br/>![2](https://github.com/darblietz/ppt/assets/98991080/cf4f5907-3e43-4516-9001-efeb0d3f961e)<br/><br/>
3. dan install node.js dan exec bash dan nvm install 14<br/><br/>![3](https://github.com/darblietz/ppt/assets/98991080/e31bab2c-e5d7-446e-9fd4-2497ff8b6372)![4](https://github.com/darblietz/ppt/assets/98991080/e079b840-b0e4-4909-9878-c90a90eb7fed)<br>![5](https://github.com/darblietz/ppt/assets/98991080/c06c1183-e2dc-43c2-9c5b-341a16f216da)<br/><br/>
4. Setelah itu git clone frontend dan backend <br/><br/>![6](https://github.com/darblietz/ppt/assets/98991080/425c3288-1fb3-4c63-9ead-c8e0e0da0b6f)<br>![7](https://github.com/darblietz/ppt/assets/98991080/45bff896-4be7-451c-8fa5-eddd7d79e703)<br/><br/>
5.  Berikutnya penginstallan Node Packet Manager berupa node_modules di folder Frontend dan Backend.<br/><br/>![8](https://github.com/darblietz/ppt/assets/98991080/0359d360-5ffd-462e-98e8-ac8c12f80046)
<br>![9](https://github.com/darblietz/ppt/assets/98991080/9d462b9e-f9a5-41b1-89ef-abcbd864d7ff)<br/><br/>
6. Setelah install, lakukan test aplikasi bisa berjalan atau tidak dengan perintah npm start <br/><br/>![13](https://github.com/darblietz/ppt/assets/98991080/394e4330-b883-461f-a29c-442f3677666c)<br>![12](https://github.com/darblietz/ppt/assets/98991080/ae9fdcea-6a7e-41c4-890f-6f16e2eb5208)<br>![11](https://github.com/darblietz/ppt/assets/98991080/c2399ed5-1b16-4e7f-bcd3-cbe8ed010ab2)<br>![10](https://github.com/darblietz/ppt/assets/98991080/fd2a32f2-ebe8-4d5b-93a0-5a640f279ba3)<br><br/><br/>
7. Berikutnya install mySQL untuk membuat database dan membuat user di mySQL.<br/><br/>![14](https://github.com/darblietz/ppt/assets/98991080/1a3092a5-3704-4848-b94b-df7821034130)<br/><br/>
8. Setelah install masuk ke mySQL dengan perintah sudo mysql -u root -p.<br/><br/>![15](https://github.com/darblietz/ppt/assets/98991080/499497f6-3d18-4eb8-b009-1c871e8f455e)<br/><br/>
9. Sesudah itu kita membuat ALTER USER root untuk dipassword supaya menjamin keamanannya. ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password  by 'password';<br/><br/>![16](https://github.com/darblietz/ppt/assets/98991080/c846960a-b39d-432f-bfdd-d586b2301b68)<br/><br/> 
10. Selanjutnya membuat user dengan nama kita sendiri di mySQL dengan perintah CREATE USER 'rommel'@'%' IDENTIFIED BY 'password';<br/><br/>![17](https://github.com/darblietz/ppt/assets/98991080/fd16311a-426f-4031-bc05-d9d3966a816a)<br/><br/>
11. Sebelum kita membuat database di -u rommel maka kita harus melakukan perintah  GRANT ALL PRIVILEGES ON *.* TO 'rommel'@'%';<br/><br/>![18](https://github.com/darblietz/ppt/assets/98991080/ae7060b7-e2ee-42d4-830f-4fc319f7972a)<br/><br/>

### Install mysql_secure_installation
1. Install mySQL securenya <br/><br/>![19](https://github.com/darblietz/ppt/assets/98991080/219d6255-cc2f-4b42-a0f2-95b0c9e27bf8)<br>![19-1](https://github.com/darblietz/ppt/assets/98991080/9b9c09f6-09ca-4c7b-ac64-6ef71fb9e1b0)<br/><br/>

### Koneksikan Frontend ke Backend
1. Ubah baseURL menjadi api.haidar.studentdumbways.my.id di api.js<br/><br/>![20](https://github.com/darblietz/ppt/assets/98991080/a954ec65-3310-4e39-899f-40d9d422dd76)<br>![21](https://github.com/darblietz/ppt/assets/98991080/7cef9e9c-cf98-4516-a854-d2d0b2d94162)<br/><br/>

### Koneksikan Backend ke mySQL
1. Untuk koneksinya dengan masuk ke folder wayshub-backend lalu cd config dan nano config.json<br/><br/>![22](https://github.com/darblietz/ppt/assets/98991080/460f208b-d699-4928-bd47-cb734c9fd50b)<br>![23](https://github.com/darblietz/ppt/assets/98991080/c6dbc236-1a74-4c17-a57e-4da8e149c2eb)<br/><br/>

### Sequelize
1.  Pertama install terlebih dahulu sequelizenya difolder wayshub-backend dengan perintah berikut npm install -g sequelize-cli <br/><br/>![24](https://github.com/darblietz/ppt/assets/98991080/7be83665-dd3a-4128-974b-c19908d0844d)<br/><br/>
2. Setelah itu membuat database mySQL dengan perintah sequelize db:create dan setelah dibuat, lakukan untuk memigrasikan data backend ke mySQL dengan perintah sequelize db:migrate. <br/><br/>![25](https://github.com/darblietz/ppt/assets/98991080/d4148899-1f97-43c9-aa3f-259e84a9b270)<br>![26](https://github.com/darblietz/ppt/assets/98991080/d64db539-dade-45b9-98a7-db884260db3e)
<br/><br/>
3. Kemudian untuk memastikan apakah migrasi sudah berhasil atau tidak dengan masuk dulu ke mySQL : sudo mysql -u rommel -p, dan perintah SHOW DATABASES; lalu USE db-wayshub; dan SHOW TABLES.<br/><br/>![27](https://github.com/darblietz/ppt/assets/98991080/e501feb1-c905-4583-b20a-5808fe90a07a)<br/><br/>

### Deploy aplikasi menggunakan PM2 
1. Pertama-tama install PM2 terlebih<br/><br/>![28](https://github.com/darblietz/ppt/assets/98991080/8e842f7a-4833-45e5-ad1a-4a4021fb8109)<br/><br/>
2. Berikutnya lakukan perintah pm2 ecosystem simple difolder frontend dan backend.<br/><br/>![29](https://github.com/darblietz/ppt/assets/98991080/eda5b067-ecae-47df-903c-3bf003b7e6f9)<br>![30](https://github.com/darblietz/ppt/assets/98991080/8154d4f3-1f5f-4b24-b41a-f7dc9ef65a84)<br/><br/>
3. Lalu edit script di ecosystem.config.js menjadi npm start, disetiap directory frontend dan backend.<br/><br/>![31](https://github.com/darblietz/ppt/assets/98991080/54ed610d-7fb4-4806-83f7-d750e35a6ac1)<br>![32](https://github.com/darblietz/ppt/assets/98991080/a19b221a-f4cd-4772-ab2d-5f2eeec905ca)<br/><br/>
4. <br/><br/><br/><br/>

### Gateway Nginx
1. Daftarkan DNS diCloudflare dengan IP Public Gateway<br/><br/>![33](https://github.com/darblietz/ppt/assets/98991080/25aa8bd1-f68c-4f21-af34-1a74b939562d)<br/><br/>
2. lalu install nginx di server gateway<br/><br/>![34](https://github.com/darblietz/ppt/assets/98991080/232deb69-ff6e-4876-b7e6-7ad10d8e78a3)<br/><br/>
3. setelah itu membuat 2 file pengaturan Reverse Proxy di /etc/nginx/dumbways. dengan nama frontend.conf dan backend.conf<br/><br/>![35](https://github.com/darblietz/ppt/assets/98991080/697d21ff-c777-4510-9132-8ca9dad6d3d3)<br>![37](https://github.com/darblietz/ppt/assets/98991080/3be5029d-1a52-452a-9d9f-15bac888c25e)<br>![36](https://github.com/darblietz/ppt/assets/98991080/96e9c78e-5e6a-48d4-922d-de1b56d8c89c)<br/><br/>
4. berikutnya masuk ke file nginx.conf untuk menambahkan include/etc/nginx/dumbways/*; <br/><br/>![39](https://github.com/darblietz/ppt/assets/98991080/5adbc8ee-2a8b-4caf-860e-af23f78cb7b9)<br>![38](https://github.com/darblietz/ppt/assets/98991080/1c84ac01-cfe2-468e-91ae-04a8c1adb657)<br/><br/>
5. habis itu lakukan sudo nginx -t untuk mengetest syntax configurasi nginx.conf sudah berhasil atau belum. <br/><br/>![40](https://github.com/darblietz/ppt/assets/98991080/1fbfc317-9213-431e-b540-bd9c5637f800)<br/><br/>
6. lakukan reload dan restart nginx <br/><br/>![41](https://github.com/darblietz/ppt/assets/98991080/ff571ddf-22c1-4d9a-af22-67eae9f1a606)<br/><br/>

# TEST DNS 

- Frontend<br>![42](https://github.com/darblietz/ppt/assets/98991080/d48fe591-4cc3-4e6a-8836-5d3e24cb6f92)<br>
- Backend<br>![43](https://github.com/darblietz/ppt/assets/98991080/fbfe6863-5b6e-4139-891b-a22ff820ce37)
- Login <br><br>
![45](https://github.com/darblietz/ppt/assets/98991080/6f03d9df-8744-44b8-9872-a70f4ee99add)<br>
![44](https://github.com/darblietz/ppt/assets/98991080/55e57b01-0f44-4b2f-bd74-937deedad34b)




