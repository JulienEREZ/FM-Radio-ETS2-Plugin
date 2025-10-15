Pré-requis :

7zip : https://www.7-zip.org/download.html

Node : https://nodejs.org/fr/download

Python : https://www.python.org/downloads/

ETS2 Telemetry : https://github.com/Funbit/ets2-telemetry-server

Notepad++ : https://notepad-plus-plus.org/downloads/

Autres outils :

DCSB : https://github.com/Kalejin/DCSB

JoyToKey : https://joytokey.net/en/download

------------------------------------


Installation :

Ouvrir un CMD sur le dossier en cours, puis copier coller ces lignes (il y aura besoin de plusieurs CMD)

npm init -y

npm install express node-fetch

node proxy.js


npm install ws

node server.js

Pour lancer le server local : 

python -m http.server 8000

Pensez a ouvrir ETS2 Telemetry.exe et le configurer afin de pouvoir recevoir la position du camion (une fois le jeu lancé, partie lancée)

**Pensez bien a mettre votre IP locale dans proxy.js** 

Le test de la page, si tout fonctionne bien
http://localhost:8000/radio.html


Les prochaines fois, il y aura juste besoin d'aller sur le fichier Start.bat pour tout lancer d'un coup

---------------------------------------------
**Le Plugin**

Plage de fréquence: 87.5 à 108.0

Possibilité de naviguer manuellement sur chaque fréquences, ou utiliser la fonction de scan automatique qui accrochera sur la station la plus proche de la fréquence

L'autoradio dispose d'une fonction autostore, permettant de stocker les 5 stations les mieux reçus

La radio ne dispose pas de la fonction 'RDS', affichage de la station via l'afficheur, mais il a la fonction de fréquence alternative qui (activé par défaut) permetant a l'utilisateur de conduire sereinement, sans avoir besoin de toucher à l'autoradio, lorsque le signal devient faible, si la même station est disponible, il bascule automatiquement dessus, il y aura une petite coupure de son afin de lire le flux

La fonction AF est affiché sur l'afficheur lorsqu'il est activé, lorsqu'il est désactivé, AF n'est pas affiché

Les émetteurs émettent dans un rayon de 30 à 50km dans la majorité des cas, il se peut que certaines zones soient perturbés par d'autres stations voisines

Le bargraphe : La radio possède un système d'affichage de puissance de signal sous forme de bargraphe, 3 niveaux de réception, 3/3 Très bonne réception, 2/3 Bonne réception, 1/3 Moyenne à Faible réception, 0/3 Faible réception jusqu'à aucun signal

La radio est cliquable, vous pouvez naviguer manuellement dans les fréquences, activer un autostore, naviguer dans les presets
Seul la fonction AF n'est pas nativement implémentée dans l'autoradio à l'origine, d'oû le fait que le bouton soit en dehors de l'autoradio

Les raccourcis : La radio possède des raccourcis directement via le navigateur, vous pouvez naviguer manuellement dans les fréquences avec la touche A pour la fréquence précédente , < pour la fréquence suivante

lorsque AF est activé, il est possible de changer de fréquence de la même station si une fréquence est perturbée
la touche Q pour lancer l'autoscan, l'autoscan balaye la bande fm, puis s'arrête dès qu'une station est recue, il est possible de stopper l'autoscan en appuyant a nouveau sur la touche Q

Raccourcis avancés pour la conduite sur ETS2
Il n'est pas possible de focus la page HTML en même temps que le jeu, mais il est possible de contourner la chose !

Installez JoyToKey et DCSB (dispo dans le dossier du plugin)

DCSB : Une fois installé, creez le compteur, en liant preset.txt, puis pareil en liant Command.txt et AF.txt
(C'est un death counter à la base, mais il est utilisable en étant focus sur ETS2)
Assignez des touches (suppr inser par exemple, des boutons qui servent pas pour ETS2), sans oublier une touche aussi pour changer le compteur (passer de Command à Presets ou AF)

Command.txt = Recherche de fréquence manuelle, et Autoscan
Preset.txt = Activation de l'autostore et navigation des presets 1 à 5 de l'autostore
AF.txt = Activation/Desactivation de la fonction de fréquence alternative

Si vous avez une manette, une boite à boutons, un volant, il suffira d'assigner des touches (Suppr Inser, Fin par exemple) vers les touches souhaités (tant qu'elles n'affectent pas une fonction dans le jeu)


-----------------------------------------

Dans le débug en bas de page il y a possibilité de voir le nom de la station, lancer un scan, naviguer dans les fréquences, voir la position actuelle 

-----------------------------------------


Qu'est ce que Stereodist.html ?

Stereodist c'est une feature avancée de la radio, elle rends l'audio plus réaliste, coupure du stereo quand le signal devient plus faible, effet de distortion lorsque le signal est faible, suivi d'une perte des aigus

Si vous avez un setup double écran (ecran + TV) et que celle ci possède des haut parleurs avec une sortie casque, branchez en jack vers l'entrée ligne du PC, utilisez un autre navigateur pour le plugin radio, séparément de stereodist (Edge = plugin radio, Chrome : Stereodist)
dans les parametres audio de windows, cherchez Edge, puis assignez le peripherique de sortie : la TV, une fois fait, stereodist lira l'entrée ligne (le son de la télé qui lit le plugin)
A chaque redémarrage windows est un peu chiant, il faut reassigner le peripherique de sortie pour avoir a nouveau l'audio du plugin sur stereodist

Autrement si pas de double écran avec sortie casque, ni entrée ligne (laptop), ma solution : Voicemeeter Banana avec VB Cable


Stereodist c'est une fonction un peu plus galère a configurer, mais ça rends la chose bien plus réaliste !!


-------------------
Si besoin d'ajouter des stations, changer les stations, fréquences, il suffit de faire les modifications sur stations.js, utilisez formcreerradio.html, et copiez collez vers stations.js


Le plugin est pour le moment en phase de test, il sera probablement amené a évoluer dans le temps
