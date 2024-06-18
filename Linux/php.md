## install

### ubuntu

#### php 8.2/8.3

```sh
sudo add-apt-repository ppa:ondrej/php

sudo apt-get update

sudo apt-get install -y \
    php8.2 \
    php8.2-bcmath \
    php8.2-cli \
    php8.2-common \
    php8.2-curl \
    php8.2-fpm \
    php8.2-gd \
    php8.2-imagick \
    php8.2-intl \
    php8.2-mbstring \
    php8.2-mcrypt \
    php8.2-mysql \
    php8.2-pgsql \
    php8.2-sqlite3\
    php8.2-tidy \
    php8.2-tokenizer \
    php8.2-xml \
    php8.2-zip
```

---

### debian [bookworm](https://packages.sury.org/php/dists/bookworm)/[bullseye](https://packages.sury.org/php/dists/bullseye)

#### php 8.3

```sh
sudo apt-get install-y software-properties-common lsb-release apt-transport-https ca-certificates

sudo wget "https://packages.sury.org/php/apt.gpg" -O "/etc/apt/trusted.gpg.d/php.gpg"

echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee "/etc/apt/sources.list.d/php.list"

sudo apt update

sudo apt-get install -y \
    php8.3\
    php8.3-bcmath \
    php8.3-cli \
    php8.3-common \
    php8.3-curl \
    php8.3-fpm \
    php8.3-gd \
    php8.3-imagick \
    php8.3-intl \
    php8.3-mbstring \
    php8.3-mcrypt \
    php8.3-mysql \
    php8.3-pgsql \
    php8.3-sqlite3 \
    php8.3-tidy \
    php8.3-tokenizer \
    php8.3-xml \
    php8.3-zip
```
