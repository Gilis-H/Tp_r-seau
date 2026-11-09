# Cahier des charges — Projet réseau

## 1. Contexte

Concevoir, documenter et simuler l’architecture réseau d’une entreprise fictive qui ne dispose encore d’aucun réseau structuré. Le projet doit mobiliser les notions du cours de télécommunications et de réseaux, sans imposer une topologie ou une configuration toutes faites.

## 2. Persona : Atelier Nébula

Atelier Nébula est une PME fictive qui conçoit et fabrique des objets connectés. Elle réunit une équipe administrative et commerciale, un bureau d’études, un atelier de production et un petit espace d’accueil. Son activité grandit : elle accueille des visiteurs, utilise des équipements connectés et doit pouvoir collaborer avec un partenaire situé sur un autre site.

La direction souhaite un réseau fiable, évolutif et simple à administrer, tout en protégeant les données de l’entreprise et ses équipements. Elle ne connaît pas les choix techniques à effectuer et vous confie la conception.

## 3. Besoin à satisfaire

Proposez une topologie physique et logique répondant aux besoins de l’entreprise. La solution doit permettre :

- la communication nécessaire entre les équipes et leurs équipements ;
- la séparation des usages et des données qui ne doivent pas être accessibles à tous ;
- l’accès aux ressources internes et à Internet, ainsi qu’une connectivité justifiée avec le site partenaire ;
- la connexion d’équipements filaires, sans fil et, si cela est pertinent, d’équipements de production ou de voix ;
- l’ajout de nouveaux utilisateurs ou services sans devoir reconstruire tout le réseau ;
- l’administration et le dépannage du réseau.

Les étudiants déterminent les sites, le nombre et le rôle des équipements, les segments réseau, le plan d’adressage, les protocoles et les mesures de sécurité. Chaque choix doit être cohérent avec les besoins et les limites du projet.

## 4. Exigences de conception

La proposition doit traiter les thèmes suivants. Un thème peut être mis en œuvre dans la maquette ou, si son emploi n’est pas pertinent ou n’est pas pris en charge par l’outil choisi, faire l’objet d’une justification concise.

### Topologie et communications

- Présenter les topologies physique et logique, les équipements, les interfaces et les liens.
- Expliquer le rôle des couches OSI/TCP-IP, des adresses MAC et IP, et l’encapsulation dans les échanges représentés.
- Justifier les supports et liaisons retenus (cuivre, fibre, sans-fil ou autre support étudié).

### Commutation et segmentation

- Prévoir une segmentation logique adaptée aux différents usages, notamment au moyen de VLAN.
- Décrire les liaisons entre commutateurs et le routage nécessaire aux communications entre segments.
- Traiter les boucles de niveau 2 et les moyens de continuité ou de redondance pertinents (par exemple STP et EtherChannel, selon la topologie).
- Définir des mesures de sécurisation des ports et des équipements réseau.

### Adressage et routage

- Fournir un plan d’adressage justifié, avec sous-réseaux et passerelles.
- Examiner IPv4 et IPv6 et préciser leur utilisation dans la solution.
- Expliquer le cheminement des paquets et la lecture attendue des tables de routage.
- Choisir et justifier le routage nécessaire (statique et/ou dynamique, selon les besoins et les notions étudiées).
- Traiter l’accès à Internet, y compris NAT/PAT si la conception le nécessite.

### Services et contrôle d’accès

- Définir l’attribution de configuration IP aux clients (par exemple DHCP) et les services de nommage nécessaires (par exemple DNS).
- Mettre en place ou décrire des règles de filtrage entre les segments et vers l’extérieur au moyen d’ACL ou d’un mécanisme étudié équivalent.
- Décrire les protections utiles pour les utilisateurs, les visiteurs, les équipements connectés et l’administration.
- Examiner la disponibilité des services et des passerelles, ainsi que les conséquences d’une panne importante.

### Accès sans fil et télécommunications

- Intégrer le Wi-Fi si nécessaire, en précisant les catégories d’utilisateurs ou d’équipements qui y accèdent et les protections retenues.
- Examiner, selon le scénario choisi, la qualité de service, la voix, les communications radio, les antennes ou les autres notions de télécommunications abordées en cours.
- Justifier les notions non mises en œuvre dans la maquette, plutôt que de les ajouter sans besoin identifié.

## 5. Livrables attendus

1. **Dossier de conception** : besoins retenus, hypothèses, choix techniques et justifications.
2. **Schémas** : topologie physique et topologie logique lisibles, avec légende.
3. **Plan d’adressage** : sous-réseaux, préfixes/masques, passerelles, VLAN et affectation des usages.
4. **Maquette fonctionnelle** dans l’outil convenu (par exemple Packet Tracer), accompagnée des configurations utiles.
5. **Plan de tests** présentant les vérifications réalisées, leurs résultats et au moins un scénario de panne ou de refus d’accès attendu.
6. **Bilan** : limites de la maquette, risques restant à traiter et pistes d’évolution.

Le format de remise, le niveau de détail des configurations et les modalités de démonstration sont à convenir avec l’enseignant.

## 6. Critères de réussite

Le projet est réussi si :

- les choix répondent au persona et sont expliqués ;
- les schémas, le plan d’adressage et la maquette sont cohérents entre eux ;
- les communications autorisées fonctionnent et les communications interdites sont effectivement bloquées ou démontrées ;
- les notions de commutation, de routage, de services et de sécurité sont appliquées de façon pertinente ;
- les tests permettent de vérifier le fonctionnement et de diagnostiquer les problèmes ;
- les limites, les compromis et les notions non retenues sont explicitement présentés.

La créativité est encouragée : plusieurs architectures peuvent répondre au cahier des charges. La pertinence et la justification des choix priment sur la quantité d’équipements ou de protocoles.

## 7. Périmètre et références pédagogiques

Le projet s’appuie sur les supports présents dans le dossier `Cour`, notamment :

- `00 - Concepts de routage et commutation - rappels 26 - 27.pdf`
- `01 - Concepts de routage et commutation - chap 1 26 - 27.pdf`
- `02 - Concepts de routage et commutation - chap 2 26 - 27.pdf`
- `Telecommunication Avancé.pdf`
- les fiches de documentation sur les ACL, les tables de routage et les concepts de routage et de commutation.

Les protocoles ou fonctions effectivement disponibles dans l’outil de simulation dépendent de sa version. Toute limitation doit être signalée et compensée par une explication ou un test adapté.
