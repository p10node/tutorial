# Viper, Sui side blockchain

```bash
sudo vi ~/.viper/config/blockchains.json

# or

sudo nano ~/.viper/config/blockchains.json
```

```bash
[
  ...,
  {
    "id": "0003",
    "url": "https://sui-rpc.publicnode.com",
    "websocket_url": "wss://sui-rpc.publicnode.com/websocket",
    "basic_auth": {
      "username": "",
      "password": ""
    }
  }
]
```

Save it.

## Store to blockchain

```bash
viper servicers stake self <addr> <amt> 0001,0002,0003 $GEO-ID <viper node URL> testnet

# example

viper servicers stake self 41f0cc00a32b2a15124fc03a401bf17f86fee6f1 11000000000 0001,0002,0003 0C00 https://viper.p10node.com:443 testnet
```
