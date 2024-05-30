# Fiche de révision - Se connecter en SSH entre deux machines virtuelles Windows (VMWare Workstation)

## Sommaire
- [I. Installer et lancer OpenSSH.Server sur VM1 (serveur)](#i-installer-et-lancer-opensshserver-sur-vm1-serveur)  
- [II. Créer et configurer le réseau entre les deux VM](#ii-créer-et-configurer-le-réseau-entre-les-deux-vm)  
- [III. Passer de réseau public à privé sur les deux VM](#iii-passer-de-réseau-public-à-privé-sur-les-deux-vm)  
- [IV. Se connecter à la VM1 depuis la VM2](#iv-se-connecter-à-la-vm1-depuis-la-vm2)
- [V. Références et ressources complémentaires](#v-références-et-ressources-complémentaires)

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

## II. Créer et configurer le réseau entre les deux VM

1. Dans Virtual Network Editor, créer et configurer un réseau Vmnet libre en Host-Only :
    - Ouvrez **Virtual Network Editor** depuis VMware Workstation.
    - Créez un nouveau réseau et sélectionnez **Host-Only**.  

2. Dans VMWare Workstation, configurer chaque VM pour utiliser le Vmnet créé :
      - Ouvrez les paramètres de chaque VM.
      - Sous l'onglet **Network Adapter**, sélectionnez le Vmnet précédemment créé.  

## III. Passer de réseau public à privé sur les deux VM

1. Dans l'explorateur Windows des deux VM :
      - Accédez à **Network**.
      - Lorsque le bandeau jaune apparaît, cliquez dessus pour basculer le réseau de public à privé.
      - Assurez-vous que les machines sont visibles sur le réseau.  

## IV. Se connecter à la VM1 depuis la VM2

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

## V. Références et ressources complémentaires
- [Documentation Microsoft sur OpenSSH (microsoft.com)](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) - Instructions officielles pour installer et utiliser OpenSSH sur Windows.
- [Guide de configuration de réseau dans VMware Workstation (vmware.com)](https://www.vmware.com/support/ws5/doc/ws_net_configurations_changing_bridged.html) - Tutoriel pour configurer différents types de réseaux dans VMware Workstation.
- [Tutoriel pour changer un réseau de public à privé sur Windows (support.microsoft.com)](https://support.microsoft.com/en-us/windows/make-a-wi-fi-network-public-or-private-in-windows-10-92382155-d091-48ff-878b-0a6d0d4b74e6) - Guide pour basculer un réseau de public à privé sur Windows 10.
- [Guide de connexion SSH sous Windows (ssh.com)](https://www.ssh.com/academy/ssh/command) - Tutoriel détaillé sur l'utilisation de la commande SSH sous Windows.
- [Configuration du pare-feu Windows pour OpenSSH (microsoft.com)](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-inbound-port-rule) - Documentation officielle pour créer une règle de pare-feu permettant les connexions SSH sur Windows.
