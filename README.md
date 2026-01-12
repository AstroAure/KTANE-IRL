# KTANE-IRL

Ce projet est en cours de réalisation. Ce fichier [README](README.md) sert de lieu de brain-storming et de définition du projet.

## Objectif

Réalisation d'une version IRL du jeu ["Keep Talking And Nobody Explodes"](https://store.steampowered.com/app/341800/Keep_Talking_and_Nobody_Explodes/)

Le but est de fabriquer une malette/bombe comme dans le jeu, avec des modules interchangeables afin de jouer sur des niveaux plus ou moins durs. Idéalement, tous les modules du jeu vidéo seront reproduits, et des modules additionnels pourraient être imaginés.

## Cahier des charges

* La bombe doit avoir 12 emplacements pour des modules, dont un toujours occupé par l'horloge et compteur d'erreurs.
* L'interface (mécanique et électronique) entre la bombe et les modules doit être standard pour permettre au jeu d'être modulaire
  * Les modules doivent faire environ 10x10cm de côté.
  * Les modules doivent être facilement interchangeables (fixation avec des aimants ? contact électrique ou prise (USB/dupont) ?).
  * La bombe doit fournir une alimentation électrique aux modules (5V ?).
  * La bombe doit s'occuper de la gestion globale du jeu: chronomètre, nombre d'erreur, explosion...
  * Les modules doivent communiquer avec la bombe: réussite, échec...
  * La bombe doit communiquer avec les modules: début, reset, temps, indicateurs, numéro de série, batteries, ports...
  * L'interface électronique entre la bombe et les modules doit utiliser l'I2C, l'UART, la communication Série ? A DEFINIR
* Chaque module doit être autonome dans sa gestion (avoir son propre micro-contrôleur).
* Les modules doivent avoir un format standard et doivent être reprogrammables facilement (par exemple, micro-contrôleur avec port USB-C accessible).
* Les modules doivent avoir un LED rouge/verte pour indiquer une erreur ou la réussite. C'est la bombe qui peut s'occuper du signal sonore en cas d'erreur (pour éviter d'avoir besoin d'un buzzer par module).
* Les modules doivent être les plus fidèles possibles. On limitera notamment le nombre d'écrans tactiles pour ne pas avoir l'impression de juste jouer sur une tablette.
* A COMPLETER

## Différents modules

Les noms et descriptions des modules viennent du [manuel de désamorcage](https://www.bombmanual.com/fr/print/KeepTalkingAndNobodyExplodes-BombDefusalManual-v1-fr.pdf). 

#### Fils
* 3-6 fils de couleur à couper (ou débrancher, mais c'est marrant de couper physiquement les fils)
* Pour indiquer la couleur de chaque fil au module (nécessaire pour les régles de réussite), on peut imaginer avoir 5 connecteurs d'un côté, chacun correspondant à une couleur. Donc pour indiquer qu'un fil est rouge, il serait brancher dans le connecteur rouge. Chaque fil aurait donc 5 connecteurs, pour un total de 30 connecteurs disponibles (5x6 fils).

#### Bouton
* Nécessite que la bombe communique au module le temps restant (pour les cas avec la bande colorée)
* Solution *cheap*: bouton avec LED RGB pour indiquer la couleur du bouton et un écran LCD pour indiquer le message sur le bouton + LED RGB pour la bande colorée
* Solution plus complexe mais plus jolie: un vrai bouton d'arrêt d'urgence (comment changer la couleur et le texte ?)

#### Clavier
* Ecran pour afficher les 4 symboles + 4 boutons (ou écran tactile)

#### Simon
* Boutons colorés lumineux (comme un vrai Simon) + buzzer pour le son

#### Jeux de mots
* Ecran tactile
* Autre option plus mécanique ? Ecrans LCD + boutons ? Difficile de gérer les mots qui changent

#### Memory
* Ecran tactile
* Autre option plus mécanique ? Ecrans LCD + boutons ? Difficile de gérer les numéros qui changent de place

#### Code Morse
* LED clignotante pour le morse
* Slider pour entrer la fréquence
* Afficheur (à aiguille ?) pour afficher la fréquence entrée
* Bouton pour valider

#### Fils compliqués
* Idem "Fils" pour gérer la couleur des fils, avec seulement 4 connecteurs (ou 2 en haut (blanc/bleu) et 2 en bas (blanc/rouge))
* LED pour les lumières
* LED avec masque étoile pour les étoiles

#### Séquences de fils
* ALED, aucune idée de comment faire ça sans écran tactile nul

#### Labyrinthe
* Matrice de LED colorées 6x6 pour le labyrinthe
* 4 boutons pour les directions

#### Mot de passe
* Ecran LCD (ou afficheur 7+ segments pour lettres) + boutons pour défiler et soumettre la réponse

#### Evacuation du gaz
* Afficage 7 segments pour le temps
* Ecran LCD + boutons Oui/Non

#### Condensateur
* Afficage 7 segments pour le temps
* Plusieurs LEDs pour la jauge ou une seule LED de plus en plus brillante
* Buzzer pour le son
* Bouton pour décharger le condensateur

#### Molette
* Afficage 7 segments pour le temps
* Potentiomètre pour la molette
* 12 LEDs
* 4 LEDs autour de la molette pour indiquer le haut

#### Indicateurs
* Contrôlés par la bombe
* Certains indicateurs utiles toujours présents sur les bords de la bombe (FRK, CAR...) avec une LED qui peut ou non être allumée

#### Numéro de série
* Contrôlé par la bombe
* Ecran ePaper sur un côté de la bombe

#### Batteries
* Contrôlées par la bombe
* Vraies piles installées ou non sur les côtés de la bombe (AA, AAA, C ?)

#### Ports
* Contrôlés par la bombe
* ALED, aucune idée pour les implémenter
* Certains ports installés, et activés en y branchant un câble ou non ?
