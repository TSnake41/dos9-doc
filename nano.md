# Commande NANO - GNU Nano #

**GNU Nano** est un éditeur de texte en console développé par le projet GNU. 
Cette éditeur est **multiplate-forme, et libre**, c'est pourquoi il est 
intégré dans [Dos9](dos9).

**Nano** offre de nombreuses fonctionnalitées, notament la possibilté de 
colorer syntaxiquement un code source. A cette occasion, nous avons modifié 
**Nano** afin qu'il puisse colorer les scripts batch.

**Nano** est distribué par le projet **GNU** sous licnce libre **GNU GPL 
v3\)**.

## Synopsis ##

     NANO [options ...] fichier

Lance l'édition d'un fichier.

* **fichier** : le fichier à éditer.

* **options...** : une ou plus des options de la partie 'option'.

## Options ##

     -h
     --help

Affiche un message d'aide \(en anglais sur **WINDOWS**\).

     +LIGNE,COLONNE

Commence l'édition à la ligne **LIGNE** et à la colonne **COLONNE**.

     -A
     --smarthome

Active la touche **smart home**

      -B
     --backup

Fait des sauvegardes des fichiers existants.

     -C dir
     --backupdir=dir

Place les fichiers à sauvegarder dans le dossier **dir**.

     -D
     --boldtext

Utilise du texte gras plutôt que du texte inversé \(coluleur de fond et du 
texte\)

     -E
     --tabstospace

Convertit les tabulations en espaces.

     -F
     --multibuffer

Active les buffers de fichiers multiples.

     -H
     --historylog

Sauvegard et lit l'historique des recherches et remplacements.

     -I
     --ignorercfiles

Ne prends pas en compte le fichier nano.rc

     -K
     --rebindkeypad

Résoud le problème de la confusion des touches du clavier numérique

     -L
     --nonewlines

N'ajoute pas de nouvelles lignes a la fin des fichiers.

     -N
     --noconvert

Ne convertit pas les fichiers au formats DOS/WINDOWS ou MAC

     -O
     --morespace

Utilise plus de ligne pour l'édition.

     -Q str
     --quotestr=str

Chaine de citation.

     -R
     --restricted

Utilise le mode restreint.

     -S
     --smooth

Le fichier défile ligne par ligne plutôt que demi écran par demi écran

     -T n
     --tabsize=n

Fixe la largeur d'une tabulation à **n** colonnes.

     -U
     --quickblank

Change la couleur de la barre d'accès rapide en blanc.

     -V
     -version

Affiche les informattions de versions puis quitte.

     -W
     --wordbounds

Détecte les limites de mots plus efficatement

     -Y langage
     --syntax=langage

Séléctionne le langage **langage** pour la coloration syntaxique.

     -c
     --const

Affiche la position du curseur tout le temps.

     -d
     --rebinddelete

Règle le problème de confusion des touches SUPPR.

     -i
     --autoindent

Indente les nouvelles lignes automatiquement.

     -k
     --cut

Coupe depuis le curseur jusqu'a la fin de la ligne.

     -l
     --nofollow

Ne suit pas les liens symboliques mais les écrase.

     -o dir
     --operatingdir=dir

Sélectionne le dossier **dir** comme nouveau dossier courrant.

     -p
     --preserve

Conserve les touches XON \(^Q\) et XOFF \(^S\).

     -q
     --quiet

Ignore silencieusement les problèemes de démarages, comme les erreurs du 
fichier nano.rc

     -r col
     --fill=col

Change le point de wrapping à la colonne **col**.

     -s prog
     --speller=prog

Utilise le programme **prog** comme correcteur orthographique.

     -t
     --tempfile

Sauvegarde à l'arrêt du programme, sans demander à l'utilisateur.

     -u
     --undo

Active l'utilisation du retour en arrière \(expérimental\).

     -v
     --view

Mode visonnage \(lecture seule\).

     -w
     --nowrap

Ne wrappe pas les ligne longues.

     -x
     --nohelp

N'affiche pas les deux lignes d'aides.

     -z
     --suspend

Autorise la supsension de l'édition

     -$
     --softwrap

Active le wrappage léger des lignes.

     -a  -b
     -e -f
     -g -j

Ignorés, uniquement pour la compatibilité avec **Pico**

## Compatibilité ##

Disponible depuis la version **0.7**. Incompatible avec **cmd.exe**, qui ne 
possède plus de tel éditeur depuis l'abandon de MS-DOS.

## A voir aussi ##

[Commande ICONV](iconv), [IDE batman](batman) 

