---
description: How to setup up the server.
---

# How To Set Up The Server

## Automatic Setup

Install DwServer installer from [here](https://cdn.discordapp.com/attachments/1163956866309697588/1170755715497988227/Bo4\_Deamonware\_Server\_Installer.msi?ex=65a4063a\&is=6591913a\&hm=b61c299d67c09cc565dd2397650749eb6af9718addc92f6144436ba0ac4f1e81&) .

Run `Bo4_Deamonware_Server_Installer.msi`

<figure><img src="../.gitbook/assets/Captura de pantalla 2024-01-17 143135.png" alt=""><figcaption></figcaption></figure>

Make sure to tick both cases.

***

## Manual Setup

Download server from [here](https://github.com/bodnjenie14/DWUPDATES/releases/download/2/DW.SERVER.rar).

### Open ports

#### Automatic

Download `FIREWALL RULES.BAT`  [here.](https://cdn.discordapp.com/attachments/1160535315648356437/1197963063492624525/FIREWALL\_RULES.BAT?ex=65bd2d0b\&is=65aab80b\&hm=5afe3b2d5bbc28f8c753d48d1252da20b4add5540cae1830c3d3971a8043985e&)

Run the `FIREWALL RULES.BAT` file as administrator.&#x20;

Optionally, to make the webserver accessible over external network, run the `FIREWALL RULES (WEBSERVER).BAT` file as administrator.

#### Manual

Open Windows Defender Firewall with Advanced Security by pressing Windows+R, type `WF.msc` and press ok.

* In the Inbound Rules tab, create a new rule by pressing the "New Rule..." button.

For the type, select `Port`. In the protocol and ports menu, select TCP and specific ports. With the value `3074,6542,8080`. You can keep the default settings for the next menus and give `ShieldServer-TCP` as a name.

* Create another rule with the "New Rule..." button, also with the type `Port`.

In the protocol and ports menu, select UDP and specific ports. With the value `3074`. You can keep the default settings for the next menus and give `ShieldServer-UDP` as a name.

* In the Outbound Rules tab, create a new rule by pressing the "New Rule..." button.

For the type, select `Port`. In the protocol and ports menu, select TCP and specific ports. With the value `3074,6542`. You can keep the default settings for the next menus and give `ShieldServer-TCP` as a name.

* Create another rule with the "New Rule..." button, also with the type `Port`.

In the protocol and ports menu, select UDP and specific ports. With the value `3074`.

* Create another rule with the "New Rule..." button, also with the type `Port`.

In the protocol and ports menu, select UDP and specific ports. With the value `3074`.\
You can keep the default settings for the next menus and give `ShieldServer-UDP` as a name. If you want to play with players outside your local netword, you also need the forward your ports with your router. Or use `radmin` / `zero tier`. This website can help with most of the routers: [https://portforward.com/router.htm](https://portforward.com/router.htm) The ports are:

```
TCP: 3074, 6542
UDP: 3074
```

The webserver ports are:

```
TCP: 8080
```
