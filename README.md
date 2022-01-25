# Installing Denodo Tutorial on Fedora 35

**Tutorial Landing Page**  
```
https://community.denodo.com/tutorials/browse/basics/index 
```
**Download Denodo Express**  
You'll have to register for an account and then you can download the Denodo Express product and license File. 
You can download Denodo Express from:
```
https://community.denodo.com/express/download/
```

**Install MySQL**
```
sudo dnf -y install https://dev.mysql.com/get/mysql80-community-release-fc35-1.noarch.rpm
sudo dnf install mysql-community-server --nogpgcheck
sudo systemctl enable --now mysqld.service
```
**Grab the temporary MySQL root password. You will use this for the next step**
```
sudo grep 'A temporary password' /var/log/mysqld.log | tail -1
```
**Install MySQL**
```
sudo mysql_secure_installation
```
**Log into MySQL as root user**
```
mysql -u root -p
```
**Set MySQL password policy to low**
```
set global validate_password.policy=LOW;
```
**Run the Schema.sql script**
```
source <path to>/Schema.sql;
```
**Install mysql_connector-java and mysql-workbench-community**
```
sudo dnf install ./mysql-connector-java-8.0.28-1.fc35.noarch.rpm, mysql-workbench-community --nogpgcheck
```
