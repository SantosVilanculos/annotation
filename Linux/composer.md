## required

- php>=8.2

## install/update

```sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'.PHP_EOL; } else { echo 'Installer corrupt'.PHP_EOL; unlink('composer-setup.php'); exit(1); }"
php composer-setup.php --filename="composer"
php -r "unlink('composer-setup.php');"

sudo chmod +x "./composer"
sudo mv "./composer" "/usr/local/bin/composer"
```

## configuration

### .bashenv/.zshenv

```sh
export PATH="$PATH:$HOME/.config/composer/vendor/bin"
```

```sh
composer config --global github-oauth.github.com <token>
```
