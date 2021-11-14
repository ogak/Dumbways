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
   host_key_checking = false
   timeout = 60
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
1. Buat file yml ``setup-databse.yml``
2. Buat task update dan upgrade system
3. Buat task install mysql-server
4. Berikut adalah yml codenya:
   ```
   ---
   - name: Setup Database
     hosts: 52.207.158.23
     become: true
     tasks:
       - name: Update system
         apt:
           update_cache: yes
       - name: Upgrade system
         apt:
           upgrade: dist

       - name: Install Mysql-Server
         apt:
           name: mysql-server
           state: present

   ```
5. Setup manual untuk secure installation, config database lainnya seperti grant akses user-host dan config mysqld.cnf "bind-address = 0.0.0.0"

### Ansible-Playbook Install docker
1. Buat file yml untuk instalasi docker di server ``setup-docker.yml``
2. Masukkan kode berikut
   ```
   ---
   - name: Setup Docker & Docker Compose
     hosts: 
       - 44.198.105.77
       - 54.92.233.212
       - 204.236.226.148
     become: true
     tasks:
       - name: Update system
         apt:
           update_cache: yes

       - name: Upgrade system
         apt:
           upgrade: dist

       - name: Setup repository
         shell: "sudo apt-get install ca-certificates curl gnupg lsb-release"
         args:
           executable: /bin/bash

       - name: Add docker GPG key
         apt_key:
           url: https://download.docker.com/linux/ubuntu/gpg
           state: present

       - name: Add docker repository
         apt_repository:
           repo: deb https://download.docker.com/linux/ubuntu focal stable
           state: present

       - name: Update system
         apt:
           update_cache: yes

       - name: Install docker engine
         apt:
           name: "{{item}}"
           state: latest
           update_cache: yes
         loop:
           - docker-ce
           - docker-ce-cli
           - containerd.io

       - name: Install stable release docker compose
         shell: "sudo curl -L 'https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)' -o /usr/local/bin/docker-compose"
         args:
           executable: /bin/bash

       - name: Apply executable permission to the binary
         shell: "sudo chmod +x /usr/local/bin/docker-compose"
         args:
           executable: /bin/bash
   
   ```

3. Save kemudian execute command ``ansible-playbook setup-docker.yml``
4. Tunggu hingga proses instalasi selesai


