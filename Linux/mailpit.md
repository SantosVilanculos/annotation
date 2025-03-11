## install

```sh
wget https://github.com/axllent/mailpit/releases/download/v1.21.1/mailpit-linux-amd64.tar.gz -O "./mailpit-linux-amd64.tar.gz"
tar -xf ./mailpit-linux-amd64.tar.gz
sudo mv ./mailpit /usr/local/bin
sudo chmod +x /usr/local/bin/mailpit
```

```sh
cat <<'EOF' | sudo tee /etc/systemd/system/mailpit.service
[Unit]
Description=An email testing tool capturing emails from your application during development.

[Service]
ExecStart=/usr/local/bin/mailpit
Restart=always
User=root
Group=root

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl daemon-reload
sudo systemctl enable mailpit.service
sudo systemctl start mailpit.service
```

## endpoint

| protocol |host   | port  |
| -------- |-------|-------|
| http     |`0.0.0.0`| `8025` |
| smtp     |`0.0.0.0`| `1025` |
