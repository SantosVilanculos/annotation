## install

```sh
sudo apt-get install mariadb-server
```

## configuration

### password

```sh
sudo mysql -u root
```

```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';
exit;
```

### expose

```sh
sudo sed -i 's/^bind-address\s*=\s*127\.0\.0\.1/bind-address = 0.0.0.0/' /etc/mysql/mariadb.conf.d/50-server.cnf

sudo systemctl restart mariadb
```
