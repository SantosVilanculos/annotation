# NVM

## Installation

1. Run the command bellow in a terminal

   ```sh
   wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
   ```

2. Add to path, by adding to the end of the archive (.bashrc, .zshrc or equivalent)

   ```sh
   export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
   [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
   ```

## Install Node

```sh
    nvm install node # "node" is an alias for the latest version
    nvm install 22 # or 16.3.0, 12.22.1, etc
    nvm ls-remote #You can list available versions using ls-remote:
    nvm use node #And then in any new shell just use the installed version:
```
