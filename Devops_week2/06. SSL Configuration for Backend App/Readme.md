# SSL Configuration for Backend App

### Arahkan frontend api.js ke backend app ###
1. Login ke frontend instance.
2. Masuk ke folder ``frontend/config``.
![SSL Config](screenshot/gambar0.jpg) <br />
3. Edit file ``api.js`` arahkan ``baseURL: 'https://api.ogak.onlinecamp.id:5000/api/v1``.
![SSL Config](screenshot/gambar1.jpg) <br />
4. Restart app.


### SSL Configuration ###
1. Login ke instance gateway.
2. Update dan upgrade sistem.
3. Install certbot untuk backend.
4. Perintahnya ``sudo certbot -d api.ogak.onlinecamp.id``.
![SSL Config](screenshot/gambar3.jpg) <br />
5. Reverse proxy otomatis akan ditambahkan generated syntax dari certbot.
![SSL Config](screenshot/gambar3a.jpg) <br />
