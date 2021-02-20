# gasprice

estimates ethereum gas price based on recent blocks and provides a simple api

## installation

requires python 3.6 or higher and an ethereum full node. If you dont have a full node you can use [Quiknode](https://www.quiknode.io/) or [Infura](https://infura.io/).

```bash
pip3 install -r requirements.txt
```

Make sure you export `ETH_RPC_URL` 

there is an example of systemd service if you want to run it as a service.

## usage

```bash
gasprice

Options:
  -h, --host 127.0.0.1
  -p, --port 8000
  -s, --skip-warmup
```

ethereum rpc url can be set with `ETH_RPC_URL` environment variable (default `http://localhost:8545`).

## api

```json
{
   "health":true,
   "block_number":11799460,
   "slow":137.0,
   "standard":214.459,
   "fast":283.064,
   "instant":311.0,
   "block_time":14.176
}
```


## Install

```
cd /opt
git clone https://github.com/maurodelazeri/eth-gasprices.git
cd eth-gasprices
cp gasprice.service /etc/systemd/system/gasprice.service
systemctl daemon-reload
systemctl start gasprice.service
systemctl status gasprice.service
```

`slow`, `standard`, `fast` and `instant` values represent minimal gas price of the latest 200 blocks. by default slow represents 30% probability, standard is 60%, fast is 90% and instant is 100%.

This project was forked from https://github.com/banteg/gasprice
