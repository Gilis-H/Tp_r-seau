# Packet Tracer 3.3.12 — Configuration des VLAN

> Fiche de travail en français, reformulée à partir des consignes de l’activité.

## Objectifs

1. Examiner la configuration VLAN par défaut.
2. Créer et nommer les VLAN sur les commutateurs.
3. Affecter les ports d’accès aux VLAN demandés.
4. Vérifier la connectivité au sein d’un VLAN et diagnostiquer son absence.

## Plan d’adressage des postes

| Poste | Interface | Adresse IP | Masque | VLAN |
|---|---|---|---|---:|
| PC1 | Carte réseau | 172.17.10.21 | 255.255.255.0 | 10 |
| PC2 | Carte réseau | 172.17.20.22 | 255.255.255.0 | 20 |
| PC3 | Carte réseau | 172.17.30.23 | 255.255.255.0 | 30 |
| PC4 | Carte réseau | 172.17.10.24 | 255.255.255.0 | 10 |
| PC5 | Carte réseau | 172.17.20.25 | 255.255.255.0 | 20 |
| PC6 | Carte réseau | 172.17.30.26 | 255.255.255.0 | 30 |

## Partie 1 — Examiner les VLAN par défaut

1. Sur S1, afficher les VLAN et les ports qui leur sont associés.
2. Vérifier la connectivité initiale entre les postes d’un même sous-réseau :
   - PC1 et PC4 ;
   - PC2 et PC5 ;
   - PC3 et PC6.
3. Constater que les communications entre sous-réseaux différents nécessitent un périphérique de couche 3 assurant le routage inter-VLAN.

**Question :** quels bénéfices la segmentation en VLAN apporte-t-elle au réseau ?

## Partie 2 — Créer les VLAN

Sur **S1, S2 et S3**, créer les mêmes VLAN et leur attribuer les noms suivants (respecter les majuscules et minuscules) :

| VLAN | Nom |
|---:|---|
| 10 | Faculty/Staff |
| 20 | Students |
| 30 | Guest(Default) |
| 99 | Management&Native |
| 150 | VOICE |

Exemple pour créer et nommer un VLAN :

```text
configure terminal
vlan 10
name Faculty/Staff
```

Répéter la procédure pour les autres VLAN, puis vérifier leur présence. La commande `show vlan brief` affiche notamment leur nom, leur état et les ports d’accès associés.

## Partie 3 — Affecter les ports d’accès

Effectuer les affectations suivantes **sur S2 ET sur S3** :

| Port | VLAN de données |
|---|---:|
| FastEthernet 0/11 | 10 |
| FastEthernet 0/18 | 20 |
| FastEthernet 0/6 | 30 |

Exemple pour le port Fa0/11 :

```text
configure terminal
interface fastEthernet 0/11
switchport mode access
switchport access vlan 10
```

Répéter ces commandes pour Fa0/18 dans le VLAN 20 et Fa0/6 dans le VLAN 30, puis faire les trois affectations sur l’autre commutateur. Vérifier le résultat sur S2 et S3 avec `show vlan brief`.

### Port du téléphone IP sur S3

Sur S3, Fa0/11 relie un téléphone IP et PC4. Le trafic du PC doit rester dans le VLAN de données 10, tandis que le trafic vocal utilise le VLAN 150. Configurer le VLAN voix sur Fa0/11 et activer la confiance CoS demandée pour la QoS :

```text
configure terminal
interface fastEthernet 0/11
mls qos trust cos
switchport voice vlan 150
```

## Diagnostic de la connectivité entre VLAN

Après l’affectation des ports, examiner la configuration VLAN de S2 et tester de nouveau les communications entre les paires de postes. Dans la sortie fournie par l’activité, Fa0/11, Fa0/18 et Fa0/6 figurent dans les VLAN attendus, mais `GigabitEthernet0/1` reste listé comme port du VLAN 1.

Un ping entre PC1 et PC4 peut donc échouer même si les deux postes ont des adresses du réseau `172.17.10.0/24` et que leurs ports d’accès sont dans le VLAN 10 : si les postes sont raccordés à des commutateurs différents, le lien intercommutateur doit aussi transporter le VLAN 10. Vérifier le rôle de `GigabitEthernet0/1` dans la topologie. S’il s’agit d’un lien entre commutateurs transportant plusieurs VLAN, il doit être configuré comme trunk sur les deux extrémités, avec les VLAN nécessaires autorisés.

Procéder méthodiquement :

1. Repérer les ports reliant les commutateurs dans la topologie.
2. Vérifier que les VLAN existent sur les commutateurs concernés.
3. Vérifier que les ports des postes sont des ports d’accès dans les VLAN attendus.
4. Vérifier le mode trunk et les VLAN autorisés sur les liaisons intercommutateurs.
5. Refaire les tests de ping au sein d’un même VLAN.

Le routage inter-VLAN n’est pas requis pour faire communiquer deux hôtes du même VLAN et du même sous-réseau ; il est nécessaire pour les échanges entre VLAN différents.

**Questions de diagnostic :**

- Le ping PC1–PC4 réussit-il après l’affectation des ports ? Justifier le résultat.
- Pourquoi l’appartenance de `GigabitEthernet0/1` au VLAN 1 peut-elle être importante ?
- Quelle configuration du lien intercommutateur permettrait de transporter les VLAN nécessaires ?
