# Ansible & Ansible playbook

### Install Ansible <br><br>
- Install Ansbile bisa dilihat di Web Official Ansible<br><br>![1  web ansible](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/e35acf78-a85d-4975-a3d1-6ab794608e7d)<br><br>
- Pertama-tama kita pastikan pip terinstall <br><br>
   ```
   $ python3 -m pip -V
   ```
- bila sudah terinstall pipnya, maka akan menampilkan seperti berikut :<br><br>
   ```        
   $ python3 -m pip -V
   pip 21.0.1 from /usr/lib/python3.9/site-packages/pip (python 3.9)
   ```
- Bila belum terinstall, maka harus terinstall terlebih dahulu penambahan OS Package python3-pip atau menginstall pip yang terbaru dari Otoritas Package Python.<br><br>
   ```
   $ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
   $ python3 get-pip.py --user
   ```
- Berikutnya install Ansible melalui pip<br><br>
   ```
   $ python3 -m pip install --user ansible
   ```
- Setelah terinstall, konfirmasi install Ansible dengan :<br><br>
   ```
   ansible --version |
   ansible-community --version
   ```
   ![2  ansbile --version](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/64b6a39b-550b-4ac1-b416-eba07ef0bca2)<br><br>

### Setup Konfigurasi Ansible <br><br>
- Membuat file konfigurasi Inventory dan ansible.cfg<br><br>![3  nano Inventory dan ansible cfg](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/eae065ba-0d57-43fe-a5da-06fae45251e6)<br><br>![4  nano Inventory](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/86337232-71c4-4cc3-883f-a6e4f765ae33)<br><br>![5  nano ansible cfg](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/3fae3fa3-e217-41b0-acb6-b707b36d847d)<br><br>
### Create User <br><br>
- Pertama buat file create-user.yml. Dan isikan konfigurasi seperti dibawah ini :<br><br>
  ```
  ---
  - become: true
    gather_facts: false
    hosts: all
    tasks:
      - name: "Creating User"
        ansible.builtin.user:
        groups: sudo
        name: "{{username}}"
        password: "{{password}}"
        state: present
        append: yes
        home: /home/({username})
    vars:
      - username: # Fill in your desired username
      - password:  # whois encrypted password
  ```
  ![6  create-user yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/03e387f4-c79f-4c5e-a63c-4b024f4619f0)<br><br>
- Untuk password user harus mengisinya dengan password yang sudah di enkripsi, untuk membuat password yang di enkripsi memerlukan package yang bernama whois. Install whois dan ketikkan password yang akan di enkripsi. Bisa gunakan perintah dibawah ini.<br><br>
  ```
  $ sudo apt install whois
  ```
  ```
  $ mkpasswd --method=sha-256
  ```
  ![7  encyript password](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/8a288363-4a7a-4d52-966c-f6a2f4b3ddb7)<br><br>
- Setelah mendapatkan password yang sudah di enkripsi, copy password tersebut dan tambahkan kedalam file create-user.yml. Setelah itu jalankan file dengan menggunakan ansible playbook.<br><br>![8  ansible-playbook create-user yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/22989726-9309-435a-9ce9-3ae000cb7f36)<br><br>

### Install Docker dan Menjalankan wayshub-frontend melalui Ansible
- Pertama membuat file install-docker.yml dengan parameter kebutuhan user. dan jalankan dengan ansible-playbook.<br><br>![9  cat install-docker yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/c6c343d6-5e6e-4b6f-adde-94dc3edc7917)<br><br>![10  ansible-playbook install-docker yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/041f84ed-2507-4dfc-8c1a-24413b730676)<br><br>
- Kemudian buat file docker-compose.yml.<br><br>![11  docker-compose yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/ea05d08c-c81b-4201-9584-8dad36796c94)<br><br>
- Berikutnya membuat file deploy-wayshub.yml<br><br>![12  deploy-wayshub yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/dd78f25b-4b3f-40f9-bab0-f15b6f85e710)<br><br>
- Dan jalankan dengan ansible-playbook<br><br>![13  ansible-playbook deploy-wayshub yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/48ea747b-f3d9-48bf-a60e-943fb401e9e5)<br><br>
- Result<br><br>![14  haidar studentdumbways my id](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/8a3cb192-f135-4300-984f-9149e81b30de)<br><br>

### Setup Nginx 
- Pertama daftarkan DNS di cloudflare<br><br>![15  cloudflare](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/3e641068-1e23-44d2-99fc-3eb56508f4e2)<br><br>
- Kemudian membuat file untuk install Nginx dan setup reverse proxy di Ansible<br><br>![16  nano nginx yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/18f0098a-e234-42e7-ad3e-043993a1ccea)<br><br>
- Setelah selesai file yang dibuat, lakukan perintah ansible-playbook untuk menjalankannya.<br><br>![17  ansible-playbook nginx yml](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/8a55cde9-34e5-4d9a-947e-78fcb7d674a8)<br><br>




















































































