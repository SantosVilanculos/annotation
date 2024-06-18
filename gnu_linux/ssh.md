```sh
if [ ! -d "$HOME/.ssh" ];
    then mkdir "$HOME/.ssh"
fi

cd "$HOME/.ssh"

ssh-keygen -t rsa -b 4096 -C "95357132+SantosVilanculos@users.noreply.github.com"

eval "$(ssh-agent -s)"
```

```sh
ssh-add ~/.ssh/id_ed25519
```
