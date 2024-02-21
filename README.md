# dmenu_mnt
- Il faut modifier la première ligne si /bin/python n'existe pas (remplacer par /bin/python3 par exemple)
- Il faut pouvoir exécuter mount, umount et rmdir avec sudo sans mot de passe
- Le script explose si une partition est montée à deux endroits différents
- Les erreurs sont passées sous le tapis pour l'instant

Pour exécuter des commandes avec sudo sans mot de passe, il faut soit modifier /etc/sudoers avec la commande visudo (à la main ça marche aussi) soit modifier l'un des fichiers dans /etc/sudoers.d (si le dossier existe c'est probablement ici qu'il faut regarder)\

Mon /etc/sudoers.d/wheel:\
%wheel ALL=(ALL:ALL) ALL\
%wheel ALL=(ALL:ALL) NOPASSWD:/bin/rmdir\
%wheel ALL=(ALL:ALL) NOPASSWD:/bin/mount\
%wheel ALL=(ALL:ALL) NOPASSWD:/bin/umount\

En gros:\
%groupe ALL=(ALL:ALL) ALL - le groupe wheel peut tout faire avec sudo\
bonjour ALL=(ALL:ALL) NOPASSWD:/bin/jojo - bonjour peut exécuter jojo sans mot de passe\
bernard ALL=(ALL:ALL) NOPASSWD:ALL - bernard est le maître du monde\
