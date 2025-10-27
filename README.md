# Instructions d'installation du plugin

## Les Pré-requis :

7zip : https://www.7-zip.org/download.html

Node : https://nodejs.org/fr/download

Python : https://www.python.org/downloads/

ETS2 Telemetry : https://github.com/Funbit/ets2-telemetry-server

Notepad++ : https://notepad-plus-plus.org/downloads/

### Autres outils :

DCSB : https://github.com/Kalejin/DCSB

JoyToKey : https://joytokey.net/en/download

Voicemeeter (Pour ceux qui n'ont pas d'écran avec sortie casque / Laptop sans Entrée Ligne)

Voicemeeter : https://vb-audio.com/Voicemeeter/banana.htm

VB Cable : https://vb-audio.com/Cable/index.htm


-----------------------------------------

#### Installation des pré-requis:

Installez Python 3.13

Installez Node

Dezipper ETS2 Telemetry (avec 7zip de préférence)

------------------------------------------


**ATTENTION DE BIEN CONFIGURER "proxy.js" et de mettre l'IP locale de VOTRE PC qui tournes avec ETS2**

L'IP locale peut être trouvable via CMD en tapant ipconfig
Bien penser a renseigner l'adresse IPv4 (192.168.x.x)

Si c'est un setup double PC, bien mettre l'IP locale du PC avec ETS2, non celui du pc qui lit le plugin
et bien penser a ouvrir ETS2 Telemetry.exe sur le pc avec ETS2 pour la lecture de la position


------------------------------------------
# Création de l'environement

Ouvrir un CMD sur le dossier en cours, puis copier coller ces lignes (il y aura besoin de plusieurs CMD)


npm init -y

npm install express node-fetch

node proxy.js

npm install ws

node server.js


# Pour lancer le server local : 

python -m http.server 8000



Pensez a ouvrir ETS2 Telemetry.exe et le configurer afin de pouvoir recevoir la position du camion (une fois le jeu lancé, partie lancée)

Pour ouvrir ETS2 Télémetry : une fois dézippé, Rentrez dans le dossier ets2-telemetry-server-master, ensuite "Server" puis vous avez Ets2Telemetry.exe

Le test de la page, si tout fonctionne bien :
http://localhost:8000/RetroTuner_EU.html

Les prochaines fois, il y aura juste besoin d'aller sur le fichier Start.bat pour tout lancer d'un coup


---------------------------------------------
# RetroTuner

La plage de fréquence: 87.5 à 108.0

Possibilité de naviguer manuellement sur chaque fréquences, ou utiliser la fonction de scan automatique qui accrochera sur la station la plus proche de la fréquence

L'autoradio dispose d'une fonction autostore, permettant de stocker les 5 stations les mieux reçus

La radio ne dispose pas de la fonction 'RDS', affichage de la station via l'afficheur, mais il a la fonction de fréquence alternative permetant a l'utilisateur de conduire sereinement, sans avoir besoin de toucher à l'autoradio, lorsque le signal devient faible, si la même station est disponible, il bascule automatiquement dessus, il y aura une petite coupure de son afin de lire le flux

La fonction AF est affiché sur l'afficheur lorsqu'il est activé, lorsqu'il est désactivé, AF n'est pas affiché

Les émetteurs émettent dans un rayon de 30 à 50km dans la majorité des cas, il se peut que certaines zones soient perturbés par d'autres stations voisines

Le bargraphe : La radio possède un système d'affichage de puissance de signal sous forme de bargraphe, 3 niveaux de réception, 3/3 Très bonne réception, 2/3 Bonne réception, 1/3 Moyenne à Faible réception, 0/3 Faible réception jusqu'à aucun signal

La radio est cliquable, vous pouvez naviguer manuellement dans les fréquences, activer un autostore, naviguer dans les presets, activer la fonction AF, Permuter le scan en mode Local ou DX

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
(Totalement compatible avec le Hori)

-----------------------------------------

Dans le débug en bas de page il y a possibilité de voir le nom de la station, lancer un scan, naviguer dans les fréquences, voir la position actuelle 

-----------------------------------------

## Utilitaire de plan de fréquences

