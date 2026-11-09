# Plan d’adressage et correspondance des ports

Les adresses sont attribuées selon les plages indiquées pour le projet. Sur les liens `/30`, R1 utilise la dernière adresse utilisable et l’équipement en face la première. Les postes et le serveur utilisent les premières adresses disponibles de leur sous-réseau. Les VLAN 10 et 20 utilisent respectivement `192.168.10.0/24` et `192.168.20.0/24`.

## Liens routés

| Équipement | Interface | Adresse IP / préfixe | Équipement distant | Interface distante | Adresse IP / préfixe |
|---|---|---|---|---|---|
| R1 | Gig0/0 | 10.10.7.2/30 | Multilayer Switch1 | Gig1/0/4 | 10.10.7.1/30 |
| R1 | Fa0/1/0 | 10.10.8.2/30 | Multilayer Switch2 | Gig1/0/4 | 10.10.8.1/30 |
| R1 | Gig0/2 | 10.10.9.2/30 | R3 | Gig0/1 | 10.10.9.1/30 |
| R1 | Gig0/1 | 10.10.10.2/30 | R2 | Gig0/1 | 10.10.10.1/30 |
| R2 | Gig0/2 | 172.16.0.14/28 | SW-3 | Fa0/1 | — (port de commutation) |
| R3 | Gig0/0 | 172.168.0.254/24 | SW-4 | Fa0/1 | — (port de commutation) |

## Interfaces VLAN des commutateurs multicouches

| Équipement | Interface VLAN | Adresse IP / préfixe | Rôle |
|---|---|---|---|
| Multilayer Switch1 | VLAN 10 | 192.168.10.254/24 | Passerelle des postes du VLAN 10 |
| Multilayer Switch1 | VLAN 20 | 192.168.20.254/24 | Passerelle du poste du VLAN 20 |
| Multilayer Switch2 | VLAN 10 | 192.168.10.253/24 | Interface VLAN secondaire |
| Multilayer Switch2 | VLAN 20 | 192.168.20.253/24 | Interface VLAN secondaire |

Les postes utilisent `.254` comme passerelle par défaut. Les adresses `.253` de Multilayer Switch2 ne fournissent pas de bascule automatique ; celle-ci nécessiterait un mécanisme de redondance de passerelle.

## Postes et serveur

| Équipement | Interface | VLAN / réseau | Adresse IP / préfixe | Passerelle par défaut |
|---|---|---|---|---|
| PC-1 | Fa0 | VLAN 10 — 192.168.10.0/24 | 192.168.10.1/24 | 192.168.10.254 |
| PC-3 | Fa0 | VLAN 10 — 192.168.10.0/24 | 192.168.10.2/24 | 192.168.10.254 |
| PC-2 | Fa0 | VLAN 20 — 192.168.20.0/24 | 192.168.20.1/24 | 192.168.20.254 |
| PC-Dragster | Fa0 | Réseau attaquant — 172.16.0.0/28 | 172.16.0.1/28 | 172.16.0.14 |
| PC-Externe | Fa0 | Entreprise externe — 172.168.0.0/24 | 172.168.0.1/24 | 172.168.0.254 |
| Server-Externe | Fa0 | Entreprise externe — 172.168.0.0/24 | 172.168.0.2/24 | 172.168.0.254 |

## Liaisons de niveau 2

Les interfaces physiques ci-dessous servent aux liaisons de commutation (accès ou trunk) et ne reçoivent pas d’adresse IP.

| Équipement | Interface locale | Équipement distant | Interface distante |
|---|---|---|---|
| Multilayer Switch1 | Gig1/0/3 | Multilayer Switch2 | Gig1/0/3 |
| Multilayer Switch1 | Gig1/0/2 | SW-1 | Fa0/5 |
| Multilayer Switch1 | Gig1/0/1 | SW-2 | Fa0/2 |
| Multilayer Switch2 | Gig1/0/2 | SW-1 | Fa0/4 |
| Multilayer Switch2 | Gig1/0/1 | SW-2 | Fa0/1 |
| SW-1 | Fa0/1 | PC-1 | Fa0 |
| SW-1 | Fa0/2 | PC-2 | Fa0 |
| SW-1 | Fa0/3 | PC-3 | Fa0 |
| SW-3 | Fa0/3 | PC-Dragster | Fa0 |
| SW-4 | Fa0/3 | PC-Externe | Fa0 |
| SW-4 | Fa0/2 | Server-Externe | Fa0 |

Les adresses de gestion de SW-1 à SW-4 ne sont pas définies ici. Les liens trunk doivent transporter les VLAN nécessaires ; leur configuration et celle de STP restent à réaliser dans la maquette.
