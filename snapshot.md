Instructions

Stop the service and reset the data



sudo systemctl stop nolusd


cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup


rm -rf $HOME/.nolus/data


Download latest snapshot


curl -O http://86.48.16.205/nolus/nolus-rila_snapshot_latest.tar.lz4


tar -I lz4 -xf nolus-rila_snapshot_latest.tar.lz4 -C $HOME/.nolus


mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json


Restart the service and check the log



sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
