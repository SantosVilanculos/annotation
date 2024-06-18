# MySQL

## Installation

```sh
sudo apt install mysql-server
```

## Change root user`s password

1. Open MySQL Prompt

   ```sh
   sudo mysql
   ```

2. Then run the command bellow

   ```sql
   ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';
   ```

3. Finally exit MySQL Prompt

   ```sql
   exit;
   ```
