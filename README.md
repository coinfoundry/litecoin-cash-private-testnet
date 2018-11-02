## Litecoin-Cash three-node private network in regtest mode

- Node Pool
  - RPC Port 16001, Username: user, Password: pass
- Node Bob
  - RPC Port 16002, Username: user, Password: pass
- Node Alice
  - RPC Port 16003, Username: user, Password: pass

### Addresses

- Pool:  QUsZdWSfcRFf4z1EJToU9VKYHo6ojoKNkV
- Bob:   QfJKi6TsAXDrpwrTwatcXWoeAAvGg1DH5B
- Alice: Qb2Fuyjx4oDoUzNJUKRqB52NQNTwVGhU6q

### To run this image with internal ports exposed at host:

```bash
docker run -it -d -p 16001:16001 -p 16002:16002 -p 16003:16003 coinfoundry/litecoin-cash-private-testnet
```

### Generating blocks:

```bash
docker exec -i -t <container_id> /usr/bin/litecoincash-cli -datadir=/data/node-pool generate 1
```

### Example RPC against Node-Pool:

```bash
curl --user user:pass --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getinfo", "params": [] }' -H 'content-type: application/json;' http://127.0.0.1:16001/
```
