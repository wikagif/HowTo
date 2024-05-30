# Fiche de révision - Partage de dossier entre deux machines virtuelles (VM) hors domaine

## Sommaire
1. [Configuration des utilisateurs sur le serveur](#configuration-des-utilisateurs-sur-le-serveur)
2. [Configuration avancée du partage](#configuration-avancée-du-partage)
3. [Configuration des permissions NTFS](#configuration-des-permissions-ntfs)
4. [Mapping du dossier partagé comme lecteur réseau sur Windows 11](#mapping-du-dossier-partagé-comme-lecteur-réseau-sur-windows-11)
5. [Vérification de la connexion](#vérification-de-la-connexion)
6. [Exercices pratiques](#exercices-pratiques)
7. [Références et ressources complémentaires](#références-et-ressources-complémentaires)

## Configuration des utilisateurs sur le serveur

### Création d'un utilisateur local sur Windows Server 2022
1. Ouvrez **Gestion de l'ordinateur** (`compmgmt.msc`).
2. Allez dans **Utilisateurs et groupes locaux** > **Utilisateurs**.
3. Cliquez avec le bouton droit sur **Utilisateurs** et sélectionnez **Nouvel utilisateur**.
4. Créez un utilisateur avec un **nom** et un **mot de passe** identiques à ceux utilisés sur la machine Windows 11.

## Configuration avancée du partage

1. Toujours dans l'onglet **Partage**, cliquez sur **Partage avancé**.
2. Cochez **Partager ce dossier**.
3. Définissez un **nom de partage** (le nom que les autres machines utiliseront pour accéder au dossier).
4. Cliquez sur **Autorisations** pour configurer les autorisations d'accès :
   - Ajoutez l'utilisateur que vous avez créé précédemment.
   - Définissez les **autorisations** (Contrôle total, Modification, Lecture).
5. Cliquez sur **OK**, puis sur **Appliquer** et **OK**.

## Configuration des permissions NTFS

1. Allez dans l'onglet **Sécurité** des propriétés du dossier.
2. Ajoutez l'utilisateur que vous avez créé précédemment.
3. Configurez les **permissions NTFS** pour cet utilisateur (Lecture, Écriture, etc.).

## Mapping du dossier partagé comme lecteur réseau sur Windows 11
1. Ouvrez l'**Explorateur de fichiers** sur votre machine Windows 11.
2. Cliquez sur **Ce PC** dans le volet de navigation de gauche.
3. Cliquez sur **Connecter un lecteur réseau** dans le menu en haut.
4. Sélectionnez une **lettre de lecteur** (par exemple, Z:).
5. Entrez le **chemin du dossier partagé** sous la forme `\\NomDuServeur\NomDuPartage`. Par exemple, si votre serveur s'appelle Serveur2022 et le partage s'appelle Partage, entrez `\\Serveur2022\Partage`.
6. Cochez la case **Se reconnecter à l’ouverture de session** si vous souhaitez que le lecteur soit mappé automatiquement à chaque connexion.
7. Cochez **Se connecter en utilisant des informations d'identification différentes** et entrez les **informations d'identification** du serveur (nom d'utilisateur et mot de passe que vous avez créés sur le serveur).
8. Cliquez sur **Terminer**.

## Vérification de la connexion
1. Accédez à **Ce PC** dans l'Explorateur de fichiers sur votre Windows 11.
2. Vous devriez voir le lecteur réseau mappé avec la lettre que vous avez choisie. Cliquez dessus pour accéder au contenu du dossier partagé.

## Références et ressources complémentaires
- [Documentation Microsoft sur la gestion des utilisateurs](https://docs.microsoft.com/fr-fr/windows-server/identity/local-users-and-groups)
- [Guide de partage de dossier sur Windows](https://support.microsoft.com/fr-fr/windows/partager-des-fichiers-et-des-dossiers-dans-l-explorateur-de-fichiers-1fe099e9-4000-448e-8d65-bb8c7b8856de)
- [Permissions NTFS - Microsoft](https://docs.microsoft.com/fr-fr/windows/security/identity-protection/access-control/ntfs-permissions)
- [Mapping de lecteur réseau - Tutoriel](https://www.windowscentral.com/how-map-network-drive-windows-10)
