# Introduction
The Client-Server Architecture is a fundamental design pattern in networks where multiple clients (users or applications0 interact with a centralized server that provides resources, services, or data
## Project SetUp
### EC2 Setup:
- Instance A (Server): MySQL Server installed
- Instance B (Client): MySQL Client installed
<img width="1246" height="206" alt="Screenshot 2025-09-03 at 22 03 49" src="https://github.com/user-attachments/assets/bd19095e-a751-4740-8b81-b2e40db49bc5" />


### Install MySQL-Server
- SSH into instance A
```
sudo apt update
```
```
sudo apt install mysql-server -y
```
```
sudo systemctl enable mysql
```
```
sudo mysql
```
```
CREATE USER 'remote_user'@'%' IDENTIFIED BY 'StrongPassword123!';
```
```
GRANT ALL PRIVILEGES ON *.* TO 'remote_user'@'%' WITH GRANT OPTION;
```
```
FLUSH PRIVILEGES;
```
<img width="800" height="503" alt="Screenshot 2025-09-03 at 21 52 06" src="https://github.com/user-attachments/assets/6c2ee8d4-a183-4479-b61c-2c2940452ff1" />

Add a security gruop rule to allow access from MySQL-Client security group ID
<img width="1477" height="353" alt="Screenshot 2025-09-03 at 22 05 17" src="https://github.com/user-attachments/assets/3822d874-aef9-4bca-8790-3fb73ccb60c8" />


### Install MySQL-Client
- SSH into instance B
```
sudo apt update
```
```
sudo apt install -y mysql-client
```
```
mysql -u remote_user -h <PRIVATE_IP_OF_INSTANCE_A> -p
```
```
SHOW DATABASES;
```
<img width="847" height="876" alt="Screenshot 2025-09-03 at 22 01 31" src="https://github.com/user-attachments/assets/e97531f9-746f-4551-a413-3bcaf4d800ec" />




