
# docker-electrum-bitsend

> Run a Bitsend Electrum server with one command

A Docker configuration with sane defaults for running a full Bitsend node behind an ElectrumX server.

## Usage

```
screen docker-compose up
```

This will pull the latest version of bitsendd and ElectrumX, start syncing the blockchain, generate an SSL certificate and start listening for secure Electrum traffic on port 55002.

All blockchain/bitsendd data will be stored in `./data/bitsendd` and all ElectrumX data will be stored in `./data/electrumx`. This is stored on the host machine and mounted in the docker container as a volume, meaning it will persist across reboots/updates/containers etc.

### Is this secure?

Yep, this is built to have sensible, safe defaults out of the box. bitsendd JSON-RPC is only accessible from the ElectrumX container, it's never exposed to the internet, it's not even exposed to localhost. ElectrumX will generate a fresh SSL certificate on first boot and only listen for SSL traffic. Unencrypted traffic will be ignored.

### How do I use an existing SSL certificate?

If there's an SSL certificate/key (`electrumx.crt`/`electrumx.key`) in `./data/electrumx`, it'll be used instead of generating a new one.

### I don't trust your images, how do I build them myself?

You can build `dalijolijo/bitsendd` and `lukechilds/electrumx` yourself here:

- https://github.com/dalijolijo/docker-bitsendd
- https://github.com/lukechilds/docker-electrumx

## License

MIT © Luke Childs
