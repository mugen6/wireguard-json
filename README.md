## wireguard-JSON

Bash script (+ jq) to output Wireguard stats to JSON

Running this command:

```
wg show all dump
```

Returns a tab delimited table:

```SQL
wg0     kI1DExltXHlkVdBsHqEQZatZf8XvISU7YT1RpDyJsQQ=    (none)  194.55.246.255:7471     10.10.178.16/32        1713634774      38071572        14387132  off
wg0     T7Rk0v61bY8gXWBBlDwfuAAuAHkNidRErIjJLx9ghjc=    (none)  194.181.246.252:16369   10.10.178.17/32        1713634797      38095276        14533700  off
wg0     nsWiimtOn56BBluAAuAHkNidsNeP11O7vyNRooKLQFs=    (none)  35.181.246.253:13962    10.10.178.18/32        1713634709      38167672        14579416  off
wg0     TpiTGEh9O88BRx6AQy7VuMZ9TJuTfAUbUbk36PjECXg=    (none)  87.45.211.255:16029     10.10.178.19/32        1713634814      38162952        14445784  off
```

The `wg-json` script will convert the to JSON and add a timestamp:

```json
[
  {
    "interface": "wg1",
    "publickey": "txe1dW20Y0TE045C7pxsALAIUCtZzO016J1Z2NHzEUE=",
    "public_ip": "186.52.222.66",
    "private_ip": "10.10.178.24",
    "latest_handshake": "1713635235",
    "tx": "38127744",
    "rx": "14719040",
    "timestamp": "2024-04-20T17:47:51Z"
  },
  {
    "interface": "wg1",
    "publickey": "PSjCYs4sUHBiLJcZEOT2p45AoalEYuMvJCn8IRZDcW8=",
    "public_ip": "84.34.206.70",
    "private_ip": "10.10.178.25",
    "latest_handshake": "1713635250",
    "tx": "38111696",
    "rx": "14718176",
    "timestamp": "2024-04-20T17:47:51Z"
  }
]
```

Runs very quickly thanks to jq - 10k rows takes 0.4 seconds.
