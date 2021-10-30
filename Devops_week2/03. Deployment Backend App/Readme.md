# Deployment Backend App
1. Clone backend app https://github.com/sgnd/dumbplay-backend.
![Backend App Deployment](screenshot/gambar0.jpg) <br />
2. Buka Readme file dalam backend app.
![Backend App Deployment](screenshot/gambar1.jpg) <br />

3. Kemudian jalankan requirementnya.   
   - Install nodejs
   - copy .env-copy .env
   - Import database dengan sequelize.
   ![Backend App Deployment](screenshot/gambar1a.jpg) <br />
   - Edit Config.json file sesuaikan database username, password, nama database dan host addressnya.
    ![Backend App Deployment](screenshot/gambar1b.jpg) <br />

4. Login ke database instance untuk membuat databasenya dulu.
5. Login mysql ``sudo mysql -u root -p``.
6. Masukkan password mysql.
7. Buat database ``mysql> create database myapp``.
![Backend App Deployment](screenshot/gambar1c.jpg) <br />

### Import Database dengan Sequelize ###
1. Install sequelize-cli ``npm install --save-dev sequelize-cli``.
![Backend App Deployment](screenshot/gambar2.jpg) <br />
2. Kemudian install sequelize ``npm install --save sequelize``.
![Backend App Deployment](screenshot/gambar2a.jpg) <br />
3. Install mysql2 ``npm install mysql2 -g``.
4. Migrate database ``sequelize db:migrate`` atau ``node_modules/.bin/sequelize db:migrate``.
![Backend App Deployment](screenshot/gambar2c.jpg) <br />
5. Run backend apps dengan pm2 ``pm2 start ecosystem.config.json``.
![Backend App Deployment](screenshot/gambar3.jpg) <br />
