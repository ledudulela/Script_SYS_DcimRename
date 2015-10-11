#!/bin/bash
# auteur : ledudulela
# version: 1.2
# màj : 2015-08-27 18:00 
# objet: renommer des photos par lot en fonction des données exif et d'un n° incrémenté automatiquement
# dépendances: zenity, jhead
# ----------------------------------------------------------------------------------------
FMT='%Y%m%d %f (%01i)' # format proposé par défaut dans la boite de dialogue
# %Y=année %m=mois %d=jour (exif) 
# %f=nom de fichier, peut être remplacé par n'importe quelle chaine
# %03i=incrément i, affiche i en complétant à gauche par des 0 pour obtenir 3 caractères
# ----------------------------------------------------------------------------------------
files='' # liste chainée des noms de fichiers sélectionnés
OLD_IFS=$IFS
IFS='
'
for selectedFilePath in $@
do
	selectedFileType=$(file -b --mime-type "$selectedFilePath" | awk -F "/" '{print $1}')	# type du fichier à convertir (image/jpeg)
	#if [ "$selectedFileType" == "image" ] # si le fichier est de type image
	#then
		filename=$(basename $selectedFilePath)
		fileExt='.'$(basename "$selectedFilePath" | awk -F "." '{print $NF}') # extension du nom de fichier (dernier élément=$NF)
		files=$files' "'$filename'"'
	#fi
done
IFS=$OLD_IFS
# ----------------------------------------------------
if [ -z "$files" ] # si chaine de longueur nulle
then
	zenity --info --text="Opération annulée."
	exit 0
fi
# ---------------------------------------------------
txtRemplacement=$(zenity --entry  --entry-text="$FMT$fileExt" --text="Entrez le texte de remplacement :" --title="Renommer" --width=400 --height=40 2>/dev/null)
if [ $? == 1 ] # teste si le bouton [Annuler] a été cliqué
then
	exit 10
else
	if [ ${#txtRemplacement} == 0 ]  # teste si la chaine est vide
	then
		zenity --info --text="Paramètre non valide."
		exit 20
	fi
fi
# ---------------------------------------------------
#tsStart=$(date +%s)
cmdRename='jhead -n"'${txtRemplacement}'.tmp"'${files} # ajoute l'extension .tmp avant .jpg (automatiquement par jhead)
eval "$cmdRename"
#tsStop=$(date +%s)
#sec=$(($tsStop-$tsStart))

# .jpg est ajouté automatiquement avec JHEAD
# .tmp est ajouté volontairement avant ce .jpg lors du renommage
# ce qui permet de remplacer .tmp.jpg par une chaine vide afin de n'avoir que l'extension définie par l'utilisateur (dans txtRemplacement)
rename 's/\.tmp.jpg//' *.jpg # exemple: rename 's/\.jpg/.JPG/' *.jpg = remplace .jpg par .JPG pour les fichiers *.jpg
exit 0
