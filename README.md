
# 🚀 OptimAI-CLI-Node Node Setup Guide (Linux / Ubuntu)

## 1. Check & Install Docker

First, check if Docker is already installed:
```
command -v docker >/dev/null 2>&1 || (curl -fsSL https://get.docker.com -o get-docker.sh && sudo sh get-docker.sh)
```
## 2. Install OptimAI CLI
```
# Download and rename to optimai-cli
curl -L https://cli-node.optimai.network/optimai_cli_ubuntu -o optimai-cli

# Make executable and install to PATH
chmod +x optimai-cli
sudo mv optimai-cli /usr/local/bin/optimai-cli
```
## 3. Login - Legacy (email/password)
```
optimai-cli auth login --legacy
```
## 4. Create systemd Service (Auto Start)
```
sudo tee /etc/systemd/system/optimai.service > /dev/null <<EOF
[Unit]
Description=OptimAI Node Service
After=network.target docker.service
Requires=docker.service

[Service]
User=root
WorkingDirectory=/root
ExecStart=/usr/local/bin/optimai-cli node start
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
EOF
```
## 5. Enable & Start Service
```
sudo systemctl daemon-reload
sudo systemctl enable optimai
sudo systemctl start optimai
```
Status:
```
sudo systemctl status optimai
```
View logs:
```
journalctl -u optimai -f
```
<img width="1487" height="604" alt="logs-optimai" src="https://github.com/user-attachments/assets/fb79af1c-8d7b-4a38-a169-7e2246db1e7b" />

Restart:
```
sudo systemctl restart optimai
```
Stop:
```
sudo systemctl stop optimai
```
✅ Quick Summary

Install Docker (if needed)

Install optimai-cli

Login

Start node

Configure systemd for auto-start
