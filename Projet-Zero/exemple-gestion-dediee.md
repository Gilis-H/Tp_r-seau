# Exemple à revoir : réseau de gestion dédié

> **Document de réflexion — non validé et non configuré.** Cet exemple est conservé pour être revu après l’étude de la matière. Les adresses proposées ne font pas encore partie du plan d’adressage officiel.

Un réseau de gestion dédié place les interfaces d’administration des équipements dans un VLAN et un sous-réseau distincts des postes utilisateurs. Dans l’exemple ci-dessous, le VLAN 99 est utilisé dans le réseau Nébula. Les autres zones ont des sous-réseaux de gestion distincts.

## Exemple de plan d’adressage

| Zone | Équipement | VLAN de gestion | Adresse de gestion | Passerelle |
|---|---|---:|---|---|
| Nébula | Multilayer Switch1 | 99 | `192.168.99.254/24` | — |
| Nébula | Multilayer Switch2 | 99 | `192.168.99.253/24` | — |
| Nébula | SW-1 | 99 | `192.168.99.2/24` | `192.168.99.254` |
| Nébula | SW-2 | 99 | `192.168.99.3/24` | `192.168.99.254` |
| Réseau attaquant | R2, interface de gestion | 99 | `192.168.100.1/24` | — |
| Réseau attaquant | SW-3 | 99 | `192.168.100.2/24` | `192.168.100.1` |
| Entreprise externe | R3, interface de gestion | 99 | `192.168.101.1/24` | — |
| Entreprise externe | SW-4 | 99 | `192.168.101.2/24` | `192.168.101.1` |

Le numéro de VLAN 99 peut être réutilisé dans des domaines de couche 2 séparés ; les sous-réseaux IP restent distincts. Les deux commutateurs multicouches ont ici des adresses SVI différentes. `.254` est la passerelle indiquée pour les switches d’accès Nébula ; `.253` ne fournit pas, à elle seule, de bascule automatique.

## Points à étudier avant toute configuration

- Dans Nébula, créer le VLAN 99 et le transporter sur les trunks nécessaires. Les adresses de gestion des commutateurs multicouches sont portées par leurs interfaces VLAN.
- Pour donner une interface de gestion aux switches SW-3 et SW-4, il faudrait prévoir comment le VLAN de gestion rejoint R2 ou R3 : par exemple, un lien trunk avec sous-interfaces de routeur ou une interface physique distincte. Cela modifierait le fonctionnement actuel des liaisons et doit être conçu avant d’attribuer ces adresses.
- Le réseau attaquant est non fiable. Placer SW-3 dans son propre sous-réseau de gestion ne suffit pas à protéger son plan de gestion contre les hôtes de cette zone. L’accès administratif à SW-3 et aux équipements de Nébula doit être restreint et justifié ; ne pas rendre les interfaces de gestion Nébula accessibles depuis le réseau attaquant.
- L’accès de gestion de SW-4 relève de la politique de l’entreprise externe. Les échanges d’administration entre zones ne doivent pas être activés par défaut.
- Définir les routes et les ACL nécessaires, les postes autorisés à administrer les équipements, ainsi que les protocoles d’administration retenus.

Ces choix sont des pistes de réflexion. Ils devront être corrigés ou confirmés après l’étude des VLAN, des trunks, du routage inter-VLAN et du filtrage.
