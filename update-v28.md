
```
cd $HOME
wget https://github.com/Orchestra-Labs/symphony/releases/download/v1.0.4/symphonyd-1.0.4-SNAPSHOT-fad9f314f-linux-amd64.tar.gz
tar -xzf symphonyd-1.0.4-SNAPSHOT-fad9f314f-linux-amd64.tar.gz
chmod +x symphonyd
mkdir -p /root/.symphonyd/cosmovisor/upgrades/v28/bin
cp symphonyd /root/.symphonyd/cosmovisor/upgrades/v28/bin/
chmod +x /root/.symphonyd/cosmovisor/upgrades/v28/bin/symphonyd
```
```
/root/.symphonyd/cosmovisor/upgrades/v28/bin/symphonyd version
```
