# Cahier des charges — Projet réseau

## Contexte : Atelier Nébula

Atelier Nébula est une PME fictive qui conçoit des objets connectés. Elle comprend des équipes administratives et commerciales, un bureau d’études, un atelier de production et un espace d’accueil. Elle reçoit des visiteurs, utilise des équipements connectés et collabore avec un partenaire sur un autre site.

L’entreprise ne possède pas encore de réseau. Elle souhaite une architecture fiable, sécurisée, évolutive et administrable.

## Mandat

Concevez et simulez dans **Cisco Packet Tracer** un réseau répondant aux besoins d’Atelier Nébula. Vous choisissez librement la topologie, les équipements, l’adressage et les protocoles : justifiez vos choix et ne retenez que les fonctions utiles au scénario.

**Un commutateur de couche 3 est obligatoire.** Il doit être actif dans la maquette et assurer le routage inter-VLAN.

Le réseau doit permettre aux utilisateurs et équipements de communiquer selon leurs besoins, séparer les usages sensibles, donner accès aux ressources nécessaires et à Internet, et faciliter l’administration, le dépannage et l’évolution de l’infrastructure.

## Notions à traiter

Intégrez les notions pertinentes des cours, ou expliquez brièvement pourquoi elles ne sont pas mises en œuvre :

- **Topologie et transmission :** schémas physique et logique, équipements, interfaces, liens et supports (cuivre, fibre, sans-fil) ; modèles OSI/TCP-IP, adresses MAC/IP et encapsulation.
- **Commutation :** VLAN, ports d’accès et trunks ; routage inter-VLAN par le switch L3 ; sécurisation des ports ; boucles et continuité (STP, EtherChannel ou solutions pertinentes).
- **Adressage et routage :** sous-réseaux, passerelles, IPv4 et IPv6 ; tables et chemins de routage ; routage statique ou dynamique ; accès externe et NAT/PAT si nécessaire.
- **Services et sécurité :** DHCP, DNS ou autres services utiles ; filtrage inter-VLAN et vers l’extérieur (ACL ou équivalent) ; protection des utilisateurs, visiteurs, équipements et accès d’administration.
- **Télécommunications et disponibilité :** Wi-Fi, redondance, QoS, voix, radio ou antennes selon les besoins ; analyse des pannes et de leurs conséquences.

## Trame de documentation de la topologie

La topologie est entièrement au choix des étudiants. Réalisez vos propres schémas et indiquez :

- le rôle des équipements, leurs interfaces et leurs interconnexions ;
- les VLAN, sous-réseaux et passerelles, ainsi que les trunks et ports d’accès utilisés ;
- les supports de transmission et les connexions aux réseaux externes, si nécessaires.

Cette liste précise les informations à documenter, pas une architecture à reproduire.

## Livrables

1. Dossier présentant les besoins, hypothèses et choix justifiés.
2. Schémas physique et logique avec légende, et plan d’adressage.
3. Maquette Packet Tracer et configurations utiles, comprenant le switch L3 et le routage inter-VLAN.
4. Tests de connectivité et de filtrage, avec résultats et au moins un scénario de panne.
5. Bilan des limites, risques et pistes d’évolution.

Les modalités de remise et de démonstration sont à convenir avec l’enseignant. Les limites de Packet Tracer doivent être signalées et, si nécessaire, expliquées par un test ou une description.

## Réussite du projet

La solution doit être cohérente entre besoins, schémas, adressage et maquette. Les communications prévues doivent fonctionner, les accès interdits être bloqués ou démontrés, et les tests permettre de vérifier et diagnostiquer le réseau. La qualité des justifications et la pertinence des choix priment sur le nombre d’équipements ou de protocoles.

## Références

Le projet s’appuie sur les supports du dossier `Cour` : rappels, chapitres 1 et 2 de routage et commutation, `Telecommunication Avancé.pdf`, ainsi que les fiches sur les ACL, les tables de routage et les concepts de routage et de commutation.
