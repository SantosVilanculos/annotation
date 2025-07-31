## required

```sh
sudo apt-get install -y \
 build-essential \
 libffi-dev \
 libreadline-dev \
 libssl-dev \
 zlib1g-dev \
 tk-dev
```

## recommended

```sh
sudo apt-get install -y \
 libbz2-dev \
 liblzma-dev \
 libsqlite3-dev
```

##  install

```sh
 curl https://pyenv.run | bash
```

## configuration

### .bashenv/.zshenv

```sh
if [ -d "$HOME/.pyenv/bin" ]; then
  export PATH="$PATH:$HOME/.pyenv/bin"

  eval "$(pyenv init -)"
  eval "$(pyenv virtualenv-init -)"
fi
```

## python

```sh
pyenv install 3.12.9
pyenv global 3.12.9
```
