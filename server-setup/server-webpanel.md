---
description: Server webpanel instructions.
---

# Server Webpanel Instructions

## Managing The Server

Admin Page: [http://localhost:1234/](http://localhost:8080/)

1: Nat type and kick players

2:Disband lobbys



For public hosting use [http://localhost:8080/](http://localhost:8080/) this displays players and lobbys no kick button.

<figure><img src="../.gitbook/assets/Webpannel small most important explanation.png" alt=""><figcaption></figcaption></figure>

***

## Change The Server Access

Edit the project-bo4.json if you want to change the access ip to limit people connecting to the webpanel.

```
"httpserver": {
    "access_ip": "0.0.0.0"
}
```

<figure><img src="../.gitbook/assets/Webpannel IP.png" alt=""><figcaption></figcaption></figure>

Replace `"0.0.0.0"` or whatever value you have with the IP address you only want to be able to access the webpanel. (Leaving it `"0.0.0.0"` - will allow anyone to access the webpanel with your ip:8080 ) To know your IP address, you can use this website: [https://whatismyipaddress.com/](https://whatismyipaddress.com/), only you will be able to connect to the webpanel.

