# Table d’adressage — activité 15.6.1

| Appareil | Interface | Adresse IPv4 / préfixe | Adresse IPv6 / préfixe |
|---|---|---|---|
| Edge_Router | S0/0/0 | `10.10.10.2/30` | `2001:db8:a:1::2/64` |
| Edge_Router | S0/0/1 | `10.10.10.6/30` | `2001:db8:a:2::2/64` |
| Edge_Router | G0/0 | `192.168.10.17/28` | `2001:db8:1:10::1/64` |
| Edge_Router | G0/1 | `192.168.11.33/27` | `2001:db8:1:11::1/64` |
| ISP1 | S0/0/0 | `10.10.10.1/30` | `2001:db8:a:1::1/64` |
| ISP1 | G0/0 | `198.0.0.1/24` | `2001:db8:ff::1/64` |
| ISP2 | S0/0/1 | `10.10.10.5/30` | `2001:db8:a:2::1/64` |
| ISP2 | G0/0 | `198.0.0.2/24` | `2001:db8:ff::2/64` |
| PC-A | Carte réseau | `192.168.10.19/28` | `2001:db8:1:10::19/64` |
| PC-B | Carte réseau | `192.168.11.4/27` | `2001:db8:1:11::45/64`* |
| Serveur client | Carte réseau | `198.0.0.10/24`* | `2001:db8:ff::10/64`* |

\* Le préfixe n’est pas indiqué dans l’image pour cette adresse ; il est déduit du sous-réseau de l’interface correspondante.