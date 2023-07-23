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
- Membuat file konfigurasi Inventory dan ansible.cfg<br><br>![3  nano Inventory dan ansible cfg](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/eae065ba-0d57-43fe-a5da-06fae45251e6)<br><br>![4  nano Inventory](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/86337232-71c4-4cc3-883f-a6e4f765ae33)<br><br>![5  nano ansible cfg](https://github.com/darblietz/devops17-dw--M-Yusuf-Haidar-/assets/98991080/3fae3fa3-e217-41b0-acb6-b707b36d847d)













































































