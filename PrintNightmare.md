# Print Nightmare c'est quoi ?
    Print Nightmare est un exploit qui s'execute sur Windows 7 et c'est version ultérieur, il permet à l'attaquant d'exécuter du code sur une machine cible, avec un niveau d'accées le plus élevé.
    L'exploit utilise une faille du service service Windows Print Spooler qui permet de gérer une file d'attente des impression en simultané

# Les risques encourue par cet faille sont:
    Installation de programmes, modification ou vole de données, création et modification d'utilsateur
    
# En quoi consiste cet faille 
  La faille PrintNightmare utilise une fonction appeler RpcAddPrinterDrive provenant de RPC, qui permet a un client d'installer des pilotes

# S'en protéger
  Tout d'abord désactiver le service File d'attente d'impression:
    Dans le powershell en admin: 
    - Get-Service -Name Spooler
    - Stop-Service -Name Spooler -Force
    - Set-Service -Name Spooler -StartupType Disabled
  
  Vérifier le registre pour les valuer:
    - HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT\Printers\PointAndPrint
    - NoWarningNoElevationOnInstall = 0 (DWORD) ou valeur non définie (paramètre par défaut)
    - UpdatePromptSettings = 0 (DWORD) ou valeur non définie (paramètre par défaut)
  Si la clé NoWarningNoElevationOnInstall a la valeur 1, votre système est vulnérable.

# Sources
  - https://www.journaldugeek.com/2021/07/09/windows-le-patch-contre-la-faille-critique-printnightmare-est-disponible/
  - https://cyberwatch.fr/actualite/cve-2021-34527-comment-identifier-et-neutraliser-la-vulnerabilite-printnightmare/