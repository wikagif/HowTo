# Fiche de Révision : Adressage Réseau et Sous-Réseaux en IPv4

## Sommaire
1. [Introduction à l'Adressage Réseau](#introduction-à-ladressage-réseau)
2. [L'Adresse Réseau](#ladresse-réseau)
3. [Nombre d'Adresses Attribuables](#nombre-dadresses-attribuables)
4. [Adresse de Broadcast](#adresse-de-broadcast)
5. [Notation CIDR (Classless Inter-Domain Routing)](#notation-cidr-classless-inter-domain-routing)
6. [Exercices Pratiques](#exercices-pratiques)
7. [Références et Ressources Complémentaires](#références-et-ressources-complémentaires)

## Introduction à l'Adressage Réseau

L'adressage réseau en IPv4 est crucial pour la structuration et la gestion des réseaux IP. Il permet de définir des plages d'adresses pour les appareils connectés et de faciliter la communication entre eux.

## L'Adresse Réseau

### Définition
L'adresse réseau est obtenue en appliquant un masque de sous-réseau à une adresse IP. Les bits à 1 de l'adresse IP et du masque de sous-réseau déterminent l'adresse réseau.

### Calcul de l'Adresse Réseau
- **Exemple :**
  - Adresse IP : 192.168.1.10
  - Masque de sous-réseau : 255.255.255.0
  - Calcul : (192.168.1.10) AND (255.255.255.0) = 192.168.1.0

- **En binaire :**

|                  | Octet 1  | Octet 2  | Octet 3  | Octet 4  |
|------------------|----------|----------|----------|----------|
| **Adresse IP**   | 11000000 | 10101000 | 00000001 | 00001010 |
| **Masque**       | 11111111 | 11111111 | 11111111 | 00000000 |
| **Adresse Réseau** | 11000000 | 10101000 | 00000001 | 00000000 |

## Nombre d'Adresses Attribuables

### Calcul
Le nombre d'adresses attribuables est déterminé par les bits à 0 du masque de sous-réseau.
- **Formule :** `2^n - 2` où `n` est le nombre de bits à 0 dans le masque de sous-réseau.
- **Exemple :**
  - Masque de sous-réseau : 255.255.255.252
  - En binaire : 11111111.11111111.11111111.11111100
  - Nombre de bits à 0 : 2
  - Nombre d'adresses attribuables : `2^2 - 2 = 4 - 2 = 2`

### Explication
Le "-2" est utilisé pour soustraire l'adresse réseau et l'adresse de broadcast, qui ne peuvent pas être attribuées à des hôtes.

## Adresse de Broadcast

### Définition
L'adresse de broadcast permet de communiquer avec tous les hôtes d'un réseau donné.

### Calcul de l'Adresse de Broadcast
Remplacer les bits à 0 du masque de sous-réseau par des 1 dans l'adresse IP.
- **Exemple :**
  - Adresse IP : 192.168.1.10
  - Masque de sous-réseau : 255.255.255.252
  - Calcul : 192.168.1.11

- **En binaire :**

|                  | Octet 1  | Octet 2  | Octet 3  | Octet 4  |
|------------------|----------|----------|----------|----------|
| **Adresse IP**   | 11000000 | 10101000 | 00000001 | 00001010 |
| **Masque**       | 11111111 | 11111111 | 11111111 | 11111100 |
| **Adresse de Broadcast** | 11000000 | 10101000 | 00000001 | 00001111 |

## Notation CIDR (Classless Inter-Domain Routing)

### Définition
La notation CIDR est une méthode de spécification des masques de sous-réseau de manière concise.

### Compréhension et Utilisation
- **Exemple :** `/25` signifie que les 25 premiers bits de l'adresse sont des 1, les bits restants sont des 0.
- **Conversion :**
  - `/25` : 11111111.11111111.11111111.10000000
  - En décimal : 255.255.255.128

- **Application :**

|                  | Octet 1  | Octet 2  | Octet 3  | Octet 4  |
|------------------|----------|----------|----------|----------|
| **/25**          | 11111111 | 11111111 | 11111111 | 10000000 |
| **255.255.255.128** |

  - Adresse IP : 192.168.1.0/25
  - Plage d'adresses : de 192.168.1.1 à 192.168.1.126
  - Adresse de broadcast : 192.168.1.127

## Exercices Pratiques

### Calculer l'Adresse Réseau
- **Adresse IP :** 172.16.5.10
- **Masque de sous-réseau :** 255.255.255.240
- **Solution :**
  - Adresse IP en binaire : 10101100.00010000.00000101.00001010
  - Masque : 11111111.11111111.11111111.11110000
  - Adresse réseau : 10101100.00010000.00000101.00000000 (172.16.5.0)

### Calculer le Nombre d'Adresses Attribuables
- **Masque de sous-réseau :** 255.255.255.240
- **Solution :**
  - Nombre de bits à 0 : 4
  - Nombre d'adresses attribuables : `2^4 - 2 = 16 - 2 = 14`

### Calculer l'Adresse de Broadcast
- **Adresse IP :** 172.16.5.10
- **Masque de sous-réseau :** 255.255.255.240
- **Solution :**
  - Adresse IP en binaire : 10101100.00010000.00000101.00001010
  - Masque : 11111111.11111111.11111111.11110000
  - Adresse de broadcast : 10101100.00010000.00000101.00001111 (172.16.5.15)

### Conversion en Notation CIDR
- **Masque de sous-réseau :** 255.255.255.192
- **Solution :**
  - En binaire : 11111111.11111111.11111111.11000000
  - Notation CIDR : /26

## Références et Ressources Complémentaires

- **RFC 1918 :** Adressage IP privé.
- **Documentation Cisco :** Guide sur le VLSM (Variable Length Subnet Mask).
- **Outils en ligne :** Calculateur de sous-réseaux IP.
