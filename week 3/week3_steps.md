# Week 3 Steps

## 1. Open Terminal
```bash
cd ..
# Output: /home
cd ..
# Output: /
```
## 2. Move to HTML Folder
```bash
cd var
# Output: /var
cd www
# Output: /var/www
cd html
# Output: /var/www/html
```
## 3. Check for 'DVWA' Folder/Directory
```bash
ls
```
- If it is present already
  ```bash
  sudo mv DVWA [your_folder_name]
  ```
- Else, clone the git repo
```bash
  sudo git clone https://github.com/digininja/DVWA.git
# Output: Cloning into DVWA ....
sudo mv DVWA [your_folder_name]
```
## 4. Move to Your New Created Folder
(Assuming new folder name is 'dvwa3')
```bash
cd dvwa3
```
## 5. Move to Config Folder Under dvwa3
```bash
cd config
sudo cp config.inc.php.dist config.inc.php
sudo nano config.inc.php
```
Change the Following in config.inc.php
```plaintext
database = 'dvwa3'
user = 'admin'
password = 'admin'
```
- Press Ctrl+S to save
- Press Ctrl+X to exit nano mode

## 6. Running SQL Commands
```bash
sudo service mysql start
sudo mysql -u root -p
```
### Enter the password which you provided earlier in config.inc.php
### In our case, it is: admin
Next run the following commands one by one
```sql
create database dvwa3;
create user 'dvwa3'@'127.0.0.1' identified by 'admin';
grant all on dvwa3.* to 'admin'@'127.0.0.1';
exit
```
## 7. Configuring Apache2 Server
Perform the following commands one after the other
```bash
cd /etc
cd php
cd 8.2
ls
cd apache2
sudo nano php.ini
```
### Change the Following in php.ini
```plaintext
allow_url_fopen = On
allow_url_include = On
```
- Press Ctrl+S to save
- Press Ctrl+X to exit nano mode

## 8. Start the Server
```bash
sudo service apache2 start
```
### 9. Open Firefox
Go to `http://127.0.0.1/dvwa3` to check if the application is running or not.
