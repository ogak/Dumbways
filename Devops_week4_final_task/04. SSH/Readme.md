# SSH

### SSH Key for access the server without username & password
1. Generate authorized key
2. ``ssh-keygen -y -f Downloads/aws-key.pem``

![04](screenshot/gambar2a.jpg)

3. Masuk ke server/instance
4. Buat file dan folder  ``.ssh/authorized_key``
5. Edit ``authorized_key``, copy paste generated key dari step 2
6. Simpan
7. Disable PasswordAuthentication pada sshd_config set ke "no", restart sshd service

![04](screenshot/gambar2.jpg)

### SSH Key for access the git without username & password
1. Generate SSH key ``ssh-keygen -t rsa -C "ogak@dumbways"
2. Add ssh key yang telah dibuat ``ssh-add ~/.ssh/id_rsa``

![04](screenshot/gambar1a.jpg)

3. Login ke github
4. Tambahkan ssh key yang telah dibuat pada step 1

![04](screenshot/gambar1b.jpg)

5. Kemudian test koneksi ke github

![04](screenshot/gambar1c.jpg)




