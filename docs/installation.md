# Install Ollama

## Download and extract the ARM64-specific package
```shell
curl -L https://ollama.com/download/ollama-linux-arm64.tgz -o ollama-linux-arm64.tgz
tar -C /usr -xzf ollama-linux-arm64.tgz
```

## Adding Ollama as a startup service (recommended)
```shell
# Create a user and group for Ollama
useradd -r -s /bin/false -U -m -d /usr/share/ollama ollama
usermod -a -G ollama $(whoami)

# Create a service file in /etc/systemd/system/ollama.service
cat > /etc/systemd/system/ollama.service << 'EOF'
[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/bin/ollama serve
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment="PATH=$PATH"
Environment="OLLAMA_HOST=0.0.0.0"

[Install]
WantedBy=multi-user.target
EOF


# start the service
systemctl daemon-reload
systemctl enable ollama

systemctl start ollama
systemctl status ollama
```