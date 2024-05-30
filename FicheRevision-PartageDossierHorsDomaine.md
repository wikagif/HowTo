# Fiche de révision - Partage de dossier/partition entre deux PC Windows sur un même réseau, hors domaine

## Sommaire
[I. Configuration côté serveur de fichiers](#i-configuration-côté-serveur-de-fichiers)  
[II. Configuration côté client](#ii-configuration-côté-client)  
[III. Références et ressources complémentaires](#iii-références-et-ressources-complémentaires)  

## I. Configuration côté serveur de fichiers

### Création d'un utilisateur local
1. Ouvrez **Gestion de l'ordinateur** (`compmgmt.msc`).
2. Allez dans **Utilisateurs et groupes locaux** > **Utilisateurs**.
3. Cliquez avec le bouton droit sur **Utilisateurs** et sélectionnez **Nouvel utilisateur**.
4. Créez un utilisateur avec un **nom** et un **mot de passe** identiques à ceux utilisés sur le poste client.

### Configuration avancée du partage
1. Accédez à l'**Explorateur de fichiers** sur votre Windows.
2. Créez un **nouveau dossier** ou sélectionnez un **dossier existant** que vous souhaitez partager.
3. Cliquez avec le bouton droit sur le dossier et sélectionnez **Propriétés**.
4. Dans l'onglet **Partage**, cliquez sur **Partage avancé**.
5. Cochez **Partager ce dossier**.
6. Définissez un **nom de partage** (le nom que les autres machines utiliseront pour accéder au dossier).
7. Cliquez sur **Autorisations** pour configurer les autorisations d'accès :
   - Ajoutez l'utilisateur que vous avez créé précédemment.
   - Définissez les **autorisations** (contrôle total, modification, lecture).
8. Cliquez sur **OK**, puis sur **Appliquer** et **OK**.

### Configuration des permissions NTFS
1. Allez dans l'onglet **Sécurité** des propriétés du dossier.
2. Ajoutez l'utilisateur que vous avez créé précédemment.
3. Configurez les **permissions NTFS** pour cet utilisateur (lecture, écriture, etc.).

## II. Configuration côté client

### Mapping du dossier partagé comme lecteur réseau
1. Ouvrez l'**Explorateur de fichiers**.
2. Séléctionnez **Ce PC** dans le menu déroulant de la barre d'adresse.
3. Cliquez sur **Connecter un lecteur réseau** dans le menu en haut de la fenêtre.
4. Sélectionnez une **lettre de lecteur** (par exemple, Z:).
5. Entrez le **chemin du dossier partagé** sous la forme `\\NomDuServeur\NomDuPartage`.
6. Cochez la case **Se reconnecter à l’ouverture de session** si vous souhaitez que le lecteur soit mappé automatiquement à chaque connexion.
7. Cochez **Se connecter en utilisant des informations d'identification différentes** et entrez les **informations d'identification** (nom d'utilisateur et mot de passe créés plus haut).
8. Cliquez sur **Terminer**.

### Vérification de la connexion
1. Accédez à **Ce PC** dans l'Explorateur de fichiers.
2. Vous devriez voir le lecteur réseau mappé avec la lettre que vous avez choisie. Cliquez dessus pour accéder au contenu du dossier partagé.

## III. Références et ressources complémentaires
- [Documentation Microsoft sur la gestion des utilisateurs locaux sur Windows Server](https://docs.microsoft.com/fr-fr/windows-server/identity/local-users-and-groups)
- [Guide officiel de partage de dossier sur Windows par Microsoft](https://support.microsoft.com/fr-fr/windows/partager-des-fichiers-et-des-dossiers-dans-l-explorateur-de-fichiers-1fe099e9-4000-448e-8d65-bb8c7b8856de)
- [Permissions NTFS - Documentation officielle de Microsoft](https://docs.microsoft.com/fr-fr/windows/security/identity-protection/access-control/ntfs-permissions)
- [Tutoriel sur le mapping de lecteur réseau par Windows Central](https://www.windowscentral.com/how-map-network-drive-windows-10)
