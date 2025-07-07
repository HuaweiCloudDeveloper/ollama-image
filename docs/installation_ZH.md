# 安装Ollama

## 下载并解压ARM64专用包
```shell
curl -L https://ollama.com/download/ollama-linux-arm64.tgz -o ollama-linux-arm64.tgz
tar -C /usr -xzf ollama-linux-arm64.tgz
```

## 将Ollama添加为开机自启服务（推荐）
```shell
# 为Ollama创建专用用户和用户组
useradd -r -s /bin/false -U -m -d /usr/share/ollama ollama
usermod -a -G ollama $(whoami)

# 在/etc/systemd/system/目录下创建ollama.service服务文件
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

# 启动服务
systemctl daemon-reload
systemctl enable ollama

systemctl start ollama
systemctl status ollama
```