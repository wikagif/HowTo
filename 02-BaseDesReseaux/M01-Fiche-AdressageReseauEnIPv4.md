# Fiche - Adressage réseau et sous-réseaux en IPv4

## Sommaire
[I. Introduction à l'adressage réseau](#i-introduction-à-ladressage-réseau)  
[II. L'adresse réseau](#ii-ladresse-réseau)  
[III. Nombre d'adresses attribuables](#iii-nombre-dadresses-attribuables)  
[IV. Adresse de Broadcast](#iv-adresse-de-broadcast)  
[V. Notation CIDR (Classless Inter-Domain Routing)](#v-notation-cidr-classless-inter-domain-routing)  
[VI. Exercices pratiques](#vi-exercices-pratiques)  
[VII. Références et ressources complémentaires](#vii-références-et-ressources-complémentaires)  

---

## I. Introduction à l'adressage réseau

- L'adressage réseau en IPv4 est crucial pour la structuration et la gestion des réseaux IP. Il permet de définir des plages d'adresses pour les appareils connectés et de faciliter la communication entre eux.

- A noter : Pour qu'un masque de sous-réseau soit considéré comme valide, une fois converti en binaire, il doit avoir des bits de 1 consécutifs suivis de bits de 0 consécutifs. Les masques sont utilisés pour structurer des réseaux en sous-réseaux de tailles spécifiques selon les besoins du réseau.

## II. L'adresse réseau

### Définition
L'adresse réseau est obtenue en appliquant un masque de sous-réseau à une adresse IP. Les bits à 1 de l'adresse IP et du masque de sous-réseau déterminent l'adresse réseau.

### Calcul de l'adresse réseau
- **Exemple :**
  - Adresse IP : 192.168.1.10
  - Masque de sous-réseau : 255.255.255.0
  - Calcul : (192.168.1.10) AND (255.255.255.0) = 192.168.1.0

- **En binaire :**

|                    | Octet 1  | Octet 2  | Octet 3  | Octet 4  |
|--------------------|----------|----------|----------|----------|
| **Adresse IP**     | 11000000 | 10101000 | 00000001 | 00001010 |
| **Masque**         | 11111111 | 11111111 | 11111111 | 00000000 |
| **Adresse Réseau** | 11000000 | 10101000 | 00000001 | 00000000 |

## III. Nombre d'adresses attribuables

### Calcul
Le nombre d'adresses attribuables est déterminé par les bits à 0 du masque de sous-réseau.
- **Formule :** $2^n$ - 2 où $^n$ est le nombre de bits à 0 dans le masque de sous-réseau.

- **Exemple :**
  - Masque de sous-réseau : 255.255.255.252
  - En binaire : 11111111.11111111.11111111.11111100
  - Nombre de bits à 0 : 2
  - Nombre d'adresses attribuables : $2^2$ - 2 = 2

### Explication
Le "-2" est utilisé pour soustraire l'adresse réseau et l'adresse de broadcast, qui ne peuvent pas être attribuées à des hôtes.

## IV. Adresse de Broadcast

### Définition
L'adresse de broadcast permet de communiquer avec tous les hôtes d'un réseau donné.

### Calcul de l'adresse de broadcast

1. Écrivez l'adresse IP donnée en format binaire.
2. Ecrivez le masque de sous-réseau sous forme binaire.
3. Écrivez l'inverse du masque de sous-réseau sous forme binaire.
4. Effectuez l'opération de OU logique (OR) entre les octets de l'adresse IP et l'inverse du masque de sous-réseau.
5. Reconvertissez le résultat obtenu en format décimal pour obtenir l'adresse de broadcast.

- **Exemple :**
  - Adresse IP : 192.168.1.10
  - Masque de sous-réseau : 255.255.255.252
  - Adresse de broadcast calculée : 192.168.1.15

- **En binaire :**

|                                           | Octet 1  | Octet 2  | Octet 3  | Octet 4  |
|-------------------------------------------|----------|----------|----------|----------|
| **Adresse IP**                            | 11000000 | 10101000 | 00000001 | 00001010 |
| **Inverse du masque de sous-réseau**      | 00000000 | 00000000 | 00000000 | 00000011 |
| **Adresse de Broadcast**                  | 11000000 | 10101000 | 00000001 | 00001111 |

## V. Notation CIDR (Classless Inter-Domain Routing)

### Définition
La notation CIDR est une méthode de spécification des masques de sous-réseau de manière concise.

### Compréhension et utilisation
- **Exemple :** `/25` signifie que les 25 premiers bits de l'adresse sont des 1, les bits restants sont des 0.
- **Conversion :**
  - `/25` : 11111111.11111111.11111111.10000000
  - En décimal : 255.255.255.128

- **Application :**

|                     | Octet 1  | Octet 2  | Octet 3  | Octet 4  |
|---------------------|----------|----------|----------|----------|
| **/25**             | 11111111 | 11111111 | 11111111 | 10000000 |
| **255.255.255.128** |      255 |      255 |      255 |      128 |

  - Adresse IP : 192.168.1.0/25
  - Plage d'adresses : de 192.168.1.1 à 192.168.1.126
  - Adresse de broadcast : 192.168.1.127

## VI. Exercices pratiques

### Calculer l'adresse Réseau
- **Adresse IP :** 172.16.5.10
- **Masque de sous-réseau :** 255.255.255.240

- **Solution :**
  - Adresse IP en binaire : 10101100.00010000.00000101.00001010
  - Masque : 11111111.11111111.11111111.11110000
  - Adresse réseau : 10101100.00010000.00000101.00000000 (172.16.5.0)

### Calculer le nombre d'adresses attribuables
- **Masque de sous-réseau :** 255.255.255.240

- **Solution :**
  - Nombre de bits à 0 : 4
  - Nombre d'adresses attribuables : $2^4$ - 2 = 16 - 2 = 14

### Calculer l'Adresse de Broadcast
- **Adresse IP :** 172.16.5.10
- **Masque de sous-réseau :** 255.255.255.240

- **Solution :**
  - Adresse IP en binaire : 10101100.00010000.00000101.00001010
  - Masque : 11111111.11111111.11111111.11110000
  - Adresse de broadcast : 10101100.00010000.00000101.00001111 (172.16.5.15)

### Conversion en notation CIDR
- **Masque de sous-réseau :** 255.255.255.192
- **Solution :**
  - En binaire : 11111111.11111111.11111111.11000000
  - Notation CIDR : /26

## VII. Références et ressources complémentaires

- [RFC 1918 : Documentation officielle sur l'utilisation des adresses IP privées (ietf.org)](https://tools.ietf.org/html/rfc1918)
- [Documentation Cisco : Guide sur le VLSM (Variable Length Subnet Mask) (cisco.com)](https://www.cisco.com/c/en/us/support/docs/ip/ip-routing/16453-7.html)
- [Outil en ligne : Calculateur de sous-réseaux IP (subnet-calculator.org)](https://www.subnet-calculator.org/)
