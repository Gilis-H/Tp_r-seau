# Correspondance des liaisons physiques

Les interfaces indiquées sont celles communiquées pour la topologie Packet Tracer. L’adressage IP reste à définir.

| Équipement | Interface locale | Équipement distant | Interface distante |
|---|---|---|---|
| R1 | Gig0/0 | Multilayer Switch1 | Gig1/0/4 |
| R1 | Gig0/1 | R2 | Gig0/1 |
| R1 | Gig0/2 | R3 | Gig0/1 |
| Multilayer Switch1 | Gig1/0/3 | Multilayer Switch2 | Gig1/0/3 |
| Multilayer Switch1 | Gig1/0/2 | SW-1 | Fa0/5 |
| Multilayer Switch1 | Gig1/0/1 | SW-2 | Fa0/2 |
| Multilayer Switch2 | Gig1/0/2 | SW-1 | Fa0/4 |
| Multilayer Switch2 | Gig1/0/1 | SW-2 | Fa0/1 |
| SW-1 | Fa0/1 | PC-1 | Fa0 |
| SW-1 | Fa0/2 | PC-2 | Fa0 |
| SW-1 | Fa0/3 | PC-3 | Fa0 |
| R2 | Gig0/2 | SW-3 | Fa0/1 |
| SW-3 | Fa0/3 | PC-Dragster | Fa0 |
| R3 | Gig0/0 | SW-4 | Fa0/1 |
| SW-4 | Fa0/3 | PC-Externe | Fa0 |
| SW-4 | Fa0/2 | Server-Externe | Fa0 |