L'utilitaire permet d'attribuer automatiquement des fréquences à la ville souhaitée, dispo pour Grand Utopia et la map de base d'ETS2
Il suffit de renseigner le nom de la ville, suivi du nombre de fréquences à attribuer, selon la couverture d'autres stations dans la zone provenant d'autres villes, il attribuera de nouvelles fréquences si il y en a de disponible pour la zone
par exemple Paris : je veux 3 nouvelles stations : Paris,3, puis une fois cliqué sur le bouton générer en bas de la page, il affichera les fréquences disponible


## Qu'est ce que StereoDist ?

Stereodist c'est une feature avancée de la radio, elle rends l'audio plus réaliste, coupure du stereo quand le signal devient plus faible, effet de distortion lorsque le signal est faible, suivi d'une perte des aigus

Si vous avez un setup double écran (ecran + TV) et que l'un des deux possède une sortie casque, branchez en jack vers l'entrée ligne du PC, utilisez un autre navigateur pour le plugin radio, séparément de stereodist (Edge = plugin radio, Chrome : Stereodist)
dans les parametres audio de windows, cherchez Edge, puis assignez le peripherique de sortie : la TV (ou l'écran), une fois fait, stereodist lira l'entrée ligne (le son de la télé/écran qui lit le plugin)


A chaque redémarrage, windows est un peu chiant, il faut reassigner le peripherique de sortie pour avoir a nouveau l'audio du plugin sur stereodist


L'autre méthode c'est de lancer le plugin, copier le lien du plugin_radio.html, l'ouvrir sur un autre onglet et fermer l'autre, souvent l'audio va ensuite dans le bon device 
(les bugs windows qui rendent fou)


Autrement si pas de double écran avec sortie casque, ni entrée ligne (laptop), ma solution : Voicemeeter Banana avec VB Cable (Edge sur VB Cable)

Stereodist c'est une fonction un peu plus galère a configurer, mais ça rends la chose bien plus réaliste !


-------------------
Si besoin d'ajouter des stations, changer les stations, fréquences, il suffit de faire les modifications sur stations.js, utilisez formcreerradio.html, et copiez collez vers stations.js


----------------------

## Utilitaire de plan de fréquences

L'utilitaire permet d'attribuer automatiquement des fréquences à la ville souhaitée, dispo pour Grand Utopia et la map de base d'ETS2
Il suffit de renseigner le nom de la ville, suivi du nombre de fréquences à attribuer, selon la couverture d'autres stations dans la zone provenant d'autres villes, il attribuera de nouvelles fréquences si il y en a de disponible pour la zone
par exemple Paris : je veux 3 nouvelles stations : Paris,3, puis une fois cliqué sur le bouton générer en bas de la page, il affichera les fréquences disponible

----------------------

## Questions & Réponses

Q: Pourquoi l'Europe ne comporte que quelques stations pour chaque villes ?

R: Comme vous le savez, ETS2 possède un très grand nombre de villes, tout completer (station par station) prendrait beaucoup de temps

____________________
Q: Est ce que je peux ajouter une station/modifier celles existantes | Planter un émetteur dans une ville de son choix

R: Vous êtes libre de modidier/ajouter des stations, implémenter des émetteurs, pour ajouter une station, pensez à aller sur le fichier formcreerradio.html qui aide a ajouter les stations, il ne suffira plus qu'à les coller dans stationseurope.js
_________________________
Q: Je veux ajouter un émetteur mais je ne sais pas comment faire pour trouver la position

R: Activez le mode Développer et Console sur le fichier Config.cfg d'ETS2 se trouvant dans Documents/ETS2 | cherchez uset "g_developer" et mettez le sur "1" , puis uset g_console et mettez le sur "1" , Sauvegardez, puis sur ETS2 appuyez sur la touche 0 (celle avec le @/à) , puis naviguez en camera libre avec le pavé numérique, puis a la position souhaité, faites F11, vous aurez une fenetre de report avec 3 positions affichée, la première équivaut à X, la seconde à Z (ne pas en tenir compte), la dernière à Y, puis vous n'avez plus qu'à les reporter dans le formulaire
______________
Q: J'ai ajouté une station et une fréquence, mais le plugin ne la pas pris en compte, j'ai un bruit blanc sur la station choisie

R: Il est probable que le navigateur ait gardé le cache de la version précédente, dans le navigateur faitez ctrl+F5, puis regardez si elle est maintenant dispo
_______________
Q: J'ai suivi le processus ctrl+F5, mais la station n'est toujours pas présente, que dois je faire

R: Vérifiez que la position a été correctement renseignée, souvent on a tendance a oublier le - ou oublier un chiffre, pour verifier, allez dans mapall.html (via http://localhost:8000/mapall.html), décochez toutes les fréquences depuis le bouton en bas, puis cochez la fréquence, et regardez si vous trouvez bien le rayon d'émission
_________________
Q: Je suis en caméra libre, mais je captes exactement la même chose alors que je suis a 200km du camion, est ce un bug ?

R: En caméra libre, la télémétrie n'est pas pris en compte, il faut faire spawn le camion a cet endroit (ctrl+f9)

________________

Q: J'ai ajouté une station et une fréquence, mais la radio ne s'allume plus depuis cet ajout, pourquoi ?

R: Il est fort probable que vous ayez oublié la virgule à la fin de votre saisie si pas à la fin (par ex: range: 42000 } ) / placé une virgule à la fin de la dernière saisie (range: 42000 },) le formulaire place toujours la virgule à la fin, soyez bien attentif | Autre possiblité : que vous ayez effacé une lettre par inadvertence / effacé le pied du script (le ]; à la toute fin)

