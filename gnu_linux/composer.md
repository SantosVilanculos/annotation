# Composer

## Instalation

1. Prerequisites

   - php >= 8.2

2. Run the command bellow on a terminal

   ```sh
   cd ~/Downloads
   php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
   php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
   php composer-setup.php
   php -r "unlink('composer-setup.php');"
   sudo mv composer.phar /usr/local/bin/composer
   sudo chmod +x /usr/local/bin/composer
   ```

3. Add to path, by adding to the end of the archive (.bashrc, .zshrc or equivalent)

   ```sh
   export PATH="$PATH:$HOME/.config/composer/vendor/bin"
   ```
