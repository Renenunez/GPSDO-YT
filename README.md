# GPSDO-YT
https://www.instructables.com/GPSDO-YT-10-Mhz-Lcd-2x16-With-LED/

Gpsdo Yannick.atsln  ---> Source file can be open with AtmelStudio 7

The nop loop is very important. It assure to take only one cycle to enter and come out of an interruption.
If you bypass the loop it will works. But the count will be +- .002 instead .001

Skip to content
Search or jump to…

Pull requests
Issues
Marketplace
Explore
 
@YannickTurcotte 
Learn Git and GitHub without any code!
Using the Hello World guide, you’ll start a branch, write comments, and open a pull request.


YannickTurcotte
/
GPSDO-YT
Private
1
00
Code
Issues
Pull requests
Actions
Projects
Security
Insights
Settings
GPSDO-YT/Readme.txt
@YannickTurcotte
YannickTurcotte Update Readme.txt
Latest commit 3db4372 22 minutes ago
 History
 1 contributor
37 lines (36 sloc)  3.21 KB
  
;V 1.5

;1.5 Add delay to always start count at the same place. Correct some display error. wrong frequency was display of +- .006 some time or .002. 
;return in phase 4 after reset.

;v1.51 ajouter unreachable frequency

;v1.52q remove moyenne sub routine. faisait un bug que pwm changeais a une valeur incorrecte. Jamais trouvé pourquoi, fonctionne en simulateur mais en vrai bug intermittent,
;de plus celle ci n'était pas nécessaire car apres analyse, je ne peux faire une moyenne car le pwm change trop d'un bord ou l'autre selon la température. Le fait de le ramener
;au millieu apres 20 x 1000s n'aidait en rien.

;1.52q et c ajouter jumper pour classis et quick ensemble (pb5 a 0) et un autre pour baud rate a 4800 pour jorge qui utilise un vieux gps module

;1.53 -ajouter ligne code to 512 bytes memory. (clear waitflag wasn't cleared) Mais ce n'était pas mon bug.
;dans wait, quand j'appuie sur le bouton,j'affiche le temps et la config a la place de bypasser le wait. Apres analyse, ce n'était pas le wait_flag mais plutot du rebond sur le ;bouton int1. 2 interrupt back to back ne fait aller directement afficher l'heure.
;j'ai donc ajouter du code pour améliorer cela
;-Un pulse manque, on passe en self running, un pulse revien, sa affiche la phase et attendait le prochain pulse qui venait jamais pour cause de signal faible. On reste sur un ;afficheur ph3, 60s
;J'ai donc activé le watchdog plus de tot. Au début du retour en mode interrupt.
;-Ajouter LedInit

;1.54  ajouter counting led qui flash. Si jamais le uC plante on s'en appercoit. La led est on ou off

;1.55 enlever les phase pour les remplacer par le pwm. Nettoyer le code.

;1.56 add serial tx data to monitor with putty or other on uart.
