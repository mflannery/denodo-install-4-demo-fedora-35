# Installing Denodo Tutorial on Fedora 35
**Tutorial Landing Page**  
```
https://community.denodo.com/tutorials/browse/basics/index 
```
**Download Denodo Express**  
You'll have to register for an account and then you can download the Denodo Express product and the license File. 
You can download Denodo Express and the license file from:
```
https://community.denodo.com/express/download/
```
**Make the denodo_express directory to install denodo into**  
```
mkdir denodo_express
```
**Download the tutorial files into the denodo_tutorial directory**  
```
wget -P ~/denodo_tutorial https://community.denodo.com/tutorials/files/denodo_tutorial_files.zip
```
**Unzip the tutorial files**  
```
unzip ~/denodo_tutorial/denodo_tutorial_files.zip -d ~/denodo_tutorial
```
**Download and start mysqld**  
```
sudo dnf -y install https://dev.mysql.com/get/mysql80-community-release-fc35-1.noarch.rpm
sudo dnf -y install mysql-community-server mysql-connector-java mysql-workbench-community --nogpgcheck
sudo systemctl enable --now mysqld.service
```
**Install MySQL**  
```
sudo mysql_secure_installation --password=$(sudo grep 'A temporary password' /var/log/mysqld.log | tail -1 | cut -d: -f4 | tail --bytes 13) --use-default
```
**Set MySQL password validation to low and require length to be 4 characters or more**  
```
echo 'validate_password.policy=LOW' | sudo tee -a /etc/my.cnf
echo 'validate_password.length=4' | sudo tee -a /etc/my.cnf
```
**Restart mysqld**  
```
sudo systemctl restart mysqld.service
```
**Log into MySQL as root user using the password created when mysql_secure_installation was run**  
```
mysql -u root -p
```
**If a less complex root password is desired**  
```
alter user 'root'@'localhost' identified by 'something-easier';
```
**Automatically logging into mysql**  
If you want to automatically log into mysql, create a ~/.my.cnf file that looks like this
```
[client]
user = root
password = something-easier
```
**Run the Schema.sql script**
```
mysql -u root -p < path/to/Schema.sql
```
**Install Denodo Express**  
Download denodo express to your server and follow the instructions for installation.
