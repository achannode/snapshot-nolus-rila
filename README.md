# snapshot-nolus-rila

Snapshots are taken automatically every 6 hours

# Instructions
# 1. Stop the service and reset the data
```sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```
* $HOME bisa juga pakai /root/ atau directory buat install node nya misal /mnt/node/

# 2. Download latest snapshot
```curl -L https://snapshots.achannode.xyz/nolus-testnet/snapshot_latest.tar.lz4 | tar -Ilz4 -xf - -C $HOME/.nolus
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```
* $HOME bisa juga pakai /root/ atau directory buat install node nya misal /mnt/node/

# 3. Restart the service and check the log
```sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```
Atau
```nolusd start / nolusd --home /mnt/node start (apabila directory di /mnt/node)
``` 
jangan lupa untuk run pakai binaries pakai screen lalu ctrl A + D
