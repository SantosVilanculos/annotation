## install

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

## configuration

### .bashenv/.zshenv

```sh
if [ -s "$HOME/.nvm/nvm.sh" ]; then
  source "$HOME/.nvm/nvm.sh"
fi

if [ -s "$HOME/.nvm/bash_completion" ]; then
  source "$HOME/.nvm/bash_completion"
fi
```

## node

```sh
nvm install 22
nvm use 22
```
