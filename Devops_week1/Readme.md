# VMware-Install-Ubuntu

#### Install Ubuntu Server 18.x with VMware ####

1. Download VMware, dan juga Ubuntu server iso
2. Install VMware, kemudian jalankan VMware
3. Create virtual machine baru <br />
![Create virtual machine](screenshot/gambar0.jpg)
4. Pilih "Use ISO image:" Browse ubuntu server iso yang telah di download pada step 1, kemudian Next.
![Create virtual machine](screenshot/gambar1.jpg)
5. Pada "Personalize Linux" input nama, username, dan password. kemudian Next
![Create virtual machine](screenshot/gambar2.jpg)
6. Kemudian beri nama pada virtual machine serta tentukan lokasi filenya. Klik Next.
![Create virtual machine](screenshot/gambar3.jpg)
7. Pada "Disk Size" beri sebesar 20 Gb (recommended size untuk ubuntu) kemudian pilih "Split virtual disk into mulItiple files"
![Create virtual machine](screenshot/gambar4.jpg)
8. Selanjutnya Custom spec virtual machine sesuai kebutuhan, misal 2 CPU cores, memory 4096 Mb, network adapter Bridge. Klik Finish
![Create virtual machine](screenshot/gambar5.jpg)
9. Masuk pada proses instalasi os ubuntu
10. Pilih bahasa "English"
![Install Ubuntu-server](screenshot/gambar5a.jpg)
11. Konfigurasi keyboard set default. 
![Install Ubuntu-server](screenshot/gambar5b.jpg)
12. Setting network connections bisa DHCP (ip dinamis) ataupun manual (ip static), sesuai kebutuhan. Untuk sementara bisa menggunakan DCHP.
![Install Ubuntu-server](screenshot/gambar5c.jpg)
13. Configure Proxy, jika ingin menggunakan proxy address bisa diisi ataupun dikosongkan saja.
![Install Ubuntu-server](screenshot/gambar5d.jpg)
14. Ubuntu archive mirror menggunakan yang default saja.
![Install Ubuntu-server](screenshot/gambar5e.jpg)

#### Create swap memory and root partition ####
Proses pembuatan swap dan root partition dilakukan saat proses instalasi ubuntu server di vmware <br />

1. Selanjutnya, atur storage configuration, pilih "Custom storage layout", kemudian "Done"
![Install Ubuntu-server](screenshot/gambar6.jpg)
2. Pilih device /dev/sda , kemudian Add GPT partition
![Install Ubuntu-server](screenshot/gambar7.jpg)
3. Misal akan dibuat 1 Gb swap, pada field Size input 1G.
4. Pada format ubah menjadi swap, kemudian Create
![Install Ubuntu-server](screenshot/gambar7a.jpg)
5. Swap sudah dibuat.
6. Pilih /dev/sda, kemudian Add GPT partition
7. Pada field "Size" input sisa disk yaitu 18.997G
8. Pilih format ext4
9. Untuk Mount pilih "/" untuk root, kemudian Create
![Install Ubuntu-server](screenshot/gambar7b.jpg) <br />
![Install Ubuntu-server](screenshot/gambar7c.jpg)
10. Kemudian konfirmasi pilih Continue
![Install Ubuntu-server](screenshot/gambar7d.jpg)
11. Isi User profile seperti nama, nama server, username, dan password untuk sebgai informasi login ke ubuntu nanti
![Install Ubuntu-server](screenshot/gambar8.jpg)
12. Selanjutnya install ssh, pilih atau centang Install OpenSSH server.
![Install Ubuntu-server](screenshot/gambar9.jpg)
13. Featured Server bisa dipilih sesuai kebutuhan, jika tidak ada kosongkan saja. Next
![Install Ubuntu-server](screenshot/gambar10.jpg)
14. Tunggu proses instalasi ubuntu server selesai.
![Install Ubuntu-server](screenshot/gambar11.jpg)
15. Setelah proses instalasi selesai reboot vm kemudian login menggunakan akun yang telah dibuat pada step 11.
![Install Ubuntu-server](screenshot/gambar12.jpg)
16. Ubuntu di vmware sudah dapat di operasikan.
![Install Ubuntu-server](screenshot/gambar13.jpg)

#### Local server can connect to the internet ####
1. Setelah proses instalasi ubuntu di vm selesai.
2. Login ke vm ubuntu server 
3. Untuk mengecek apakah vm ada koneksi internet bisa dilakukan perintah ping, misal ping www.google.com
![Install Ubuntu-server](screenshot/gambar13.jpg)


 
