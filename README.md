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
**Install MySQL**  
```
sudo dnf -y install https://dev.mysql.com/get/mysql80-community-release-fc35-1.noarch.rpm
sudo dnf -y install mysql-community-server --nogpgcheck
sudo systemctl enable --now mysqld.service
```
**Grab the temporary MySQL root password. You will use this for the next step**  
```
sudo grep 'A temporary password' /var/log/mysqld.log | tail -1
```
**Install MySQL using the password from above**  
```
sudo mysql_secure_installation --password=$(sudo grep 'A temporary password' /var/log/mysqld.log | tail -1 | cut -d: -f4 | tail --bytes 13)
```
**Set MySQL password validation to low**  
```
echo 'skip-validate_password=1' | sudo tee -a /etc/my.cnf
````
**Install MySQL**  
```
sudo mysql_secure_installation --password=
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
