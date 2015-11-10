# Script_Sys_DcimRename
objet: renommer des photos par lot en fonction des données exif et d'un n° incrémenté automatiquement
dépendances: zenity, jhead

FMT='%Y%m%d %f (%01i)' format proposé par défaut dans la boite de dialogue
%Y=année %m=mois %d=jour (exif) 
%f=nom de fichier, peut être remplacé par n'importe quelle chaine
%03i=incrément i, affiche i en complétant à gauche par des 0 pour obtenir 3 caractères
