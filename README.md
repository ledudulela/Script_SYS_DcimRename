# Script DcimRename

objet: renommer des photos par lot en fonction des données exif et d'un n° incrémenté automatiquement

dépendances: zenity, jhead

![screenshot](https://github.com/ledudulela/Script_SYS_DcimRename/blob/master/dcimrename.jpg)

--

FMT = '%Y%m%d %f (%01i)' format proposé par défaut dans la boite de dialogue

%Y=année %m=mois %d=jour (exif) 

%f = nom de fichier, peut être remplacé par n'importe quelle chaine

%02i = incrémente i, affiche i en complétant à gauche par des 0, pour obtenir un chiffre sur 2 caractères

--

Le script est à placer dans le répertoire /usr/local/bin/ (retirez le .sh s'il existe ou créer un lien symbolique sans .sh)

Bien que prévu pour être exécuté en ligne de commandes, il peut aussi être appelé depuis le gestionnaire de fichiers.

Par exemple pour Caja, en créant un lien symbolique vers /usr/local/bin/dcimrename

dans le répertoire /home/utilisateur/.config/caja/scripts

et en nommant ce lien symbolique "Renommer les photos", il apparaitra en faisant un
 clic-droit sur une sélection de photos dans Caja, un sous-menu Scripts > Renommer les photos

*ln -s "/usr/local/bin/dcimrename" "$HOME/.config/caja/scripts/Renommer les photos"*

