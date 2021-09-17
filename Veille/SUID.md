# SUID sous Linux
    Le SUID sous linux est une permission qui permet, lorsquel est activé, à un executable de fournir les même droits que le propriétaire.
    Il fait parti des permissions étendue avec la représentation "s" avec une valeur octale de 4000 (sudo chmod +4000 /path) active le SUID 

# Comment ça marche ?
    Pour voir les permissions d'un dossier ou d'un fichier: 
        - $ stat path
        - $ ls -l (pour lister les fichiés dans le répertoire actuelle et leurs permissions)

    Acitvé le SUID:
        - $ mkdir test
        - $ ls -l folderTest
        -   out: -rwxr-xr-x. 1 root root 62792 Aug 17 09:20 folderTest
        - $ sudo chmod +4000 folderTest
        - $ ls -l foldetTest
        -   out: -rwsr-xr-x. 1 root root 62792 Aug 17 09:20 folderTest



# Sources
    https://linux.goffinet.org/administration/securite-locale/permissions-linux/