______________________

Q: Quand je veux avancer de fréquence en fréquence, je suis bloqué sur une station, comment me débloquer ?

R: La fonction AF (Fréquence Alternative) a été activée, pour ne plus être bloqué sur une station, désactivez la fonction via le bouton au dessus du poste ou via le raccourci défini par DSCB

______________

Q: A quoi sert le bouton de Fréquence Alternative ?

R: Lorsque vous vous déplacez, vous vous déplacez dans le rayon d'émission de l'émetteur 1, lorsque le signal devient faible, si l'émetteur 2 comportant la même station est à portée, il basculera directement sur celle ci, il y aura un petit temps de chargement du flux

____________

Q: J'ai activé la fonction AF, mais après quelques kilomètres je n'ai plus aucun signal de ma station préférée, n'est il pas censé me garder la station ?

R: Dans le cas ou aucun émetteur a proximité n'émet la station sur une fréquence, ou qu'elle est trop faible, AF clignotera pour rechercher la station, mais ne basculera pas, tant que le signal n'est pas suffisant

____________

Q: A quoi sert L'autostore (AST) ?

R: L'autostore vous permets de mémoriser 5 stations les plus fortes selon votre position

______________

Q: Comment utiliser L'autostore (AST) ?

R: Via le bouton du poste (AST), appuyez dessus, il aura mémorisé les stations les plus fortes, vous n'aurez plus qu'à naviguer entre le bouton 1 à 5 pour choisir votre station | Vous pouvez le réaliser également en jeu via le volant/clavier/manette avec la méthode DSCB

___________

Q: A quoi sert le bouton LOC/DX ? Je peux l'activer/désactiver mais je ne sais pas a quoi il sert

R: La fonction Local/DX permet au scan : Mode Local : Accrocher seulement les stations les mieux reçues | Mode DX : Ce mode est par défaut activé, il permet d'accrocher des stations plus faibles, un peu lointaines mais avec suffisament de force

_______________



Q: Lorsque j'ouvres le fichier HTML du plugin, rien ne fonctionne

R: Il ne faut pas ouvrir le plugin via le fichier html directement, il faut toujours passer via le server local localhost, via le fichier .bat qui ouvre ce server directement

_______________

Q: Est ce que le plugin est compatible avec ATS ?

R: Oui il l'est car la télémétrie est la même que celle de ETS, pour le moment il n'y a pas de stations configurés pour les villes d'ATS, mais il est tout à fait possible d'implémenter les stations ! il suffit d'aller dans stationsATS.js

_______________

Q: Puis je partager mon fichier de stations à la communautée ? | Embellir le fichier existant et le proposer en tant que nouvelle version ? | Proposer un fichier pour ATS ?

R: Il est tout à fait possible de partager son propre fichier de stations à la communautée / Une mise à jour du fichier existant avec de nouvelles stations, bien plus garnie/ reorganiser les fréquences ? Oui, et je dirais même merci beaucoup d'agrandir la liste des stations | Une réorganisation des fréquences, également !
_______________

Q: A l'heure actuelle, dans quelle map le plugin est le plus compatible

