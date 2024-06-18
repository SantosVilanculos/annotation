# Mailpit

## Installation

```sh
wget https://github.com/axllent/mailpit/releases/download/v1.18.3/mailpit-linux-amd64.tar.gz
tar -x -f mailpit-linux-amd64.tar.gz -C /tmp
sudo mv /tmp/mailpit /usr/local/bin
sudo chmod +x /usr/local/bin/mailpit
```

| NETWORK PROTOCOL | PORT         |
| ---------------- | ------------ |
| HTTP             | 0.0.0.0:8025 |
| SMTP             | 0.0.0.0:1025 |
