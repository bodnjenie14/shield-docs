---
'0': S
'1': e
'2': r
'3': v
'4': e
'5': r
'6': ' '
'7': w
'8': e
'9': b
'10': p
'11': a
'12': 'n'
'13': e
'14': l
'15': ' '
'16': i
'17': 'n'
'18': s
'19': t
'20': r
'21': u
'22': c
'23': t
'24': i
'25': o
'26': 'n'
'27': s
'28': .
description: Server webpanel instructions.
---

# Server Webpanel

## Managing The Server

Open [http://localhost:8080/](http://localhost:8080/).

1: Nat type and kick players

2:Disband lobbys

<figure><img src="../.gitbook/assets/Webpannel small most important explanation.png" alt=""><figcaption></figcaption></figure>

## Change The Server Acsess

Edit the project-bo4.json if you want to change the access ip to limit people connecting to the webpanel.

```
"httpserver": {
    "access_ip": "0.0.0.0"
}
```

<figure><img src="../.gitbook/assets/Webpannel IP.png" alt=""><figcaption></figcaption></figure>

Replace `"0.0.0.0"` or whatever value you have with the IP address you only want to be able to access the webserver. (Leaving it `"0.0.0.0"` - will allow anyone to access the webserver with your ip:8080 ) To know your IP address, you can use this website: [https://whatismyipaddress.com/](https://whatismyipaddress.com/), only you will be able to connect to the webpanel.
