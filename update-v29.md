
```
cd $HOME
wget https://github.com/Orchestra-Labs/symphony/releases/download/v1.0.6/symphonyd-1.0.6-SNAPSHOT-daecefe87-linux-amd64.tar.gz
tar -xzf symphonyd-1.0.6-SNAPSHOT-daecefe87-linux-amd64.tar.gz
chmod +x symphonyd
mkdir -p /root/.symphonyd/cosmovisor/upgrades/v29/bin
cp symphonyd /root/.symphonyd/cosmovisor/upgrades/v29/bin/
chmod +x /root/.symphonyd/cosmovisor/upgrades/v29/bin/symphonyd
```
```
/root/.symphonyd/cosmovisor/upgrades/v29/bin/symphonyd version
```