R: Le plugin est bien plus garni en stations dans la map GrandUtopia du au fait qu'il n'y a pas beaucoup de villes, et que la map n'est pas immense

__________

Q: Est-ce que la réception est réaliste ?

R: Oui, le comportement de la réception est simulé de manière réaliste (perte progressive, bruit blanc, bascule de fréquence si AF activé), les portées varient selon les émetteurs

____________________

Q: Si je suis dans un tunnel, est ce que je perds la réception ?

R: Le plugin est basé sur la télémétrie (Position X, Y et la hauteur), pas de l'environement direct d'ETS2, il serait très complexe de coder le plugin via l'environement direct

____________________

Q: Est ce que la radio capte partout ?

R: Non, certaines zones peuvent être mal couvertes, cela renforce l'immersion et l'aspect authentique du plugin

__________

Q: Si je suis tout en haut d'une colline, est ce que je captes mieux que si je suis tout en bas ?

R: Oui, en haut d'une colline il est possible même de capter une station qui tout en bas ne captes pas du tout (no signal)

__________

Q: Est ce que la fonction Stereodist est obligatoire ?

R: Non, Elle est optionnelle mais elle rajoute une vraie dimension audio, par exemple la perte du stereo, l'attenuation des aigus selon la puissance du signal, accompagné d'une accentuation de distortion de l'audio

________________

Q: Pourquoi avoir choisi ce style de radio des années 90 ?

R: Les autoradios de l'époque avaient quelque chose que les autoradios modernes n'ont pas, c'est également pour retrouver la sensation de ces anciens autoradios, une réception imparfaite, un vrai scan FM, pas un "Seek" aseptisé sans âme, puis cette sensation d'exploration et de découverte comme pendant la route des vacances, vous tombez sur une station inconnue mais incroyable, loin de cette ère du streaming uniformisé et sans saveur

________________

Q: Le plugin est il dans sa version finale ?

R: Le plugin sera probablement amené a évoluer dans le temps

________________

Q: Pourquoi ne pas avoir créé un executable plutôt qu'un .bat ?

R: J'ai tenté de creer un executable, mais certaines fonctions fondamentales comme la télémétrie ne répondait plus a l'appel, c'est aussi une façon a ce que chaqu'un puisse modifier certaines choses, comme la sensibilité du scan (Loc/DX), le seuil de basculement pour la fonction AF

________________

Q: Il existe déjà un plugin radio créé par Koevenh est ce une nouvelle version ?

R: J'ai été inspiré du plugin LocalRadio de Koevenh, j'ai énormément apprécié ce plugin, ceci dit, LocalRadio ne fonctione pas exactement pareil, il ne mets pas a disposition une bande FM naviguable, LocalRadio, la bande FM est remplacé par une liste définie sur une ville, un peu comme le DAB, mais avec un whitenoise, si la station est hors portée, il n'y aura rien d'autre, concernant la bande FM, si une station est hors de portée, en faisant quelques kilomètres, une autre sera peut être a portée

_____

Q: J'ai le DLC Grece, pourquoi je ne reçois aucune station en grece ?

R: Pour le moment aucun émetteur n'a été implanté dans cette zone, cette zone sera couverte très bientôt !

_____

Q: Je suis sur la map d'ETS, mais je ne reçois rien, pourtant je suis en Allemagne/Benelux/France, est ce normal ?

R: Il est fort probable que le HTML lancé n'est pas celui de la map europe, mais celle pour Grand Utopia

_______


Q: Je suis sur le jeu, mais la position reste sur X:0 Y:0 Z:0, pourquoi ?

R: Bien verifier que ETS2 Télémetry.exe soit bien lancé / Assurez vous que l'IP locale du pc soit identique a celle renseigné dans proxy.js

________

Q: Je veux utiliser l'afficheur sur mon smartphone, mais je n'y ai pas accès

R: Assurez vous d'être sur le même réseau que le PC, même réseau Wifi | Assurez vous d'avoir bien renseigné la bonne adresse IP tout en bas dans serverdisplay.js , puis dans la page Display_Only_OBS , recherchez  " const ws = new WebSocket("ws://192.168. " et completez votre IP locale | puis dans la page du plugin " const ws = new WebSocket('ws://192.168. " puis completez par votre IP Locale


_____________ 


Projet personnel à but non commercial
