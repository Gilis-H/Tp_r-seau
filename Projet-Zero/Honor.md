# Projet-Zero — Avancement de Honor

[Maquette Packet Tracer](./Projet-zero-Honor.pkt) · [Plan d’adressage](./addressage.md)

## Configuration réalisée sur S1

| Poste | Port d’accès | VLAN | Adresse IP | Passerelle prévue |
|---|---|---|---|---|
| PC-1 | Fa0/1 | 10 `ORION` | `192.168.10.1/24` | `192.168.10.252` |
| PC-2 | Fa0/2 | 20 `HELIX` | `192.168.20.1/24` | `192.168.20.252` |
| PC-3 | Fa0/3 | 10 `ORION` | `192.168.10.2/24` | `192.168.10.252` |

Les VLAN 10 et 20 ont été créés sur S1. Les trois ports des PC ont été placés en mode accès. `show vlan brief` confirme leurs affectations et `show ip interface brief` les affiche en `up/up`.

## Test validé

Le ping **PC-1 → PC-3** réussit après correction de l’adresse IP de PC-3. Pendant le diagnostic, la table MAC de S1 a montré une adresse apprise sur chacun des deux ports dans le VLAN 10.

Les trunks vers les switches multicouches et le routage entre les VLAN 10 et 20 restent à valider.
