# Plume

## Origin document

- https://docs.plumenetwork.xyz/plume/getting-started/running-a-node
- https://github.com/plumenetwork/node-config

## Incentive Testnet Form

- Join Plume's Incentivized Testnet Waitlist https://deform.plumenetwork.xyz/testnet?referral=6fGPVeJwOSrw

## Current Plume Testnet Node

> Currently, the Plume team maintains all the testnet infrastructure, so we are not looking for operators to run any testnet nodes. If you would still like to run a node yourself for free and without any promise of future fees, rewards, or potential airdrops.

### 0. Prepare

Docker

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
rm -rf get-docker.sh

sudo docker --version
```

### 1. Run docker compose

```bash
git clone https://github.com/plumenetwork/node-config.git ~/node-config
cd ~/node-config

export PWD=$(pwd)

sudo docker compose up -d
```

change `--parent-chain.connection.url=` at `docker-compose.yml` if you want to use your RPC (Sepolia).

### 2. Misc

#### Logs

Check logs

```bash
cd ~/node-config

sudo docker compose logs -f

# Ctrl-C for exit
```

#### Update

```bash
cd ~/node-config

git fetch --prune
git pull

sudo docker compose down
sudo docker compose up
```
