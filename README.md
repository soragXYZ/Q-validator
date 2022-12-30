# Q validator Installation Guide

## Official Documentation
https://docs.qtestnet.org/how-to-setup-validator/

## Prerequisites
```
apt-get update \
&& apt-get install -y git \
docker-compose
```


## Q Installation

### Clone repo
```
git clone https://gitlab.com/q-dev/testnet-public-tools
```

### Generate keypair
```
cd testnet-public-tools/testnet-validator
mkdir keystore
echo <password> > keystore/pwd.txt
docker-compose run --rm --entrypoint "geth account new --datadir=/data --password=/data/keystore/pwd.txt" testnet-validator-node
```

Save private key !!!
  
### Get token here

Use your newly generated address  
https://faucet.qtestnet.org/

### Configure set up
```
cp .env.example .env
nano .env
```

Modify ADDRESS and IP fields, without Ox for address  

```
nano config.json
```

Modify ADDRESS and PASSWORD fields, without Ox for address, and same password than before  

### Put stake in the validator contract
Download keyfile in /keystore then import it to Metamask.  
Go to https://hq.qtestnet.org/validator-staking  
Stake to ranking 4Q, then join validator ranking

### Add to leaderboard
```
nano docker-compose.yaml
```
Add after "geth":  
"--ethstats=<Your_Validator_Name>:qstats-testnet@stats.qtestnet.org",



### Start / stop fullnode
```
docker-compose up -d
```
```
docker compose down
```

### Get fullnode container logs
```
docker-compose logs -f --tail "100"
```

Then wait for the validator to sync up

## Troubleshoot

to do

## Start as a service
```
to do
```
