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
2. <br/><br/><br/><br/>
3. <br/><br/><br/><br/>
16. <br/><br/><br/><br/>
17. <br/><br/><br/><br/>
18. <br/><br/><br/><br/>
19. <br/><br/><br/><br/>
20. <br/><br/><br/><br/>
