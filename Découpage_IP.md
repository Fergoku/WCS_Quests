

## Découpage Symétrique

Réseau 172.16.1.0/24 à découper en 4 sous-réseaux équivalents.

Nous prenons donc en compte le réseau ayant le nombre déquipements le plus grand, ici le réseau du pôle informatique avec 50 machines.

Dans la table des puissances on prend le nombre supérieur à 50, 64 qui est 2 à la puissance 6.

Nous découperons donc notre réseau en 4 sous-réseaux de 62 machines + 1 adresse de réseau et 1 adresse de broadcast pour un total de 64 adresses IP.

Pour trouver le CIDR on prend la puissance (ici 6) que l'on soustrait au nombre de bits dans une adresse IP (32) : 32-6=26

Le CIDR du réseau sera donc 26, équivalent à 255.255.255.192


|                    | Adresse Réseau  | Adresse de Broadcast | Adresse de début de plage | Adresse de fin de plage |
| ------------------ | --------------- | ----------------- | -------------- | ------------ |
| Pôle Info          | 172.16.1.0 /26  | 172.16.1.63       | 172.16.1.1     | 172.16.1.62  |
| Pôle developpement | 172.16.1.64/26  | 172.16.1.127      | 172.16.1.65    | 172.16.1.126 |
| Pôle administratif | 172.16.1.129/26 | 172.16.1.191      | 172.16.1.129   | 172.16.1.190 |
| Pôle technicien    | 172.16.1.192/26 | 172.16.1.255      | 172.16.1.193   | 172.15.1.24  |
|                    |                 |                   |                |              |



## Découpage Asymétrique

On à 4 pôle à découper de manière asymétrique.

Pour chaque pôle on recherche la puissance de 2 supérieur au nombre d’équipements prévus pour chaque pôle :

Pôle informatique : 2 puissance 6 soit 64 adresses dont deux pour le réseau et le broadcast (62).

Pôle développement : 2 puissance 4 soit 16 adresses dont deux pour le réseau et le broadcast (14).

Pôle Administratif : 2 puissance 5 soit 32 adresses dont deux pour le réseau et le broadcast (30).

Pôle technicien : 2 puissance 4 soit 16 adresses dont deux pour le réseau et le broadcast (14).

Pour le CIDR, on se réfère au tableau des puissances de 2.

Pôle informatique : 32 - 6 = /26

Pôle developpement : 32 - 4 = /28

Pôle administratif : 32 - 5 = /27

Pôle technicien : 32- 5 =/2


|                    | Adresse Réseau  | Adresse de Broadcast | Adresse de début de plage | Adresse de fin de plage |
| ------------------ | --------------- | ----------------- | -------------- | ------------ |
| Pôle Informatique  | 172.16.1.0/26   | 172.16.1.63       | 172.16.1.1     | 172.16.1.62  |
| Pôle developpement | 172.16.1.64/28  | 172.16.1.78       | 172.16.1.65    | 172.16.1.77  |
| Pôle administratif | 172.16.1.80/27  | 172.16.1.109      | 172.16.1.81    | 172.16.1.108 |
| Pôle technicien    | 172.16.1.112/27 | 172.16.1.140      | 172.16.1.113   | 172.15.1.139 |

