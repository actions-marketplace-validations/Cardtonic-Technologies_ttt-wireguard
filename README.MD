# TTT WireGuard

Simplified WireGuard GitHub Action using `wg-quick`. Requires WireGuard configuration file as input, or defaults to `secrets.WG_CONFIG`(must have set this secret in organization secrets) to get your connection up and running.

## Example Secret Config
```text

[Interface]
PrivateKey = Poiuhejuhjs1Jr3U=
Address = 10.8.0.10/24
DNS = 1.1.1.1

[Peer]
PublicKey = 0987yhi87yhji87yhj8Z5qJ9r9/Hhw9uxE=
PresharedKey = 098uj98UJUhki8uhj8uh8uhjihu+nN0QLI=
AllowedIPs = 0.0.0.0/0, ::/0
PersistentKeepalive = 0
Endpoint = 213.10.12.15:51820
```
## Usage

To use this GitHub Action, follow these steps in your workflow file:

```yaml
name: WireGuard Connection

on:
  push:
    branches:
      - main

jobs:
  wireguard:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Set up WireGuard Connection
      uses: Cardtonic-Technologies/ttt-wireguard@v1
      with:
        WG_CONFIG: ${{ secrets.WG_CONFIG }}
```