# CI/CD Jenkins

### Install Jenkins Docker
1. Login ssh server jenkins
2. Buat file docker compose
   ```
    version: '3.9'
    services:
      jenkins:
        image: jenkins/jenkins:lts-jdk11
        ports:
          - 8080:8080
          - 50000:50000
        privileged: true
        user: root
        container_name: jenkins
        volumes:
          - ~/jenkins:/var/jenkins_home
          - /var/run/docker.sock:/var/run/docker.sock
          - /usr/local/bin/docker:/usr/local/bin/docker
   ```
3. Run ``docker-compose up -d``

![08](screenshot/gambar0.jpg) <br />

### Setup jenkins
1. Install plugin publish over ssh dan slack notification (optional)

![08](screenshot/gambar2.jpg) <br />

2. Setup Publish over ssh

![08](screenshot/gambar2a.jpg) <br />

### Setup jenkins job frontend
1. Buat freestyle project
2. Configure, setup source code management

![08](screenshot/gambar3.jpg) <br />

2. Setup build triggers

![08](screenshot/gambar3a.jpg) <br />

3. Setup build command 

![08](screenshot/gambar3b.jpg) <br />

4. Save

### Setup jenkins job backend
1. Buat freestyle project
2. Configure, setup source code management

![08](screenshot/gambar4.jpg) <br />

2. Setup build triggers

![08](screenshot/gambar3a.jpg) <br />

3. Setup build command 

![08](screenshot/gambar4a.jpg) <br />

4. Save

5. Test build

![08](screenshot/gambar5.jpg) <br />


![08](screenshot/gambar5a.jpg) <br />



