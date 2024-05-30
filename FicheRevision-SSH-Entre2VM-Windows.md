# Fiche de révision - Se connecter en SSH entre deux VM Windows

## I. Installer et lancer OpenSSH.Server sur VM1 (serveur)

1. Vérifier la présence de OpenSSH.Server depuis PowerShell :

     ```Powershell
         Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
     ```
     Cette commande vérifie si le composant OpenSSH.Server est installé sur le système. Si le composant est absent, la commande ne retournera aucun résultat.
      
2. Si absent, installer OpenSSH.Server :
      - Pour Windows 11 : 
        Accédez à **System > Optional features** puis ajoutez OpenSSH.Server.

      - Pour autres versions de Windows :
        Accédez à **Apps > Optional features** puis ajoutez OpenSSH.Server.  

3. Dans PowerShell, démarrer le service et le configurer pour qu'il se lance automatiquement :
   
   ```powershell
      Start-Service sshd
      Set-Service -Name sshd -StartupType 'Automatic'
   ```
   
      Ces commandes démarrent le service OpenSSH.Server et le configurent pour qu'il se lance automatiquement au démarrage du système.  

## II. Créer et configurer le réseau entre les 2 VM

1. Dans Virtual Network Editor, créer et configurer un réseau Vmnet libre en Host-Only :
    - Ouvrez **Virtual Network Editor** depuis VMware Workstation.
    - Créez un nouveau réseau et sélectionnez **Host-Only**.  

2. Dans VMWare Workstation, configurer chaque VM pour utiliser le Vmnet créé :
      - Ouvrez les paramètres de chaque VM.
      - Sous l'onglet **Network Adapter**, sélectionnez le Vmnet précédemment créé.  

## III. Passer de réseau public à privé sur les 2 VM

1. Dans l'explorateur Windows des deux VM :
      - Accédez à **Network**.
      - Lorsque le bandeau jaune apparaît, cliquez dessus pour basculer le réseau de public à privé.
      - Assurez-vous que les machines sont visibles sur le réseau.  

## IV. Se connecter à la VM1

1. Depuis CMD, noter l'IP de VM1 avec :
      ```batch
      ipconfig
      ```
      Recherchez l'adresse IPv4 de l'adaptateur réseau correspondant au Vmnet configuré.  

3. Depuis VM2, tester l'accès à VM1 avec :
      ```batch
      ping [adresse IP de VM1]
      ```  

4. Ensuite, se connecter avec la commande :
      ```batch
      ssh -v NomCompteUserServeur@[adresse IP de VM1]
      ```
      Utilisez `-v` pour le mode verbose afin d'obtenir plus de détails sur la connexion.  

5. Si problème, configurer le pare-feu depuis PowerShell pour autoriser les connexions SSH :
      ```powershell
      New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
      ```
      Cette commande crée une règle de pare-feu pour autoriser les connexions entrantes sur le port 22, utilisé par le service SSH.
