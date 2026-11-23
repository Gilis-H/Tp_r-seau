# Packet Tracer 3.4.5 — Configurer les trunks

[Activité Packet Tracer (.pka)](./3.4.5%20Packet%20Tracer%20-%20Configure%20Trunks.pka) · [Énoncé Cisco NetAcad (PDF)](https://www.netacad.com/content/srwe/1.0/courses/content/m3/en-US/assets/3.4.5-packet-tracer---configure-trunks.pdf)

Garde cette fiche ouverte à côté de Packet Tracer. Dans l’activité, la fenêtre **Instructions** permet de retrouver l’étape en cours. Note ici les sorties et les résultats qui expliquent tes choix.

## Objectif

Suivre le trafic d’un même VLAN entre S2 et S3 via S1, puis vérifier le fonctionnement des trunks 802.1Q et du VLAN natif.

## Repères dans la topologie

| Liaison | Port sur S1 | Port à l’autre extrémité |
|---|---|---|
| S1–S2 | Gi0/1 | S2 Gi0/1 |
| S1–S3 | Gi0/2 | S3 Gi0/2 |

| VLAN | Poste sur S2 | Poste sur S3 | Port d’accès sur chaque switch |
|---:|---|---|---|
| 10 | PC1 · `172.17.10.21/24` | PC4 · `172.17.10.24/24` | Fa0/11 |
| 20 | PC2 · `172.17.20.22/24` | PC5 · `172.17.20.25/24` | Fa0/18 |
| 30 | PC3 · `172.17.30.23/24` | PC6 · `172.17.30.26/24` | Fa0/6 |

## Partie 1 — Vérifier les VLAN

### Étape 1 — Afficher les VLAN existants

1. Sur S1, affiche les VLAN avec `show vlan brief`. Relève leur nombre et le VLAN auquel appartiennent les ports d’accès.
2. Sur S2 et S3, utilise la même commande et compare l’affectation des ports d’accès avec le tableau.

### Étape 2 — Vérifier la connectivité initiale

Sur les PC, ouvre **Desktop → Command Prompt** et teste les trois paires du tableau. Note les résultats dans la colonne « Avant les trunks ».

**Indice.** Pour PC1 → PC4, suis le VLAN 10 de bout en bout. Quelles interfaces la trame doit-elle traverser entre les deux ports d’accès ?

## Partie 2 — Configurer les trunks

### Étape 1 — Configurer les trunks et le VLAN natif sur S1

1. Configure les liaisons Gi0/1 et Gi0/2 de S1 en trunk.
2. Définis le **VLAN 99** comme VLAN natif sur ces deux ports. Attends que les liens se stabilisent, puis relève les messages CDP et refais les pings. Qu’ont en commun les VLAN des postes testés et le VLAN natif ? Compare leurs numéros et demande-toi quelles trames circulent avec une étiquette 802.1Q.

### Étape 2 — Vérifier les trunks sur S2 et S3

Sur S2 et S3, utilise `show interfaces trunk` pour vérifier si DTP a établi les trunks. Quels VLAN actifs sont autorisés à traverser chaque liaison ?

### Étape 3 — Corriger l’écart de VLAN natif sur S2 et S3

1. Repère les interfaces concernées sur S2 et S3 et règle leur VLAN natif sur 99.
2. Vérifie le VLAN natif affiché par `show interfaces trunk`.

### Étape 4 — Vérifier la configuration sur S2 et S3

1. Vérifie le VLAN natif avec `show interfaces <port> switchport`.
2. Affiche les VLAN avec `show vlan`. Pour expliquer pourquoi Gi0/1 sur S2 a disparu de la liste des ports du VLAN 1, compare son mode opérationnel avant et après la configuration.

**Indice.** Une liaison trunk peut transporter plusieurs VLAN. Sur un trunk 802.1Q, le trafic du VLAN natif circule généralement sans étiquette.

## Mes résultats

| Test | Avant les trunks | Après configuration sur S1 |
|---|---|---|
| PC1 → PC4 | À relever | À relever |
| PC2 → PC5 | À relever | À relever |
| PC3 → PC6 | À relever | À relever |

- **Message CDP observé et ports concernés** — à relever.
- **VLAN autorisés et actifs sur les trunks** — à relever.
- **Explication d’un résultat de ping et du changement observé dans `show vlan`** — à compléter.
