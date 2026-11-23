# Projet-Zero — Avancement de Honor

[Maquette Packet Tracer](./Projet-zero-Honor.pkt) · [Plan d’adressage](./addressage.md)

## Commandes utilisées sur S1

| Action | Commandes | Résultat |
|---|---|---|
| Créer les VLAN | `vlan 10`, `name ORION`, `vlan 20`, `name HELIX` | VLAN 10 et 20 créés. |
| Affecter les ports des PC | `switchport mode access`, `switchport access vlan 10` ou `switchport access vlan 20` | `Fa0/1` (PC-1) et `Fa0/3` (PC-3) dans ORION. `Fa0/2` (PC-2) dans HELIX. |
| Vérifier les ports | `show vlan brief`, `show interfaces fa0/1 switchport`, `show ip interface brief` | Affectations confirmées et ports des PC en `up/up`. |
| Suivre le trafic pendant le dépannage | `show mac address-table dynamic` | S1 apprend une MAC sur `Fa0/1` et une sur `Fa0/3`, dans le VLAN 10. |

Sur PC-1, `ping 192.168.10.2` a servi à tester la connectivité et `arp -a` à vérifier l’adresse MAC associée à cette IP.

## Erreurs constatées et résolues

1. **Ports des PC passés en trunk.** `Fa0/1` et `Fa0/3` avaient disparu de `show vlan brief`. Le retour en mode accès a rétabli leur affectation à ORION.
2. **Ping PC-1 → PC-3 en échec.** Même après vérification des ports et de la table MAC, `ping 192.168.10.2` échouait. Après correction de l’adresse de PC-3 dans **Desktop → IP Configuration** (`192.168.10.2/24`), le ping a réussi.
3. **VLAN natif 99 renseigné sur les ports des PC.** Après discussion avec l’enseignant, le réglage a été retiré de `Fa0/1`, `Fa0/2` et `Fa0/3` pour éviter qu’un passage accidentel en trunk classe les trames non étiquetées des PC dans le VLAN 99.
4. **Filtre VLAN rejeté par S1.** `show mac address-table dynamic vlan 10` a donné une erreur de syntaxe. La commande sans filtre a permis de lire les entrées du VLAN 10.
