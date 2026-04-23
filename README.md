
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
