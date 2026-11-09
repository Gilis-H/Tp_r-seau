# Cahier des charges — Projet réseau

## Contexte : entreprise Nébula et réseaux externes

La topologie représente le réseau de l’**entreprise Nébula**, relié à deux réseaux externes distincts : un **réseau attaquant** et une **entreprise externe**. Le réseau Nébula comprend trois postes répartis entre les VLAN 10 et 20, un switch d’accès SW-1, un second switch d’accès SW-2 et deux commutateurs multicouches. Le réseau attaquant comprend le routeur R2, SW-3 et le poste PC-Dragster. L’entreprise externe comprend le routeur R3, SW-4, PC-Externe et Server-Externe. Le routeur R1 relie le réseau Nébula à R2 et R3.

## Mandat

Le fichier **`Projet-zero.pkt`** contient la topologie à exploiter. Ouvrez-le dans **Cisco Packet Tracer** et configurez les équipements et les interconnexions représentés pour assurer les communications prévues entre l’entreprise Nébula et les deux réseaux externes. Le réseau attaquant doit être considéré comme non fiable : le projet doit examiner et contrôler les accès qu’il peut tenter vers les ressources de Nébula. Toute modification ou tout ajout à la topologie doit être nécessaire et justifié ; il ne s’agit pas de la remplacer par une architecture libre.

Les deux commutateurs multicouches visibles dans le réseau Nébula doivent être intégrés à la solution. Configurez et justifiez leur rôle, notamment pour le routage inter-VLAN des VLAN 10 et 20. Configurez également le routage entre R1, R2, R3 et les réseaux qu’ils relient, selon le plan d’adressage retenu.

Le réseau doit permettre les communications nécessaires entre les postes et les ressources autorisées, préserver la segmentation des VLAN et limiter les accès depuis le réseau attaquant conformément aux règles de sécurité définies pour le scénario. Les échanges nécessaires avec l’entreprise externe doivent également être identifiés et contrôlés.

## Notions à traiter

Intégrez les notions pertinentes des cours, ou expliquez brièvement pourquoi elles ne sont pas mises en œuvre :

- **Topologie et transmission :** rôles des routeurs R1, R2 et R3, des deux commutateurs multicouches et des switches SW-1 à SW-4 ; interfaces, liens et supports présents ; modèles OSI/TCP-IP, adresses MAC/IP et encapsulation.
- **Commutation :** VLAN 10 et 20 pour les postes du réseau Nébula ; ports d’accès et liens entre les commutateurs à relever et configurer ; routage inter-VLAN par les commutateurs multicouches ; prévention des boucles et continuité (STP, EtherChannel ou mécanisme adapté aux liens présents).
- **Adressage et routage :** plan d’adressage et passerelles de chaque réseau ; routage entre Nébula, le réseau attaquant et l’entreprise externe ; tables et chemins de routage ; choix et justification du routage statique ou dynamique.
- **Services et sécurité :** rôle et services de Server-Externe à relever ou à définir ; filtrage entre les VLAN et avec les réseaux externes (ACL ou équivalent) ; politique d’accès explicite face au réseau attaquant et contrôle des accès aux équipements d’administration.
- **Disponibilité et dépannage :** incidences des liens multiples visibles ; analyse des pannes et de leurs conséquences ; vérification des communications autorisées et refusées entre les différentes zones.

## Analyse et documentation de la topologie

Relevez et exploitez la topologie présente dans `Projet-zero.pkt` et représentée dans la nouvelle capture. Elle comprend :

- le réseau de l’entreprise Nébula : R1, deux commutateurs multicouches, SW-1 et SW-2, PC-1 et PC-3 dans le VLAN 10, et PC-2 dans le VLAN 20 ;
- le réseau attaquant : R2, SW-3 et PC-Dragster ;
- l’entreprise externe : R3, SW-4, PC-Externe et Server-Externe.

Réalisez des schémas physique et logique de la maquette configurée et documentez le rôle des équipements, les interfaces et interconnexions, les VLAN, les sous-réseaux et passerelles, ainsi que les routes et les règles de filtrage. La capture montre l’organisation générale et les VLAN des trois postes Nébula, mais ne précise pas les adresses IP, les masques, les passerelles, les services du serveur ni les configurations des liens et du routage : relevez ces paramètres dans la maquette ou définissez-les lorsque nécessaire, puis documentez-les. Signalez toute modification justifiée à la topologie fournie.

## Livrables

1. Dossier présentant les besoins, hypothèses et choix justifiés.
2. Schémas physique et logique avec légende, plan d’adressage, routes et règles de filtrage.
3. Maquette Packet Tracer configurée (`Projet-zero.pkt`) et configurations utiles, comprenant les VLAN 10 et 20, le routage inter-VLAN et le routage vers les deux réseaux externes.
4. Tests documentés de connectivité et de filtrage entre les VLAN et les trois zones, incluant des tentatives d’accès depuis le réseau attaquant et au moins un scénario de panne.
5. Bilan des limites, risques et pistes d’évolution.

Les modalités de remise et de démonstration sont à convenir avec l’enseignant. Les limites de Packet Tracer doivent être signalées et, si nécessaire, expliquées par un test ou une description.

## Réussite du projet

La solution doit respecter la topologie fournie et rester cohérente entre les besoins, les schémas, l’adressage et la maquette. Les communications autorisées entre les VLAN, les ressources externes et l’entreprise Nébula doivent fonctionner ; les accès non autorisés, notamment depuis le réseau attaquant, doivent être bloqués et démontrés par des tests. La qualité des justifications et la pertinence des règles de sécurité priment sur l’ajout d’équipements ou de protocoles.

## Références

Le projet s’appuie sur les supports du dossier `Cour` : rappels, chapitres 1 et 2 de routage et commutation, `Telecommunication Avancé.pdf`, ainsi que les fiches sur les ACL, les tables de routage et les concepts de routage et de commutation.
