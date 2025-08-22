

```
sudo apt -q update
sudo apt -qy install curl git jq lz4 build-essential
sudo apt -qy upgrade
sudo apt-get update && apt-get install -y libssl-dev
```
```
sudo apt update
sudo apt install python3.10
sudo apt install python3.10-venv
```
```
cd $HOME
git clone https://github.com/cmancrypto/symphony-oracle-voter.git
```
```
cd symphony-oracle-voter
git checkout v1.0.0
```

NOT: .env dosyasının içini düzenleyin vali ve adresinizi yazın nodun portlarınıda unutmayın. env için `cp .env_sample .env` yazın sonra `nano .env` düzenleyip kaydedin.

```
python3 -m venv venv
```
```
source venv/bin/activate
```
```
pip install -r requirements.txt
```
```
deactivate
```
```
sudo tee /etc/systemd/system/oracle.service > /dev/null << EOF
[Unit]
Description=Symphony Oracle
After=network.target

[Service]
# Environment variables
Environment="SYMPHONYD_PATH=$(which symphonyd)"
Environment="PYTHON_ENV=production"
Environment="LOG_LEVEL=INFO"
Environment="DEBUG=false"

# Service configuration
Type=simple
User=root
WorkingDirectory=/root/symphony-oracle-voter/
ExecStart=/root/symphony-oracle-voter/venv/bin/python3 -u /root/symphony-oracle-voter/main.py
Restart=always
RestartSec=3
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
EOF
```
```
sudo systemctl daemon-reload
sudo systemctl enable oracle.service
sudo systemctl start oracle.service
```
```
sudo journalctl -u oracle -f -o cat
```
### oracle kaydı.
NOT: vali adresinizi kullanıcaksanız onun adresi yazılacak. cüzdan adınıda sölememe gerek yok herhalde.
```
symphonyd tx oracle set-feeder symphony1xxx --from wallet --chain-id symphony-1 --fees 2500note
```
```
sudo journalctl -u oracle.service -n 50 --no-pager
```
