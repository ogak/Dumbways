# Setup Server with Ansible

### Requirements:
- Buat repository di github untuk menyimpan file-file ansible


### Install Ansible in Ubuntu
1. Konfigurasi PPA
   ```
   sudo apt update
   sudo apt install software-properties-common
   sudo add-apt-repository --yes --update ppa:ansible/ansible
   ```
2. Install Ansible ``sudo apt install ansible``
3. Konfirmasi installasi ``ansible all -m ping --ask-pass``

### Define host server
1. Buat directory untuk menyimpan file-file ansible
2. Masuk ke dalam folder buat file  ``hosts`` untuk menyimpan hostname server <br />

   ```
   #webserver
   34.192.151.138 ansible_user=ubuntu
   #apps
   44.198.105.77 ansible_user=ubuntu
   #db
   52.207.158.23 ansible_user=ubuntu
   #CI/CD
   54.92.233.212 ansible_user=ubuntu
   #Monitoring
   204.236.226.148 ansible_user=ubuntu
    ```
3. Ping hosts untuk memastikan koneksi ansible dan server berfungsi ``ansible all --key-file ~/path-to/server-aws-key.pem -i hosts -m ping``

![Setup Server with Ansible](screenshot/gambar0.jpg)

### Setup Custom ansible.cfg file
1. Buat file ``ansible.cfg`` di work directory
2. Masukkan config berikut
   ```
   [defaults]
   inventory = hosts 
   private_key_file = ~/Downloads/server-aws-key.pem
   host_key_checking = False
   ```
3. Save config

### Ansible-Playbook Setup nginx server
1. Buat file yml ``setup-nginx.yml``
2. Buat task update dan upgrade system
3. Buat task install nginx
4. Berikut adalah yml codenya:
   ```
   ---
   - name: Setup Nginx
     hosts: 34.192.151.138
     become: true
     tasks:
       - name: Update system
         apt:
           update_cache: yes
       - name: Upgrade system
         apt:
           upgrade: dist

       - name: Install Nginx
         apt:
           name: nginx
           state: present
           update_cache: yes
   ```
5. Save
6. Execute perintah ansible-playbook ``ansible-playbook setup-nginx.yml``

![Setup Server with Ansible](screenshot/gambar1a.jpg)

7. Check nginx dengan URL

![Setup Server with Ansible](screenshot/gambar1b.jpg)


### Ansible-Playbook Setup database server
1. 
