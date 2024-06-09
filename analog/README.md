# Analog

## Install steps

## 0. Dependencies

### 0.1 Docker

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
rm -rf get-docker.sh
```

### 0.2 Packages

```bash
sudo apt install curl jq -y
```

## 1. Analog Timechain

Start

```bash
mkdir ~/timechain-data
export NAME="p10node" # change it
sudo docker run -d --name timechain -p 9944:9944 -p 30303:30303 -v ~/timechain-data:/data analoglabs/timechain --base-path /data --unsafe-rpc-external --rpc-methods=Unsafe --name=${NAME} --telemetry-url="wss://telemetry.analog.one/submit 9"
```

## 2. Check logs

```bash
sudo docker logs -f timechain
```

Ctrl + C to quit watch logs

## 3. Create validator

### 3.1 Faucet

- Go to https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.testnet.analog.one#/accounts
- Get your address
- Faucet at channel https://discord.com/channels/860069399627825163/1139090696175886376 with format: `!faucet <address>`

### 3.2 Add Stash

Run on your server:

```bash
curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "author_rotateKeys", "params":[]}' http://localhost:9944
```

You will see a result like that:

```json
{
  "jsonrpc": "2.0",
  "result": "<data>",
  "id": 1
}
```

Store the data in "result", you will need it in the next step.

- Go to https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.testnet.analog.one#/staking/actions
- Click on + Validator
- Choose your account with value bonded (>0.9), choose your payment destination (leave a little amount for gas)
- Click on Next
- Paste your data above to keys from rotatekeys. Config your reward commission percentage (<10)
- Click on Bond & Validate

## 4. Misc

### Telemetry

https://telemetry.analog.one/#/0x0614f7b74a2e47f7c8d8e2a5335be84bdde9402a43f5decdec03200a87c8b943

### Stop node

```bash
sudo docker stop timechain && sudo docker rm timechain
```

## Tags

`polka`, `docker`
