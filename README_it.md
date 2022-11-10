# M.A.M.E. SDL Plus
Un veloce e ottimizzato emulatore M.A.M.E. multipiattaforma con un __effetto CRT reale__!

[![paypal](https://www.paypalobjects.com/it_IT/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=LDCDAQUTH5A9Y)

![RealCRT](/images/ffight_real-crt.png)

### Indice dei contenuti:

* #### Panoramica:
  * [NASCITA DEL PROGETTO](README_it.md#nascita-del-progetto)
  * [VERSIONE REAL CRT](README_it.md#versione-real-crt)
  * [VIDEO DIMOSTRATIVI](README_it.md#video-dimostrativi)

* #### Funzionalità e vantaggi:
  * [SUPPORTO TRACKBALL](README_it.md#supporto-trackball)
  * [SUPPORTO SPINNER](README_it.md#supporto-spinner)
  * [ROMSET AGGIUNTI / MODIFICATI](README_it.md#romset-aggiunti--modificati)
  * [ADAPTIVE DYNAMIC FRAMESKIPPING](README_it.md#adaptive-dynamic-frameskipping)
  * [FRAMEBUFFER PERSONALIZZABILE](README_it.md#framebuffer-personalizzabile)
  * [ROTAZIONE FRAMEBUFFER](README_it.md#rotazione-framebuffer)
  * [HD ARTWORKS](README_it.md#hd-artworks)
  * [SIMPLE SCANLINES](README_it.md#simple-scanlines)
  * [CRT PIXEL EFFECTS](README_it.md#crt-pixel-effects)
  * [VIDEO INTERPOLATION - CRT BLUR](README_it.md#video-interpolation---crt-blur)
  * [VERTICAL REFRESH SYNCHRONIZATION](README_it.md#vertical-refresh-synchronization)
  * [SELEZIONE DISPOSITIVO AUDIO](README_it.md#selezione-dispositivo-audio)
  * [SALVATAGGIO HIGH SCORES](README_it.md#salvataggio-high-scores)
  * [FILE DI CONFIGURAZIONE](README_it.md#file-di-configurazione)
  * [CONFIGURAZIONE PER SINGOLO ROMSET](README_it.md#configurazione-per-singolo-romset)

* #### Romset:
  * [VERSIONE ROMSET DA UTILIZZARE](README_it.md#versione-romset-da-utilizzare)

* #### Configurazione controlli:
  * [TASTIERA](README_it.md#tastiera)
  * [JOYPAD](README_it.md#joypad)
  * [TRACKBALL](README_it.md#trackball)
  * [SPINNER](README_it.md#spinner)
  * [MOUSE](README_it.md#mouse)

* #### Sistemi Operativi supportati:
  * [VERSIONE RASPBERRY PI OS](README_it.md#versione-raspberry-pi-os)
  * [VERSIONE UBUNTU E DERIVATI](README_it.md#versione-ubuntu-e-derivati)
  * [VERSIONE WINDOWS](README_it.md#versione-windows)
  * [VERSIONE OSX/MACOS](README_it.md#versione-osxmacos)

* #### Come integrarlo in RetroPie:
  * [INTEGRAZIONE IN RETROPIE SU RASPBERRY PI](README_it.md#integrazione-in-retropie-su-raspberry-pi)
  * [INTEGRAZIONE IN RETROPIE SU SISTEMI UBUNTU E DERIVATI](README_it.md#integrazione-in-retropie-su-sistemi-ubuntu-e-derivati)

* #### Creare un sistema con Debian LXDE (x86-64):
  * [INSTALLAZIONE DEBIAN LXDE + EMULATIONSTATION + MAME SDL PLUS](README_it.md#installazione-debian-lxde--emulationstation--mame-sdl-plus)

* #### Supporto:
  * [AIUTO / RICHIESTA FUNZIONALITA'](README_it.md#aiuto--richiesta-funzionalita)


### NASCITA DEL PROGETTO
Lo scopo da cui tutto è partito era __poter utilizzare degnamente il M.A.M.E. su Raspberry Pi v1 con l'aggiunta del supporto agli artworks__.

Il codice di partenza è quello della versione 0.61 del M.A.M.E.: qualcuno si chiederà, __perché 0.61__? Inizialmente l'ho scelta perché era la prima versione con il supporto nativo ad artworks esterni ma poi mi sono reso conto che non c'era la possibilità di utilizzarli in alta definizione. A quel punto però una parte del lavoro era già stata fatta, motivo per cui successivamente ho scritto da zero il codice per supportarli. Inoltre la 0.61 è una versione intermedia e matura tra la 0.37b5 (usata in passato da altri porting) e la _famosissima 0.78_, quindi sono andato avanti su questa strada

> Il porting non è __volutamente__ appesantito dall'ulteriore layer delle versioni Libretro (quindi niente __lr-__ davanti al nome) e della versione 0.61 mantiene soltanto il core di base. Se non credete che i core Libretro siano pesanti, provate a eseguire lr-mame2003 su un Raspberry Pi v1 ;-)

__Il codice è altamente ottimizzato__, ho usato lookup table e tutta una serie di logiche per ridurre il carico della CPU, __e funziona su diversi sistemi__! Per raggiungere l'obiettivo del multipiattaforma il layer verso il sistema operativo utilizza la libreria SDL in modo che il codice possa esser compilato per qualsiasi sistema che la supporti, ovvero Windows, Linux, macOS ecc. Inoltre rispetto alla versione 0.61, il cui core è la base di partenza, sono stati aggiunti ulteriori giochi, ad oggi __M.A.M.E. SDL Plus è l'unico porting basato su una versione inferiore alla 0.126 che presenta__ __World Rally (set 1)__ (nome romset __wrally__) perfettamente __funzionante__, (e all'occorrenza ne verranno aggiunti altri) e questo è uno dei motivi, oltre alle nuove funzionalità rispetto alla versione di partenza, per cui il progetto si chiama M.A.M.E. __SDL__ _Plus_ :D

Tra le varie modifiche, che trovate illustrate negli argomenti presenti, c'è la __possibilità__, come accennato all'inizio, __di utilizzare artworks in alta risoluzione__ (formato .lyt) oltre a __poter giocare con 4 trackballs e 4 spinners contemporaneamente__!

Il porting regge senza problemi 60 frames al secondo __reali__ sui Raspberry Pi, a parte nel primo modello. Per RPi v1 arriva però in aiuto il codice che ho scritto dove, implementando un __sistema di frameskipping automatico e dinamico__, vengono saltati _al bisogno_ alcuni frames rendendo l'esecuzione sui primi Raspberry Pi _praticamente full speed_ per molti giochi! I nostri occhi fortunatamente non si accorgono quando questo accade :lol:

Per il Raspberry Pi __v1__ è richiesto (come con tutti i M.A.M.E.) l'overclock, seguite [questa guida](https://www.retropie-italia.it/viewtopic.php?p=7808#p7808) presente sul forum

### VERSIONE REAL CRT
La versione dell'emulatore __Real CRT__ è una versione speciale con un effetto realizzato sfruttando direttamente la programmazione di uno shader a basso livello con OpenGL. Attualmente, è disponibile soltanto per Raspberry Pi v4 e per sistemi con architettura x86. L'eseguibile da utilizzare è quello con il suffisso __real_crt__. In questa modalità ovviamente non è disponibile nessun altro effetto video

> Se riscontrate delle prestazioni limitate con il Raspberry Pi v4 è necessario ricompilare il driver Mesa, e le altre librerie necessarie, da zero. Aggiungerò una guida il prima possibile

### VIDEO DIMOSTRATIVI
Per darvi subito un'idea del lavoro svolto ecco un paio di video dimostrativi!

__PC di sviluppo vs Raspbery Pi v1__

Ecco un video con un confronto di esecuzione tra il portatile sul quale sviluppo e il Raspberry Pi v1:

[PC vs Raspberry Pi v1](https://drive.google.com/file/d/1XLGHF3zitmshKRqBJhUJhVQGYpB2ucCm/view?usp=sharing)

Guardare per credere ;-)

__M.A.M.E. SDL Plus vs lr-mame2003__

In questo video viene mostrata la differenza di prestazioni su __Raspberry Pi v1__ tra lr-mame2003 e il mio emulatore:

[Raspberry Pi v1: lr-mame2003 vs M.A.M.E. SDL Plus](https://drive.google.com/file/d/127u8PJ_vs-OoQVXb9tuyVK3fv-FRlaAd/view?usp=sharing)

Non credo di essere di parte se dico che lr-mame2003 non regge il confronto ;-)

### SUPPORTO TRACKBALL
Le versioni per Raspberry Pi e quella per sistemi Ubuntu-based supportano l'utilizzo di __4 trackballs connesse contemporaneamente__, ovvero il numero massimo di giocatori disponibile nei giochi che utilizzavano tale sistema di controllo.

Le versioni per __Windows e OSX/macOS__ _supportano un solo giocatore_ con questo sistema di controllo e __non è necessario eseguire la [configurazione](README_it.md#trackball)__.

Il M.A.M.E. non distingue tra movimento analogico di una trackball e movimento analogico di uno spinner. Il core del M.A.M.E. si occupa del movimento dei Players, non distingue la richiesta per tipo di periferica, se sono presenti sia trackball che spinner associati al medesimo Player (sempre vero sulle versioni per Windows e OSX/macOS) è possibile usare entrambe le periferiche per controllarlo.

Questo __non comporta nessun problema di gameplay__, è chiaro che dovrete evitare di giocare a __Missile Command II__ con la trackball mentre il nipotino/amico dispettoso armeggia sullo spinner :lol:

Ovviamente per giocare al meglio dovete utilizzare la periferica per cui il gioco è stato progettato. Se non sapete quale sia premete Tab e spostatevi in __Analog Controls__, se trovate la parola __Dial__ il gioco utilizzava uno spinner (o un volante come in __Championship Sprint__), se trovate la parola __Track__ utilizzava una trackball, se il sottomenù __Analog Controls__ non è presente non usava né uno né l'altra. Sempre nel menù __Analog Controls__ è possibile aumentare la sensibilità del dispositivo qualore fosse necessario.

Se aumentando la sensibilità del dispositivo tramite il menù del M.A.M.E. non ottenete l'effetto desiderato potete utilizzare il parametro __analog-boost__ da riga di comando, che di default è disabilitato, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arcadecl -analog-boost`

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __Boost Analog Sensitivity On/Off__ per attivare/disattivare l'aumento di sensibilità con il M.A.M.E. in esecuzione premendo semplicemente un pulsante.

Elenco giochi che utilizzano la trackball:

```
Game: "Shuffleboard" , Romset: shuffle , Year: 1978 , Flags: GAME_NO_SOUND
Game: "4 Player Bowling Alley" , Romset: bowler , Year: 1978 , Flags: GAME_NO_SOUND
Game: "Arcade Classics (prototype)" , Romset: arcadecl , Year: 1992
Game: "Extra Bases" , Romset: ebases , Year: 1980
Game: "Atari Football (revision 2)" , Romset: atarifb , Year: 1978
Game: "Atari Football (4 players)" , Romset: atarifb4 , Year: 1979
Game: "Atari Baseball (set 1)" , Romset: abaseb , Year: 1979
Game: "Atari Soccer" , Romset: soccer , Year: 1980
Game: "Marble Madness (set 1)" , Romset: marble , Year: 1984
Game: "Ataxx (set 1)" , Romset: ataxx , Year: 1990
Game: "Beezer (set 1)" , Romset: beezer , Year: 1982 , Flags: GAME_IMPERFECT_SOUND
Game: "Birdie King 2" , Romset: bking2 , Year: 1983 , Flags: GAME_NOT_WORKING
Game: "Blades of Steel (version T)" , Romset: bladestl , Year: 1987
Game: "Blades of Steel (version E)" , Romset: bladstle , Year: 1987
Game: "Basketball" , Romset: bsktball , Year: 1979
Game: "Cabal (US set 1)" , Romset: cabal , Year: 1988 , Flags: GAME_IMPERFECT_SOUND
Game: "Capcom Bowling (set 1)" , Romset: capbowl , Year: 1988
Game: "Crystal Castles (version 4)" , Romset: ccastles , Year: 1983
Game: "Centipede (revision 3)" , Romset: centiped , Year: 1980
Game: "Centipede (bootleg set 1)" , Romset: centipdb , Year: 1980
Game: "Magic Worm (bootleg)" , Romset: magworm , Year: 1980
Game: "Millipede" , Romset: milliped , Year: 1982
Game: "Cloud 9 (prototype)" , Romset: cloud9 , Year: 1983 , Flags: GAME_NO_COCKTAIL
Game: "Combat School (trackball)" , Romset: combasct , Year: 1987
Game: "Top Secret (Exidy) (version 1.0)" , Romset: topsecex , Year: 1986
Game: "Reactor" , Romset: reactor , Year: 1982
Game: "Gridlee" , Romset: gridlee , Year: 1983 , Flags: GAME_IMPERFECT_SOUND
Game: "World Class Bowling (v1.2)" , Romset: wcbowl , Year: 1995
Game: "Shuffleshot" , Romset: shufshot , Year: 1997
Game: "Danger Zone" , Romset: dangerz , Year: 1986
Game: "Lemmings (US Prototype)" , Romset: lemmings , Year: 1991
Game: "Liberator (set 1)" , Romset: liberatr , Year: 1982 , Flags: GAME_NO_COCKTAIL
Game: "Pound for Pound (World)" , Romset: poundfor , Year: 1990 , Flags: GAME_IMPERFECT_SOUND | GAME_NO_COCKTAIL
Game: "Wacko" , Romset: wacko , Year: 1982
Game: "Discs of Tron (Upright)" , Romset: dotron , Year: 1983
Game: "Tri-Sports" , Romset: trisport , Year: 1989
Game: "Missile Command (set 1)" , Romset: missile , Year: 1980
Game: "Super Missile Attack" , Romset: suprmatk , Year: 1981
Game: "The Irritating Maze / Ultra Denryu Iraira Bou" , Romset: irrmaze , Year: 1997
Game: "Shoot the Bull" , Romset: shootbul , Year: 1985
Game: "Slither (set 1)" , Romset: slither , Year: 1982
Game: "Quantum (rev 2)" , Romset: quantum , Year: 1982
Game: "Rampart (3-player Trackball)" , Romset: rampart , Year: 1990
Game: "Shuuz (version 8.0)" , Romset: shuuz , Year: 1990
Game: "Shuuz (version 7.1)" , Romset: shuuz2 , Year: 1990
Game: "Brick Zone (v5.0)" , Romset: brickzn , Year: 1992 , Flags: GAME_NOT_WORKING
Game: "Major League" , Romset: mjleague , Year: 1985
Game: "SDI - Strategic Defense Initiative" , Romset: sdi , Year: 1987
Game: "Sonic (Japan rev. C)" , Romset: sonic , Year: 1992 , Flags: GAME_NOT_WORKING | GAME_UNEMULATED_PROTECTION
Game: "Rambo III (US)" , Romset: rambo3a , Year: 1989
Game: "Syvalion (Japan)" , Romset: syvalion , Year: 1988
Game: "American Horseshoes (US)" , Romset: horshoes , Year: 1990
Game: "Tehkan World Cup" , Romset: tehkanwc , Year: 1985
Game: "Gridiron Fight" , Romset: gridiron , Year: 1985
Game: "Tee'd Off (Japan)" , Romset: teedoff , Year: 1986 , Flags: GAME_NO_COCKTAIL
```

TRACKBALL:
https://amzn.to/3AiFb9Z

USB CONNECTION CABLE:
https://amzn.to/3qICR8O

### SUPPORTO SPINNER
Le versioni per Raspberry Pi e quella per sistemi Ubuntu-based supportano l'utilizzo di __4 spinners connessi contemporaneamente__.

Le versioni per __Windows e OSX/macOS__ _supportano un solo giocatore_ con questo sistema di controllo e __non è necessario eseguire la [configurazione](README_it.md#spinner)__.

Il M.A.M.E. non distingue tra movimento analogico di una trackball e movimento analogico di uno spinner. Il core del M.A.M.E. si occupa del movimento dei Players, non distingue la richiesta per tipo di periferica, se sono presenti sia trackball che spinner associati al medesimo Player (sempre vero sulle versioni per Windows e OSX/macOS) è possibile usare entrambe le periferiche per controllarlo.

Questo __non comporta nessun problema di gameplay__, è chiaro che dovrete evitare di giocare a __Missile Command II__ con la trackball mentre il nipotino/amico dispettoso armeggia sullo spinner :lol:

Ovviamente per giocare al meglio dovete utilizzare la periferica per cui il gioco è stato progettato. Se non sapete quale sia premete Tab e spostatevi in __Analog Controls__, se trovate la parola __Dial__ il gioco utilizzava uno spinner (o un volante come in __Championship Sprint__), se trovate la parola __Track__ utilizzava una trackball, se il sottomenù __Analog Controls__ non è presente non usava né uno né l'altra. Sempre nel menù __Analog Controls__ è possibile aumentare la sensibilità del dispositivo qualore fosse necessario.

Se aumentando la sensibilità del dispositivo tramite il menù del M.A.M.E. non ottenete l'effetto desiderato potete utilizzare il parametro __analog-boost__ da riga di comando, che di default è disabilitato, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arkanoid -analog-boost`

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __Boost Analog Sensitivity On/Off__ per attivare/disattivare l'aumento di sensibilità con il M.A.M.E. in esecuzione premendo semplicemente un pulsante.

Elenco giochi che utilizzano lo spinner:

```
Game: "Time Soldiers (US Rev 3)" , Romset: timesold , Year: 1987
Game: "Battle Field (Japan)" , Romset: btlfield , Year: 1987
Game: Inc." , Romset: amspdwy , Year: 1987
Game: "Arkanoid (World)" , Romset: arkanoid , Year: 1986
Game: "Arkanoid (Japan)" , Romset: arknoidj , Year: 1986
Game: "Arkanoid (Tayto bootleg , Romset: arkatayt , Year: 1986
Game: "Road Blasters (set 1)" , Romset: roadblst , Year: 1987
Game: "720 Degrees (set 1)" , Romset: 720 , Year: 1986
Game: "Super Sprint" , Romset: ssprint , Year: 1986
Game: "Championship Sprint" , Romset: csprint , Year: 1986
Game: "APB - All Points Bulletin (set 1)" , Romset: apb , Year: 1987
Game: "Danny Sullivan's Indy Heat" , Romset: indyheat , Year: 1991
Game: "Aztarac" , Romset: aztarac , Year: 1983
Game: "Bad Lands" , Romset: badlands , Year: 1989
Game: "Night Stocker" , Romset: nstocker , Year: 1986
Game: "Blasteroids (version 4)" , Romset: blstroid , Year: 1987
Game: "Buggy Challenge" , Romset: buggychl , Year: 1984 , Flags: GAME_IMPERFECT_SOUND | GAME_IMPERFECT_GRAPHICS
Game: "Car Polo" , Romset: carpolo , Year: 1977 , Flags: GAME_NO_SOUND
Game: "Cosmic Chasm (set 1)" , Romset: cchasm , Year: 1983
Game: "Speed Freak" , Romset: speedfrk , Year: 1979 , Flags: GAME_NO_SOUND
Game: "Boxing Bugs" , Romset: boxingb , Year: 1981 , Flags: GAME_IMPERFECT_COLORS | GAME_NO_SOUND
Game: "Forgotten Worlds (US)" , Romset: forgottn , Year: 1988
Game: "Heavy Barrel (US)" , Romset: hbarrel , Year: 1987
Game: "Midnight Resistance (World)" , Romset: midres , Year: 1989
Game: "Gondomania (US)" , Romset: gondo , Year: 1987
Game: "Drag Race" , Romset: dragrace , Year: 1977 , Flags: GAME_NO_SOUND
Game: "Exterminator" , Romset: exterm , Year: 1989
Game: "Super Bug" , Romset: superbug , Year: 1977 , Flags: GAME_IMPERFECT_SOUND
Game: "Fire Truck" , Romset: firetrk , Year: 1978 , Flags: GAME_IMPERFECT_SOUND
Game: "Monte Carlo" , Romset: montecar , Year: 1979 , Flags: GAME_NO_SOUND
Game: "Goindol" , Romset: goindol , Year: 1987 , Flags: GAME_NO_COCKTAIL
Game: "Homo" , Romset: homo , Year: 1987 , Flags: GAME_NO_COCKTAIL
Game: "Mad Planets" , Romset: mplanets , Year: 1983
Game: "Grand Champion" , Romset: grchamp , Year: 1981 , Flags: GAME_IMPERFECT_SOUND
Game: "Top Gunner (bootleg)" , Romset: topgunbl , Year: 1987 , Flags: GAME_IMPERFECT_COLORS | GAME_NO_COCKTAIL
Game: "Mille Miglia 2: Great 1000 Miles Rally" , Romset: gtmr2 , Year: 1995
Game: "Cerberus" , Romset: cerberus , Year: 1985
Game: "Ironman Stewart's Super Off-Road" , Romset: offroad , Year: 1989
Game: "Kick (upright)" , Romset: kick , Year: 1981
Game: "Kick (cocktail)" , Romset: kicka , Year: 1981
Game: "Tron (set 1)" , Romset: tron , Year: 1982
Game: "Kozmik Kroozr" , Romset: kroozr , Year: 1982
Game: "Two Tigers" , Romset: twotiger , Year: 1984
Game: "Two Tigers (dedicated)" , Romset: twotigra , Year: 1984
Game: "Discs of Tron (Upright)" , Romset: dotron , Year: 1983
Game: "Demolition Derby" , Romset: demoderb , Year: 1984
Game: "Crater Raider" , Romset: crater , Year: 1984
Game: "Zwackery" , Romset: zwackery , Year: 1984
Game: "Major Havoc (rev 3)" , Romset: mhavoc , Year: 1983
Game: "Major Havoc (prototype)" , Romset: mhavocp , Year: 1983
Game: "Alpha One (prototype , Romset: alphaone , Year: 1983
Game: "Block Block (World 911106 Joystick)" , Romset: block , Year: 1991
Game: "Quester (Japan)" , Romset: quester , Year: 1987
Game: "Konami GT" , Romset: konamigt , Year: 1985
Game: "Konami RF2 - Red Fighter" , Romset: rf2 , Year: 1985
Game: "Night Driver" , Romset: nitedrvr , Year: 1976 , Flags: GAME_NO_SOUND
Game: "Off the Wall (2/3-player upright)" , Romset: offtwall , Year: 1991
Game: "Omega Race" , Romset: omegrace , Year: 1981 , Flags: GAME_NO_COCKTAIL
Game: "Over Drive" , Romset: overdriv , Year: 1990 , Flags: GAME_IMPERFECT_GRAPHICS
Game: "Pole Position" , Romset: polepos , Year: 1982
Game: "Pole Position II" , Romset: polepos2 , Year: 1983
Game: "Moonwar" , Romset: moonwar , Year: 1981
Game: "Moonwar (older)" , Romset: moonwara , Year: 1981
Game: "Dark Planet" , Romset: darkplnt , Year: 1982
Game: "Zektor (revision B)" , Romset: zektor , Year: 1982
Game: "Tac/Scan" , Romset: tacscan , Year: 1982
Game: "Star Trek" , Romset: startrek , Year: 1982
Game: "Riddle of Pythagoras (Japan)" , Romset: ridleofp , Year: 1986
Game: "TNK III (US?)" , Romset: tnk3 , Year: 1985 , Flags: GAME_NO_COCKTAIL
Game: "TouchDown Fever" , Romset: tdfever , Year: 1987 , Flags: GAME_NO_COCKTAIL
Game: "Fighting Soccer" , Romset: ftsoccer , Year: 1988 , Flags: GAME_NO_COCKTAIL
Game: "SAR - Search And Rescue (World)" , Romset: searchar , Year: 1989
Game: "Ikari III - The Rescue" , Romset: ikari3 , Year: 1989
Game: "Sprint 1" , Romset: sprint1 , Year: 1978 , Flags: GAME_NO_SOUND
Game: "Sprint 2" , Romset: sprint2 , Year: 1976 , Flags: GAME_NO_SOUND
Game: "Subs" , Romset: subs , Year: 1977 , Flags: GAME_NO_SOUND
Game: "Block Gal" , Romset: blockgal , Year: 1987 , Flags: GAME_NOT_WORKING | GAME_NO_COCKTAIL
Game: "Camel Try (US)" , Romset: cameltry , Year: 1989
Game: "Camel Try (Japan)" , Romset: cameltrj , Year: 1989
Game: "Drift Out (Japan)" , Romset: driftout , Year: 1991
Game: "Aqua Jack (World)" , Romset: aquajack , Year: 1990 , Flags: GAME_IMPERFECT_GRAPHICS
Game: "Tempest (rev 3)" , Romset: tempest , Year: 1980
Game: "Plump Pop (Japan)" , Romset: plumppop , Year: 1987
Game: "Arkanoid - Revenge of DOH (World)" , Romset: arknoid2 , Year: 1987
Game: "Arkanoid - Revenge of DOH (US)" , Romset: arknid2u , Year: 1987
Game: "Ghox" , Romset: ghox , Year: 1991 , Flags: GAME_NO_SOUND
Game: "Turbo" , Romset: turbo , Year: 1981 , Flags: GAME_NO_COCKTAIL
Game: "Victory" , Romset: victory , Year: 1982
Game: "World Rally (set 1)" , Romset: wrally , Year: 1993
Game: "Razzmatazz" , Romset: razmataz , Year: 1983 , Flags: GAME_NO_SOUND
Game: "Ixion (prototype)" , Romset: ixion , Year: 1983 , Flags: GAME_NO_SOUND
```

SPINNER:
https://amzn.to/3AiEttl

SPINNER REMAPPING:
https://iwit.me/support/english.html

### ROMSET AGGIUNTI / MODIFICATI
Ad oggi __M.A.M.E. SDL Plus è l'unico porting basato su una versione inferiore alla 0.126 che presenta__ __World Rally (set 1)__ (nome romset __wrally__) perfettamente __funzionante__ :-)

> Per ricreare il set corretto utilizzate [MAME Set Rebuilder](https://www.retropie-italia.it/viewtopic.php?p=3868#p3868) (oppure [Clrmamepro](https://mamedev.emulab.it/clrmamepro/)) con il file __0.61+.dat__ che trovate nell'archivio contenente l'emulatore oppure [estraetelo](https://www.retropie-italia.it/viewtopic.php?p=3867#p3867) direttamente dall'eseguibile di M.A.M.E. SDL Plus

Rispetto alla versione 0.61 sono presenti diverse modifiche:

* alien3   , __Alien 3__ GAME_IMPERFECT_GRAPHICS
* aligator , __Alligator Hunt__ GAME_UNEMULATED_PROTECTION
* aligatun , __Alligator Hunt (unprotected)__
* arabfgt  , __Arabian Fight__ GAME_IMPERFECT_GRAPHICS
* armora   , __Armor Attack__
* armorap  , __Armor Attack (prototype)__
* armorar  , __Armor Attack (Rock-ola)__
* bang     , __Bang!__
* brival   , __Burning Rival (Japan)__ GAME_IMPERFECT_GRAPHICS
* dadandrn , __Kyukyoku Sentai Dadandarn (Japan ver JAA)__ GAME_IMPERFECT_GRAPHICS
* daiskiss , __Daisu-Kiss (Ver JAA)__ GAME_IMPERFECT_GRAPHICS
* darkedge , __Dark Edge__ GAME_NOT_WORKING | GAME_UNEMULATED_PROTECTION
* dbzvrvs  , __Dragon Ball Z VRVS__ GAME_NOT_WORKING | GAME_UNEMULATED_PROTECTION
* dragoonj , __Dragoon Might (Ver JAA)__ GAME_IMPERFECT_GRAPHICS
* fantjour , __Fantastic Journey__ GAME_NOT_WORKING | GAME_UNEMULATED_PROTECTION
* f1en     , __F1 Exhaust Note__ GAME_IMPERFECT_GRAPHICS
* f1lap    , __F1 Super Lap__ GAME_NOT_WORKING
* ga2      , __Golden Axe - The Revenge of Death Adder (US)__ GAME_IMPERFECT_GRAPHICS
* ga2j     , __Golden Axe - The Revenge of Death Adder (Japan)__ GAME_IMPERFECT_GRAPHICS
* gaiapols , __Gaiapolis (Japan ver JAF)__ GAME_IMPERFECT_GRAPHICS
* gokuparo , __Gokujyou Parodius (Ver JAD)__ GAME_IMPERFECT_GRAPHICS
* harddunk , __Hard Dunk (Japan)__ GAME_IMPERFECT_GRAPHICS
* holo     , __Holosseum__
* jleague  , __The J.League 94 (Japan)__ GAME_NOT_WORKING | GAME_UNEMULATED_PROTECTION
* jpark    , __Jurassic Park__ GAME_IMPERFECT_GRAPHICS
* le2      , __Lethal Enforcers II: Gun Fighters (Ver EAA)__ GAME_IMPERFECT_GRAPHICS
* le2u     , __Lethal Enforcers II: Gun Fighters (Ver UAA)__ GAME_IMPERFECT_GRAPHICS
* maniacsp , __Maniac Square (prototype)__
* maniacsq , __Maniac Square (unprotected)__
* megaman2 , __Mega Man 2: The Power Fighters (US 960708)__
* megamn2a , __Mega Man 2: The Power Fighters (Asia 960708)__ GAME_NOT_WORKING
* metamrph , __Metamorphic Force (US ver UAA)__ GAME_IMPERFECT_GRAPHICS
* mtlchmpj , __Martial Champion (Japan ver JAA)__ GAME_IMPERFECT_GRAPHICS
* mystwarr , __Mystic Warriors (World ver EAA)__ GAME_IMPERFECT_GRAPHICS
* mystwaru , __Mystic Warriors (US ver UAA)__ GAME_IMPERFECT_GRAPHICS
* opengolf , __Konami's Open Golf Championship (version EAD)__ GAME_IMPERFECT_GRAPHICS
* orunners , __Outrunners (US)__ GAME_IMPERFECT_GRAPHICS
* puzldama , __Taisen Puzzle-dama (Ver JAA)__ GAME_IMPERFECT_GRAPHICS
* racinfrc , __Racin' Force (version UAB)__ GAME_NOT_WORKING
* radm     , __Rad Mobile__ GAME_IMPERFECT_GRAPHICS
* radr     , __Rad Rally__ GAME_IMPERFECT_GRAPHICS
* rungun2  , __Run and Gun 2 (Ver UAA)__ GAME_NOT_WORKING
* salmndr2 , __Salamander 2 (JAA)__ GAME_IMPERFECT_GRAPHICS
* sexyparo , __Sexy Parodius (Ver JAA)__ GAME_IMPERFECT_GRAPHICS
* snowbalt , __Snow Board Championship (set 2)__ GAME_UNEMULATED_PROTECTION
* snowboar , __Snow Board Championship (set 1)__ GAME_UNEMULATED_PROTECTION
* soccerss , __Soccer Superstars (Ver JAA)__ GAME_NOT_WORKING
* sonic    , __Sonic (Japan rev. C)__ GAME_NOT_WORKING | GAME_UNEMULATED_PROTECTION
* sonicp   , __Sonic (Japan prototype)__ GAME_IMPERFECT_GRAPHICS
* spidey   , __Spiderman (US)__ GAME_IMPERFECT_GRAPHICS
* spideyj  , __Spiderman (Japan)__ GAME_IMPERFECT_GRAPHICS
* sundance , __Sundance__
* svf      , __Super Visual Football__ GAME_IMPERFECT_GRAPHICS
* svs      , __Super Visual Soccer (US?)__ GAME_IMPERFECT_GRAPHICS
* tbyahhoo , __Twin Bee Yahhoo! (Ver JAA)__ GAME_IMPERFECT_GRAPHICS
* titlef   , __Title Fight__ GAME_NOT_WORKING
* tkmmpzdm , __Tokimeki Memorial Taisen Puzzle-dama (version JAB)__ GAME_IMPERFECT_GRAPHICS
* tokkae   , __Tokkae Puzzle-dama (Ver JAA)__ GAME_IMPERFECT_GRAPHICS
* touchgo  , __Touch & Go__ GAME_UNEMULATED_PROTECTION
* viostorm , __Violent Storm (Europe ver EAB)__ GAME_IMPERFECT_GRAPHICS
* viostrma , __Violent Storm (Asia ver AAC)__ GAME_IMPERFECT_GRAPHICS
* viostrmj , __Violent Storm (Japan ver JAC)__ GAME_IMPERFECT_GRAPHICS
* viostrmu , __Violent Storm (US ver UAB)__ GAME_IMPERFECT_GRAPHICS
* vsnetscr , __Versus Net Soccer (Ver UAB)__ GAME_NOT_WORKING
* winspike , __Winning Spike (Ver JAA)__ GAME_NOT_WORKING | GAME_UNEMULATED_PROTECTION
* wrally   , __World Rally (set 1)__
* wrally2  , __World Rally 2: Twin Racing__ GAME_UNEMULATED_PROTECTION

> Alcuni giochi sopra riportati sono già presenti nella versione 0.61. Se vengono indicati in questa lista è perché banalmente sono __passati da non funzionanti a funzionanti__ oppure perché il loro codice è diverso rispetto alla versione 0.61

### ADAPTIVE DYNAMIC FRAMESKIPPING
Ho cambiato totalmente la logica di frameskipping presente nel M.A.M.E. migliorando notevolmente le prestazioni sui Raspberry Pi v1 e v0. Per capire come è andata l'esecuzione quando l'emulatore viene chiuso vedrete nel log, tra le altre, queste informazioni:

```
End game summary:
Main loop frequency: 60.000802 Hz
Nominal FPS: 60.000000
Real FPS: 60.000802

Total play time: 3192.074000 seconds
```

__Real FPS__ si riferisce ai frames al secondo mostrati a video, se il valore è identico a __Nominal FPS__ le prestazioni saranno in tutto e per tutto uguali a quelle del cabinato originale. Però attenzione, la magia è questa: __Main loop frequency__ si riferisce ai cicli al secondo del loop principale del gioco, ovvero input, sound, video ecc. Se questo valore è prossimo o identico al valore __Nominal FPS__ le prestazioni _percepite_ saranno identiche a quelle del cabinato originale _anche se_ __Real FPS__ non coincide con __Nominal FPS__.

Normalmente quando __Main loop frequency__ e __Real FPS__ coincidono significa che nessun frame è stato saltato durante l'esecuzione: nel caso però in cui il vertical sync sia attivo potrebbero risultare diversi per motivi di sincronia

> La sincronizzazione audio/video, nonché il mantenimento dei frames al secondo nominali, sfrutta una logica basata sull'hardware audio. Se avete problemi di audio, una configurazione errata, audio non funzionante ecc., i FPS potrebbero non essere rispettati (ad esempio potreste incappare nel superamento del framerate nominale con i giochi che risulteranno accelerati)

### FRAMEBUFFER PERSONALIZZABILE
E' possibile impostare in modo arbitrario la dimensione del framebuffer video, ovvero la dimensione dell'area in cui verrà mostrato il gioco, quando l'emulatore è in esecuzione _in modalità fullscreen_. Basterà lanciare l'emulatore con i parametri __framebuffer-width__ e __framebuffer-height__, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -framebuffer-width 1280 -framebuffer-height 996`

Il codice è intelligente quindi le dimensioni finali verranno ricalcolate all'avvio del gioco in modo che l'__aspect ratio__ del cabinato originale venga __mantenuto__.

Questo può essere __particolarmente utile nel caso in cui avete uno schermo molto grande e volete ridurre la dimensione del gioco__, oppure avete costruito un cabinato arcade ma l'apertura nel legno copre leggermente i bordi dello schermo: in questo secondo caso potete utilizzare questa funzionalità e successivamente centrare il framebuffer rispetto all'apertura del cabinato con i comandi posti sul vostro monitor.

Oltre a ciò è possibile ruotare il framebuffer come spiegato [qui](README_it.md#rotazione-framebuffer)

### ROTAZIONE FRAMEBUFFER
E' possibile ruotare il framebuffer video quando si utilizza la __modalità fullscreen__. Basterà lanciare l'emulatore con l'opzione __rotate-clockwise__ oppure __rotate-counterclockwise__, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus puckman -rotate-counterclockwise`

Come per il [framebuffer personalizzabile](README_it.md#framebuffer-personalizzabile), il codice è intelligente quindi le dimensioni finali verranno ricalcolate in modo che l'__aspect ratio__ del cabinato originale (ed eventualmente dell'artwork) venga __mantenuto__ sfruttando il maggior spazio possibile

### HD ARTWORKS
Gli artworks sono quelle grafiche che circondavano il monitor dei cabinati

> __Retrostoria__: L'origine degli artworks è molto varia.
Il supporto inizialmente era solo hardcoded nel driver del gioco, questo fino alla versione 0.60: in parole povere non era possibile aggiungere un, detto genericamente, overlay esterno (motivo per cui spesso leggo di persone che chiedono come mai in M.A.M.E. 0.37b5 gli artworks _non funzionano_ seppur presenti nella cartella artwork).
La versione 0.61 è stata la prima versione che permetteva l'utilizzo degli artworks in formato .art, artworks che però potevano essere solo in bassa risoluzione. Dalla versione 0.107 invece gli artworks sono supportati (anche in alta risoluzione) in formato .lay.
Il codice sorgente è stato modificato quindi __con M.A.M.E. SDL Plus sono utilizzabili gli artworks in alta risoluzione__ nel formato .lyt. Vi basterà inserire l'immagine in formato .png nella cartella artwork con lo stesso nome del romset (per Final Fight quindi sarà ffight.png) e un file di testo, con estensione .lyt e sempre con il nome del romset (per Final Fight quindi sarà ffight.lyt).

Ad esempio per il romset __sf2ce__ si ha il seguente contenuto del file __sf2ce.lyt__:

```
Width="4000" Height="3743"
GameAreaWidth="2920" GameAreaHeight="2190"
GameAreaX="540" GameAreaY="822"
ArtworkType="merged"
```

__Width__ e __Height__ sono banalmente larghezza e altezza in pixel dell'immagine .png, niente di misterioso.

__GameAreaWidth__ e __GameAreaHeight__ rappresentano larghezza e altezza dell'area dove si vuole che venga mostrato il gioco, nel caso di __sf2ce__ rappresentano il "buco" presente nell'immagine, espresse in pixel rispetto all'immagine.

__GameAreaX__ e __GameAreaY__ sono la coordinata X e la coordinata Y, espresse in pixel, dove il gioco verrà posizionato (l'origine è in alto a sinistra) e in questo caso rappresentano l'angolo in alto a sinistra del "buco" nell'immagine.

__ArtworkType__ accetta le opzioni _ontop_ e _merged_. Il valore di default è __merged__ quindi se il parametro è assente il comportamento sarà di tipo __merged__. Il significato è presto spiegato:

* __merged__: ad esempio nel romset __warrior__ l'artwork linkato più sotto altro non è che lo sfondo del gioco, quindi il risultato finale mostrato a video sarà una fusione di immagini, il frame del gioco, l'artwork ed eventuali effetti video attivi
* __ontop__: a differenza della modalità _merged_ l'artwork viene disegnato sopra al frame del gioco. In questo modo se l'artwork si sovrappone all'area del gioco l'effetto finale sarà, a mio avviso, più gradevole a discapito di non vedere una parte dell'area di gioco

Per farvi capire ancora meglio, qui potete osservare rispettivamente la differenza tra __merged__ e __ontop__ in __Bubble Bobble__:

![bublbobl-merged](/images/bublbobl_merged.png)
![bublbobl-ontop](/images/bublbobl_ontop.png)

Alla fine è una questione di gusti, chiaramente se nel romset __warrior__ utilizzate l'opzione __ontop__, e l'artwork stesso non prevede trasparenze (come nel caso di quello allegato più in basso), non vedrete il gioco ma soltanto lo sfondo :lol:

__Warrior__ configurato correttamente:

![warrior](/images/warrior.png)

Il codice è intelligente quindi successivamente le dimensioni verranno ricalcolate in modo che l'aspect ratio del cabinato originale venga mantenuto, quindi se __GameAreaWidth__ e __GameAreaHeight__ non sono ad esempio 4:3 (come ad esempio vuole il cabinato originale di __sf2ce__) non importa, ci penserà M.A.M.E. SDL Plus (diciamo c'ho pensato io con parecchie linee di codice :lol:) a ricreare tutto correttamente.

Fatto questo basterà lanciare l'emulatore con il parametro __hd-artwork__, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -hd-artwork`

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __HD Artwork On/Off__ per mostrare/nascondere l'artwork con il M.A.M.E. in esecuzione premendo semplicemente un pulsante.

Questi sono alcuni artworks di esempio in formato .lyt creati dagli utenti del [forum](https://www.retropie-italia.it):

[1942](https://drive.google.com/file/d/1UGGUGA5TA6OZEGP6tHbJOA9ABbUeMNB1/view?usp=sharing)
[1943](https://drive.google.com/file/d/1r7n3oMDNh9c6VnJG3SIH1bJ5OYZETCIe/view?usp=sharing)
[altbeast](https://drive.google.com/file/d/1tB20bAZbQ51DmupcqJxTkE_AZhapx2Te/view?usp=sharing)
[asteroid](https://drive.google.com/file/d/1Y8xlD20Q7n0VZo146f3SJEqRfAQS7lrR/view?usp=sharing)
[baddudes](https://drive.google.com/file/d/12EmYTOlsPoyEANgSwlHcVs2ImQrB3xqR/view?usp=sharing)
[bublbobl](https://drive.google.com/file/d/14Jf6Pg5SM-oYXzpUG_LyKZKz3z_AG4qH/view?usp=sharing)
[dkong](https://drive.google.com/file/d/1-9nxLmR-Ei9ID134BqdiDHvlFZyb7kQo/view?usp=sharing)
[invaders](https://drive.google.com/file/d/1fKEb1IpgKkoKWbmIy3ScaogFMlH7ll4d/view?usp=sharing)
[mercs](https://drive.google.com/file/d/1l7fC3KTgT5R0bg8F9Uj2Wxo2hVoTiNdd/view?usp=sharing)
[puckman](https://drive.google.com/file/d/1QKfVpUj0Y7P3hj0Q8RJtPBwpCP0lmWvS/view?usp=sharing)
[sf2ce](https://drive.google.com/file/d/1SngabHwJGtuy_NkB4yBym0rMIctyMESX/view?usp=sharing)
[shdancer](https://drive.google.com/file/d/1FihbCAoWRTcvO4AiFIahV9KuZolrieKe/view?usp=sharing)
[simpsons](https://drive.google.com/file/d/1iOY-dvXuAjMZwi1f-DwjH0qwIyph40KW/view?usp=sharing)
[spacewar](https://drive.google.com/file/d/1KIDKrD5a3zs8oAtl82FWfiFX1TEn6anx/view?usp=sharing)
[warrior](https://drive.google.com/file/d/1mbOuX3WqOAhWDLId1hMHHhqgWI98WPTg/view?usp=sharing)

### SIMPLE SCANLINES
Le scanlines servono per imitare l'effetto video dei vecchi schermi CRT e di default sono disabilitate: è possibile aggiungere il parametro __simple-scanlines__ alla riga di comando per attivarle, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -simple-scanlines`

Questo effetto non potrà essere attivato se uno degli effetti [CRT pixel](README_it.md#crt-pixel-effects) risulta attivo.

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __Scanlines On/Off__ per attivare/disattivare le scanlines con il M.A.M.E. in esecuzione premendo semplicemente un pulsante

### CRT PIXEL EFFECTS
Ho creato 3 effetti video per imitare la resa di uno schermo CRT (in termini di "pixel") sui moderni display HD. Gli effetti sono questi e per default sono tutti disabilitati:

* __crt-pixel__ --> emulate CRT pixel (mutually exclusive with simple scanlines)
* __crt-pixel-scanlines-flicker__ --> emulate CRT pixel with scanlines flickering (mutually exclusive with simple scanlines)
* __crt-pixel-shape-flicker__ --> emulate CRT pixel with pixel shape flickering (mutually exclusive with simple scanlines)

Il secondo e terzo effetto aggiungono (alla simulazione di un pixel generato da un tubo catodico) il flickering (tremolio) tipico degli schermi CRT, uno con l'ausilio di scanlines, l'altro tramite la distorsione del pixel stesso.

Questi 3 effetti non potranno essere attivati se l'effetto [scanlines](README_it.md#simple-scanlines) risulta attivo. Da riga di comando potete avviare l'emulatore con un effetto predefinito, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -crt-pixel-scanlines-flicker`

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __Change CRT Pixel effect__ per "scorrere" i 3 effetti con il M.A.M.E. in esecuzione premendo semplicemente un pulsante. Il flusso è il seguente:

`all disabled --> crt-pixel --> crt-pixel-scanlines-flicker --> crt-pixel-shape-flicker --> all disabled`

### VIDEO INTERPOLATION - CRT BLUR
Esiste la possibilità di attivare un filtro video utilizzato nello scaling dell'immagine, a discapito dell'aggiunta di un [effetto blur](https://en.wikipedia.org/wiki/Gaussian_blur), che va a smussare i pixel. Per usarlo è possibile passare il parametro __linear-filter__ o il parametro __best-filter__, alla riga di comando, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -linear-filter`

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -best-filter`

> Attualmente è indifferente utilizzare uno o l'altro 

### VERTICAL REFRESH SYNCHRONIZATION
Ho inserito la possibilità di attivare, o meno, il vertical sync per evitare fenomeni di [tearing](https://en.wikipedia.org/wiki/Screen_tearing). Per default il vertical sync è attivo ma è possibile disattivarlo passando il parametro __novsync__ da riga di comando, ad esempio

`./mame_rpi3 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -novsync`

Su PC (Windows o Linux) e su Raspberry Pi v0, v1, v2 e v3 decidete voi se lasciare attiva l'opzione mentre su Raspberry Pi v4 è __necessario__ _non disattivarla_ a causa di un bug nel driver video (leggete [qui](https://www.retropie-italia.it/viewtopic.php?p=9715#p9715) per capire cosa accade). Da quel che ho visto su Raspberry Pi v1 è leggermente deleterio (si può perdere circa 1 FPS)

> Prestate attenzione al fatto che se il vostro schermo ha un refresh di 50 Hz non andrete mai oltre i 50 frames al secondo con il vertical sync attivo

Riporto un esempio di cosa succede su un display 50 Hz (15 secondi circa di runtime giusto per dare l'idea):

Opzione __vsync disattivata__

```
End game summary:
Main loop frequency: 60.152317 Hz
Nominal FPS: 60.000000
Real FPS: 60.152317

Total play time: 15.494000 seconds
```

Opzione __vsync attivata__

```
End game summary:
Main loop frequency: 60.052562 Hz
Nominal FPS: 60.000000
Real FPS: 49.737188

Total play time: 15.220000 seconds
```

Come vedete (parametro __Real FPS__) se il vsync è disattivato pur essendo lo schermo a 50 Hz il gioco viene eseguito al framerate nominale, ovvero 60 FPS. Al contrario con il vsync attivato essendo lo schermo a 50 Hz il gioco viene eseguito a 50 FPS

> Ovviamente se un gioco ha un framerate nominale di 37 Hz e lo schermo ha un refresh video di valore superiore (ad esempio 50 Hz o 60 Hz) il gioco funzionerà regolarmente a 37 FPS

> __Ricapitolando__:
se avete un Raspberry Pi v4 __non dovete disattivare__ il vsync, negli altri casi vedete voi ;-)

### SELEZIONE DISPOSITIVO AUDIO
È possibile selezionare la periferica audio passando il parametro __audio-device__ da riga di comando, ad esempio

`./mame_rpi3 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -audio-device 1`

dove il numero dopo il parametro si riferisce alla periferica __1__

> Per visualizzare una lista mnemonica dei dispositivi avviate l'emulatore, chiudetelo, e controllate quelli disponibili elencati nel log __M.A.M.E. SDL Plus.log__ in modo da poter utilizzare il numero corretto

### SALVATAGGIO HIGH SCORES
Non tutti i giochi arcade avevano la possibilità di salvare i punteggi record ma in questo porting è supportata una logica che permette ai suddetti giochi di farlo.

Nella directory che contiene l'eseguibile del M.A.M.E., _non nella cartella_ __hi__, deve esser presente il file __hiscore.dat__ che trovate allegato insieme agli eseguibili sistema per sistema.

__Quel file non contiene gli high scores ma indica al M.A.M.E. l'area di memoria del gioco da dove salvare (per poi ripristinare) il valore__

Fatto ciò se il romset è supportato dal file hiscore.dat, e soprattutto se i dati contenuti nel file sono corretti, quando uscirete dal gioco verrà creato un file nella cartella __hi__ con il nome del romset ed estensione .hi.

Per sapere se un gioco è supportato aprite il file __hiscore.dat__ e cercate il nome del romset che vi interessa.

Tutt'oggi il file __hiscore.dat__ è supportato dalla versione corrente del M.A.M.E., il formato è molto simile quindi potenzialmente potete anche provare a inserire qualche gioco (con le opportune modifiche) che non è presente nel file incluso ma che lo è nella versione corrente, lo trovate [qui](https://github.com/mamedev/mame/blob/master/plugins/hiscore/hiscore.dat).

Le differenze per passare dal nuovo formato al vecchio formato sono infatti banali, questo ad esempio è Final Fight:

__OLD__ hiscore.dat

```
ffight:
0:ff850c:3c:ff:00
0:ff80a0:04:00:00
```

__LATEST__ hiscore.dat

```
ffight:
@:maincpu,program,ff850c,3c,ff,00
@:maincpu,program,ff80a0,04,00,00
```

### FILE DI CONFIGURAZIONE
Se la vostra riga di comando sta diventando troppo lunga è possibile ulizzare un file di configurazione anziché passare i parametri alla riga di comando. È sufficiente creare il file __mame.ini__ e posizionarlo nella stessa cartella che contiene l'eseguibile di M.A.M.E. SDL Plus. Una volta creato il file inserite all'interno i parametri, ad esempio:

```
vsync 1
linear-filter 0
best-filter 0
window 1
framebuffer-width 1024
framebuffer-height 768
simple-scanlines 0
crt-pixel 0
crt-pixel-scanlines-flicker 1
crt-pixel-shape-flicker 0
hd-artwork 1
```

> __1__ sta per True, attivo, mentre __0__ sta per False, disattivo

Se volete potete sfruttare la cartella __ini__ presente nello stesso percorso dell'eseguibile e posizionare il file al suo interno. La priorità di questo file è _inferiore alla riga di comando_, quindi se nel file inserite

`window 1`

ma alla riga di comando passate __nowindow__ il gioco si avvierà in fullscreen. La configurazione può essere creata anche per singolo romset come descritto [qui](README_it.md#configurazione-per-singolo-romset)

### CONFIGURAZIONE PER SINGOLO ROMSET
In un modo simile al [file di configurazione](README_it.md#file-di-configurazione) globale, potete sfruttare la cartella __ini__ presente nello stesso percorso dell'eseguibile e posizionare al suo interno un file di configurazione per ogni romset.

Ad esempio potreste voler giocare il romset __puckman__ con un monitor 16/9 posizionato in verticale utilizzando l'opzione __rotate-counterclockwise__ da riga di comando. Il problema è che in questo modo tutti i giochi risulterebbero ruotati... La soluzione quindi è quella di creare il file di configurazione del singolo romset, nel caso di esempio __puckman.ini__, e inserire l'opzione al suo interno:

`rotate-counterclockwise 1`

> __1__ sta per True, attivo, mentre __0__ sta per False, disattivo

La priorità di questo file è _superiore a quella del file_ __mame.ini__ (ma _inferiore alla riga di comando_)

### VERSIONE ROMSET DA UTILIZZARE
Non dovete fare altro che copiare le vostre roms __versione 0.61+__ nella cartella __roms__ oppure, se state integrando l'emulatore in RetroPie, nella cartella __mamesdlplus__ come spiegato nelle sezioni apposite.

Per ricreare il set giusto usate [MAME Set Rebuilder](https://www.retropie-italia.it/viewtopic.php?p=3868#p3868), o [Clrmamepro](https://mamedev.emulab.it/clrmamepro/), con il file .dat allegato al programma oppure estraetelo direttamente dall'eseguibile di M.A.M.E. SDL Plus come dettagliatamente spiegato [qui](https://www.retropie-italia.it/viewtopic.php?p=3867#p3867)

### TASTIERA
Come di conseuto di default premete Tab per configurare i comandi tramite il menù di configurazione del M.A.M.E. (usate le frecce ed Invio), premete Esc per tornare indietro (o annullare una precedente associazione) e, se il menù non è visualizzato, per chiudere l'emulatore. Sempre come default i tasti 5 e 1 servono rispettivamente per inserire i coins e premere Start per il giocatore 1.

I tasti configurabili sono tutte le lettere dalla A alla Z, tutti le cifre da 0 a 9 (tastierino numerico _incluso_), i tasti funzione da F1 a F12, i tasti Escape, Backspace, Tab, Invio, Spazio, Canc, le frecce direzionali (tastierino numerico _escluso_), il blocco maiuscole, Shift, Ctrl, Alt (questi ultimi 3 sia destro che sinistro). Tutti gli altri sono stati volutamente esclusi per non creare confusione con la loro differente posizione a seconda del layout tastiera scelto (italiano, inglese ecc.).

Ad esempio potreste usare W, S, A, D, J, K ed L ragionevolmente associabili in un gioco ad Up, Down, Left, Right, Button 1, Button 2 e Button 3 del giocatore 1

### JOYPAD
Potete collegare fino a 4 joypads conteporaneamente e procedere come di consueto alla loro configurazione premendo Tab su una tastiera collegata ad emulatore avviato (di default usate le frecce ed Invio, premete Esc per tornare indietro o annullare una precedente associazione e, se il menù non è visualizzato, per chiudere l'emulatore).

Quando configurate i joypads tramite il menù del M.A.M.E. la configurazione si basa sull'ID che il sistema operativo assegna ai joypads. Quindi al primo avvio collegate i joypads, ogni joypad in una determinata porta USB, e configurateli nel menù del M.A.M.E. come spiegato sopra. Se durante il gioco scollegate e ricollegate un joypad, o più di uno, anche se cambiate porta USB non avrete nessun impatto sul mapping che avete eseguito, ovvero potrete continuare a giocare con gli stessi joypad associati agli stessi giocatori. La magia funziona a runtime, se però chiudete l'emulatore e lo riavviate dovrete avere i joypads collegati nelle stesse porte USB di quando avete fatto la prima configurazione, soprattutto se utilizzate joypads diversi, XBOX 360, PlayStation ecc.

Questo è un surplus, nessun emulatore si preoccupa di questo fatto lasciando all'utente l'incombenza di non scollegare i joypads durante l'esecuzione. Ha richiesto parecchie righe di codice e un sistema molto complicato di gestione dei dati per i joypads disconnessi, forse ho perso tempo, ma a me piace di più così ;-)

### TRACKBALL
Allo stesso modo dello [spinner](README_it.md#spinner), per poter usare una trackball è necessario aggiungere questi parametri alla riga di comando per l'avvio dell'emulatore:

```
trackball-id-1
trackball-id-2
trackball-id-3
trackball-id-4
```

Per gli IDs da utilizzare assieme ai parametri __trackball-id-*__ è necessario conoscere il nome della periferica così come creato da Linux durante l'avvio, quindi vi basterà eseguire questo comando

`ls -lh /dev/input/by-id`

e utilizzare le stringhe che terminano con __-event-mouse__. Ad esempio sul mio sistema quel comando riporta questo:

```
total 0
lrwxrwxrwx 1 root root 10 giu 15 10:51 usb-1ea7_2.4G_Mouse-event-if00 -> ../event21
lrwxrwxrwx 1 root root 10 giu 15 10:51 usb-1ea7_2.4G_Mouse-event-mouse -> ../event22
lrwxrwxrwx 1 root root  9 giu 15 10:51 usb-1ea7_2.4G_Mouse-mouse -> ../mouse5
lrwxrwxrwx 1 root root 10 giu 15 10:15 usb-Apple__Inc_Apple_Keyboard-event-if01 -> ../event20
lrwxrwxrwx 1 root root 10 giu 15 10:15 usb-Apple__Inc_Apple_Keyboard-event-kbd -> ../event19
lrwxrwxrwx 1 root root 10 giu 15 10:15 usb-Logitech_USB_Optical_Mouse-event-mouse -> ../event18
lrwxrwxrwx 1 root root  9 giu 15 10:15 usb-Logitech_USB_Optical_Mouse-mouse -> ../mouse4
lrwxrwxrwx 1 root root 10 giu 15 10:53 usb-PixArt_Microsoft_USB_Optical_Mouse-event-mouse -> ../event23
lrwxrwxrwx 1 root root  9 giu 15 10:53 usb-PixArt_Microsoft_USB_Optical_Mouse-mouse -> ../mouse6
lrwxrwxrwx 1 root root  9 giu 14 23:27 usb-SunplusIT_Inc_EasyCamera-event-if00 -> ../event9
```

e quindi per giocare ad esempio con 2 trackballs la riga di comando di lancio dell'emulatore sarà questa:

`./mame_rpi4 arcadecl -trackball-id-1 usb-Logitech_USB_Optical_Mouse-event-mouse -trackball-id-2 usb-PixArt_Microsoft_USB_Optical_Mouse-event-mouse -spinner-id-1 usb-1ea7_2.4G_Mouse-event-mouse`

Come avrete notato nella riga di lancio è presente anche uno spinner, dovete quindi sapere che il M.A.M.E. non distingue tra movimento analogico di una trackball e movimento analogico di uno spinner. Il core del M.A.M.E. si occupa del movimento dei Players, non distingue la richiesta per tipo di periferica, ed essendo presente sia una trackball che uno spinner associati al Player 1 (hanno entrambi ID 1) è possibile usare entrambe le periferiche per controllarlo.

Questo __non comporta nessun problema di gameplay__, è chiaro che dovrete evitare di giocare a __Missile Command II__ con la trackball mentre il nipotino/amico dispettoso armeggia sullo spinner :lol:

Ovviamente per giocare al meglio dovete utilizzare la periferica per cui il gioco è stato progettato. Se non sapete quale sia premete Tab e spostatevi in __Analog Controls__, se trovate la parola __Dial__ il gioco utilizzava uno spinner (o un volante come in __Championship Sprint__), se trovate la parola __Track__ utilizzava una trackball, se il sottomenù __Analog Controls__ non è presente non usava né uno né l'altra. Sempre nel menù __Analog Controls__ è possibile aumentare la sensibilità del dispositivo qualore fosse necessario.

> Non cercate di modificare l'input, __Track X__, __Track Y__, tramite il menù accessibile con il tasto Tab, non è necessario

Se aumentando la sensibilità del dispositivo tramite il menù del M.A.M.E. non ottenete l'effetto desiderato potete utilizzare il parametro __analog-boost__ da riga di comando, che di default è disabilitato, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arcadecl -analog-boost`

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __Boost Analog Sensitivity On/Off__ per attivare/disattivare l'aumento di sensibilità con il M.A.M.E. in esecuzione premendo semplicemente un pulsante

### SPINNER
Allo stesso modo della [trackball](README_it.md#trackball), per poter usare uno spinner è necessario aggiungere questi parametri alla riga di comando per l'avvio dell'emulatore:

```
spinner-id-1
spinner-id-2
spinner-id-3
spinner-id-4
```

Per gli IDs da utilizzare assieme ai parametri __spinner-id-*__ è necessario conoscere il nome della periferica così come creato da Linux durante l'avvio, quindi vi basterà eseguire questo comando

`ls -lh /dev/input/by-id`

e utilizzare le stringhe che terminano con __-event-mouse__. Ad esempio sul mio sistema quel comando riporta questo:

```
total 0
lrwxrwxrwx 1 root root 10 giu 15 10:51 usb-1ea7_2.4G_Mouse-event-if00 -> ../event21
lrwxrwxrwx 1 root root 10 giu 15 10:51 usb-1ea7_2.4G_Mouse-event-mouse -> ../event22
lrwxrwxrwx 1 root root  9 giu 15 10:51 usb-1ea7_2.4G_Mouse-mouse -> ../mouse5
lrwxrwxrwx 1 root root 10 giu 15 10:15 usb-Apple__Inc_Apple_Keyboard-event-if01 -> ../event20
lrwxrwxrwx 1 root root 10 giu 15 10:15 usb-Apple__Inc_Apple_Keyboard-event-kbd -> ../event19
lrwxrwxrwx 1 root root 10 giu 15 10:15 usb-Logitech_USB_Optical_Mouse-event-mouse -> ../event18
lrwxrwxrwx 1 root root  9 giu 15 10:15 usb-Logitech_USB_Optical_Mouse-mouse -> ../mouse4
lrwxrwxrwx 1 root root 10 giu 15 10:53 usb-PixArt_Microsoft_USB_Optical_Mouse-event-mouse -> ../event23
lrwxrwxrwx 1 root root  9 giu 15 10:53 usb-PixArt_Microsoft_USB_Optical_Mouse-mouse -> ../mouse6
lrwxrwxrwx 1 root root  9 giu 14 23:27 usb-SunplusIT_Inc_EasyCamera-event-if00 -> ../event9
```

e quindi per giocare con uno spinner la riga di comando di lancio dell'emulatore sarà questa:

`./mame_rpi4 arcadecl -trackball-id-1 usb-Logitech_USB_Optical_Mouse-event-mouse -trackball-id-2 usb-PixArt_Microsoft_USB_Optical_Mouse-event-mouse -spinner-id-1 usb-1ea7_2.4G_Mouse-event-mouse`

Come avrete notato nella riga di lancio sono presenti anche 2 trackballs, dovete quindi sapere che il M.A.M.E. non distingue tra movimento analogico di una trackball e movimento analogico di uno spinner. Il core del M.A.M.E. si occupa del movimento dei Players, non distingue la richiesta per tipo di periferica, ed essendo presente sia una trackball che uno spinner associati al Player 1 (hanno entrambi ID 1) è possibile usare entrambe le periferiche per controllarlo.

Questo __non comporta nessun problema di gameplay__, è chiaro che dovrete evitare di giocare a __Missile Command II__ con la trackball mentre il nipotino/amico dispettoso armeggia sullo spinner :lol:

Ovviamente per giocare al meglio dovete utilizzare la periferica per cui il gioco è stato progettato. Se non sapete quale sia premete Tab e spostatevi in __Analog Controls__, se trovate la parola __Dial__ il gioco utilizzava uno spinner (o un volante come in __Championship Sprint__), se trovate la parola __Track__ utilizzava una trackball, se il sottomenù __Analog Controls__ non è presente non usava né uno né l'altra. Sempre nel menù __Analog Controls__ è possibile aumentare la sensibilità del dispositivo qualore fosse necessario.

> Non cercate di modificare l'input, __Dial__, tramite il menù accessibile con il tasto Tab, non è necessario

Se aumentando la sensibilità del dispositivo tramite il menù del M.A.M.E. non ottenete l'effetto desiderato potete utilizzare il parametro __analog-boost__ da riga di comando, che di default è disabilitato, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arkanoid -analog-boost`

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __Boost Analog Sensitivity On/Off__ per attivare/disattivare l'aumento di sensibilità con il M.A.M.E. in esecuzione premendo semplicemente un pulsante

### MOUSE
Allo stesso modo di una trackball o di uno spinner è possibile utilizzare un mouse per giocare, molto spesso un ottimo sostituto se non possedete una trackball. Nelle versioni per Windows e OSX/macOS non è necessario eseguire alcuna configurazione, è sufficiente collegare il mouse e utilizzarlo!

Nelle versioni per __Raspberry Pi__ e quella per sistemi __Ubuntu-based__ è necessario eseguire la [configurazione](README_it.md#trackball) come se fosse una trackball.

Oltre a questo è possibile impostare fino a 3 pulsanti del mouse (per un giocatore soltanto) premendo come di consueto Tab per accedere al menù di configurazione del M.A.M.E.

Ovviamente per giocare al meglio dovete utilizzare la periferica per cui il gioco è stato progettato. Se non sapete quale sia premete Tab e spostatevi in __Analog Controls__, se trovate la parola __Dial__ il gioco utilizzava uno spinner (o un volante tipo A.P.B.), se trovate la parola __Track__ utilizzava una trackball, se il sottomenù __Analog Controls__ non è presente non usava né uno né l'altra. Sempre nel menù __Analog Controls__ è possibile aumentare la sensibilità del dispositivo qualore fosse necessario.

Se aumentando la sensibilità del dispositivo tramite il menù del M.A.M.E. non ottenete l'effetto desiderato potete utilizzare il parametro __analog-boost__ da riga di comando, che di default è disabilitato, ad esempio

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arkanoid -analog-boost`

Oltre a ciò nel menù del M.A.M.E. c'è la possibilità di configurare l'opzione __Boost Analog Sensitivity On/Off__ per attivare/disattivare l'aumento di sensibilità con il M.A.M.E. in esecuzione premendo semplicemente un pulsante

### VERSIONE RASPBERRY PI OS
> L'emulatore è stato compilato come __eseguibile a 32 bit__, gli step seguenti sono validi per un sistema a 32 bit

Attualmente la libreria __SDL Image__ installabile con Raspberry Pi OS (ex Raspbian), il sistema operativo alla base di Raspberry Pi, è una versione non recentissima che si appoggia a una versione della libreria __libpng__ (v1.6.36) che contiene un bug. Per poter quindi usare correttamente l'emulatore dovete compilare entrambe queste librerie dal codice sorgente con alcuni semplici passi che vado a indicarvi

> Se avete la libreria installata rimuovetela con questo comando:
`sudo apt remove --purge libsdl2-image-2.0-0 libsdl2-image-dev`
Se mancante, installate la libreria SDL di sviluppo con questo comando:
`sudo apt install libsdl2-dev`

Le librerie necessarie sono queste, [libpng16.zip](https://github.com/glennrp/libpng/archive/libpng16.zip) e [SDL2_image-2.0.5.zip](https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip), per installarle eseguite questi comandi in sequenza (tra un passaggio e l'altro dovrete attendere un po' di tempo, aspettate che ogni operazione venga completata correttamente):

_*LibPNG*_

```
cd /home/pi
wget https://github.com/glennrp/libpng/archive/libpng16.zip
unzip libpng16.zip
cd libpng-libpng16/
./configure
make
sudo make install
sudo ldconfig
```

_*SDL Image*_

```
cd /home/pi
wget https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip
unzip SDL2_image-2.0.5.zip
cd SDL2_image-2.0.5/
mkdir build
cd build/
../configure
make -j$(nproc)
sudo make install
sudo ldconfig
```

A questo punto potete lanciare l'emulatore da riga di comando oppure integrarlo in RetroPie come spiegato [qui](README_it.md#integrazione-in-retropie-su-raspberry-pi)

> Se il vostro Raspberry Pi è connesso a un monitor VGA-DVI, quindi per l'audio utilizzate il jack apposito, nella riga di comando potreste dover aggiungere il parametro __audio-device__, ad esempio:
`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -audio-device 1`
Dipende dalla versione del sistema operativo che state utilizzando, controllate il log e verificate quali dispositivi audio sono presenti come descritto [qui](README_it.md#selezione-dispositivo-audio)

### VERSIONE UBUNTU E DERIVATI
L'emulatore è stato compilato su Ubuntu 20.04 (potrebbe non funzionare su versioni precedenti) come __eseguibile a 32 bit__ e, come per il Raspberry Pi, dovete avere installate le librerie __SDL__ e __SDL Image__, entrambe in __versione 32 bit__. Vi spiego in qualche semplice passo come compilarle dai sorgenti.

_*Prerequisiti*_
Dal terminale eseguite questi comandi in sequenza seguiti da invio:

```
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo apt install gcc-multilib build-essential git make cmake autoconf automake libtool libasound2-dev:i386 libpulse-dev libpulse-dev:i386 libaudio-dev:i386 libx11-dev:i386 libxext-dev:i386 libxrandr-dev:i386 libxcursor-dev:i386 libxfixes-dev:i386 libxi-dev:i386 libxss-dev:i386 libgl1-mesa-dev:i386 libdbus-1-dev:i386 libudev-dev:i386 libgles2-mesa-dev:i386 libegl1-mesa-dev:i386 libibus-1.0-dev:i386 fcitx-libs-dev:i386 libsamplerate0-dev:i386 libsndio-dev:i386 libwayland-dev:i386 libxkbcommon-dev:i386 libdrm-dev:i386 libgbm-dev:i386 libpng-dev:i386
```

_*SDL*_
Scaricate SDL da [qui](https://www.libsdl.org/release/SDL2-2.0.20.zip), copiate il pacchetto nella home del vostro utente, estraete il codice sorgente e rinominate la cartella estratta in SDL, poi eseguite in sequenza questi comandi nel terminale:

```
cd SDL
mkdir build
cd build
../configure "CFLAGS=-m32" "CXXFLAGS=-m32" "LDFLAGS=-m32" --libdir=/usr/lib32
make -j$(nproc)
sudo make install
sudo ldconfig
```

_*SDL Image*_
Scaricate SDL Image da [qui](https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip), copiate il pacchetto nella home del vostro utente, estraete il codice sorgente e rinominate la cartella estratta in SDL_IMAGE, poi eseguite in sequenza questi comandi nel terminale:

```
cd SDL_IMAGE
mkdir build
cd build/
../configure "CFLAGS=-m32" "CXXFLAGS=-m32" "LDFLAGS=-m32" --libdir=/usr/lib32
make -j$(nproc)
sudo make install
sudo ldconfig
```

A questo punto potete lanciare l'emulatore da riga di comando, integrarlo in RetroPie come spiegato [qui](README_it.md#integrazione-in-retropie-su-sistemi-ubuntu-e-derivati) oppure utilizzarlo tramite [MAME Simple Frontend](https://www.retropie-italia.it/viewtopic.php?p=4568#p4568)

> Inserite MAME Simple Frontend dove sono presenti le cartelle __artwork__, __cfg__ ecc. di M.A.M.E. SDL Plus

### VERSIONE WINDOWS
L'emulatore è stato compilato su Windows 10 (potrebbe non funzionare su versioni precedenti) ed è sufficiente lanciare l'eseguibile da riga di comando in quanto le librerie necessarie sono contenute nella cartella insieme al M.A.M.E.

Per comodità __è consigliabile utilizzare un frontend__, uno vale l'altro, se ne volete uno senza fronzoli c'è sempre [MAME Simple Frontend](https://www.retropie-italia.it/viewtopic.php?p=4568#p4568) che sviluppo personalmente

> Inserite MAME Simple Frontend dove sono presenti le cartelle __artwork__, __cfg__ ecc. di M.A.M.E. SDL Plus

### VERSIONE OSX/MACOS
Compilato su OSX El Capitan 10.11.6 (potrebbe non funzionare su versioni precedenti), avete bisogno, come per gli altri sistemi, di utilizzare le librerie __SDL__ e __SDL Image__, entrambe in __versione 32 bit__. Vi spiego in qualche semplice passo come compilarle dai sorgenti.

_*SDL*_
Scaricate SDL da [qui](https://www.libsdl.org/release/SDL2-2.0.20.zip), copiate il pacchetto nella home del vostro utente, estraete il codice sorgente e rinominate la cartella estratta in SDL, poi eseguite in sequenza questi comandi nel terminale:

```
cd SDL
mkdir build
cd build
CFLAGS=-m32 CXXFLAGS=-m32 LDFLAGS=-m32 ../configure
make -j$(nproc)
sudo make install
```

_*SDL Image*_
Scaricate SDL Image da [qui](https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip), copiate il pacchetto nella home del vostro utente, estraete il codice sorgente e rinominate la cartella estratta in SDL_IMAGE, poi eseguite in sequenza questi comandi nel terminale:

```
cd SDL_IMAGE
mkdir build
cd build/
CFLAGS=-m32 CXXFLAGS=-m32 LDFLAGS=-m32 ../configure
make -j$(nproc)
sudo make install
```

A questo punto riavviate, anche se non dovrebbe essere necessario, e potrete così lanciarlo da riga di comando oppure utilizzarlo tramite [MAME Simple Frontend](https://www.retropie-italia.it/viewtopic.php?p=4568#p4568)

> Inserite MAME Simple Frontend dove sono presenti le cartelle __artwork__, __cfg__ ecc. di M.A.M.E. SDL Plus

### INTEGRAZIONE IN RETROPIE SU RASPBERRY PI
Dopo aver seguito [questa sezione](README_it.md#versione-raspberry-pi-os), scaricate l'emulatore ed estraetelo sul vostro computer. Sul Raspberry Pi aprite il file [es_systems.cfg](https://www.retropie-italia.it/viewtopic.php?f=60&t=265) con questo comando

`sudo nano /etc/emulationstation/es_systems.cfg`

> ...se utilizzate il file [es_systems.cfg](https://www.retropie-italia.it/viewtopic.php?f=16&t=11) personalizzato dovete aggiungere la configurazione in quel file...

e aggiungete in fondo al file questa configurazione

```
<system>
    <name>mamesdlplus</name>
    <fullname>MAME SDL Plus</fullname>
    <path>/home/pi/RetroPie/roms/mamesdlplus</path>
    <extension>.zip .ZIP</extension>
    <command>cd /home/pi/MAMESDLPlus; ./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus %ROM%</command>
    <platform>arcade</platform>
    <theme>mame</theme>
</system>
```

> __Attenzione__: nel tag __command__ sostituite _mame_rpi4_ con il M.A.M.E. compatibile con il vostro Raspberry Pi, ad esempio per un Raspberry Pi v2 scrivete _mame_rpi2_

> Se volete cambiare logo/tema al sistema seguite [questa](https://www.retropie-italia.it/viewtopic.php?p=9263#p9263) guida

Create la cartella __mamesdlplus__ e la cartella __MAMESDLPlus__ rispettivamente con questi comandi:

`mkdir /home/pi/RetroPie/roms/mamesdlplus`

`mkdir /home/pi/MAMESDLPlus`

Copiate l'eseguibile dell'emulatore, nel nostro esempio __mame_rpi4__, insieme alla cartelle presenti nell'archivio .zip nella cartella __MAMESDLPlus__.

Riavviate EmulationStation (o il sistema) ;-)

> Se volete avviare un gioco direttamente all'avvio del sistema leggete [questa](https://www.retropie-italia.it/viewtopic.php?p=7088#p7088) guida

> Se il vostro Raspberry Pi è connesso a un monitor VGA-DVI, quindi per l'audio utilizzate il jack apposito, nella riga di comando potreste dover aggiungere il parametro __audio-device__, ad esempio:
`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -audio-device 1`
Dipende dalla versione del sistema operativo che state utilizzando, controllate il log e verificate quali dispositivi audio sono presenti come descritto [qui](README_it.md#selezione-dispositivo-audio)

### INTEGRAZIONE IN RETROPIE SU SISTEMI UBUNTU E DERIVATI
Se volete integrare l'emulatore in RetroPie effettuate una configurazione simile a [quella](README_it.md#integrazione-in-retropie-su-raspberry-pi) spiegata per Raspberry Pi tenendo a mente che il percorso del file __es_systems.cfg__ potrebbe essere diverso

### INSTALLAZIONE DEBIAN LXDE + EMULATIONSTATION + MAME SDL PLUS
Con questa guida installerete da zero Debian LXDE (x86-64) con EmulationStation e M.A.M.E. SDL Plus così da avere un sistema che all'avvio partirà direttamente su EmulationStation, ideale per un cabinato :-)

__Prima e durante l'installazione:__

- Disabilitate, se presente, il Fast Boot dal BIOS

- Se durante l'installazione non riuscite a collegarvi alla rete wireless scegliete l'opzione "Enter ESSID manually"

- Create una partizione EFI da 512 MB

- Create una partizione di swap da 8 GB a fine disco

- Quando richiesto _deselezionate_ Debian desktop environment e GNOME, aggiungete invece LXDE e SSH server

- Ad installazione completata riabilitate, se lo avete disabilitato, il Fast Boot dal BIOS

> Nella guida sostituite __<your_username>__, in tutti i comandi che seguono, col vostro nome utente

__Al primo avvio:__

Dal Desktop di LXDE collegatevi alla rete tramite __Preferences --> Connman Settings__

`nano /home/<your_username>/.bashrc`

Aggiungete in fondo questa riga:

`export PATH=$PATH:/usr/sbin`

Passate all'utente __root__ ed eseguite:

```
/usr/sbin/usermod -aG sudo <your_username>
nano /etc/default/grub
```

Cambiate questa riga:

`GRUB_TIMEOUT="5"`

in questa:

`GRUB_TIMEOUT="1"`

Eseguite questo comando:

`update-grub`

Tornate all'utente normale ed eseguite:

`/usr/sbin/reboot`

Dopo il riavvio:

```
sudo apt update
sudo apt upgrade
sudo apt install net-tools
```

Per compilare applicazioni 32 bit su sistemi a 64 bit dovete procedere come segue:

`sudo apt install make gcc-i686-linux-gnu`

Compilate SDL con questi passi:

```
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install libsamplerate0-dev libsamplerate0-dev:i386 libudev-dev libdbus-1-dev:i386 libibus-1.0-dev:i386 libpulse-dev:i386 libx11-dev:i386 libxext-dev:i386 libasound2-dev:i386 libaudio-dev:i386 libxcursor-dev:i386 libxi-dev:i386 libxss-dev:i386 fcitx-libs-dev:i386 libsndio-dev:i386 libxkbcommon-dev:i386 libgbm-dev:i386
mkdir /home/<your_username>/sdl-sources
cd /home/<your_username>/sdl-sources/
wget https://www.libsdl.org/release/SDL2-2.0.22.zip
unzip SDL2-2.0.22.zip
cd SDL2-2.0.22/
mkdir build
cd build
../configure --host=i686-linux-gnu --build=x86_64-linux-gnu --libdir=/usr/lib/i386-linux-gnu
make -j$(nproc)
sudo make install
sudo ldconfig
```

Compilate SDL Image con questi passi:

```
sudo apt install libpng-dev:i386
cd /home/<your_username>/sdl-sources/
wget https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip
unzip SDL2_image-2.0.5.zip
cd SDL2_image-2.0.5/
mkdir build
cd build/
../configure --host=i686-linux-gnu --build=x86_64-linux-gnu --libdir=/usr/lib/i386-linux-gnu
make -j$(nproc)
sudo make install
sudo ldconfig
```

Adesso procediamo con EmulationStation e tutto il resto, non avviate EmulationStation prima della fine della guida!!!

__Compilazione:__

```
sudo apt install git cmake g++ libgles2-mesa-dev libsdl2-dev libfreetype-dev libfreeimage-dev libcurl4-openssl-dev libvlc-dev rapidjson-dev
cd /home/<your_username>/
git clone --recursive https://github.com/RetroPie/EmulationStation.git
cd EmulationStation/
cmake -DUSE_MESA_GLES=On .
make
```

__Installazione:__

```
mkdir ~/.emulationstation
cp emulationstation ~/.emulationstation/
cp emulationstation.sh ~/.emulationstation/
cp -r resources/ ~/.emulationstation/
```

__Installazione tema:__

```
mkdir ~/.emulationstation/themes
cd ~/.emulationstation/themes
wget https://github.com/RetroPie/es-theme-carbon-2021/archive/refs/heads/master.zip
unzip master.zip
rm master.zip
```

__Configurazione M.A.M.E. SDL Plus__

`nano ~/.emulationstation/es_systems.cfg`

Aggiungete questo e salvate:

```
<systemList>
	<system>
		<name>mamesdlplus</name>
		<fullname>MAME SDL Plus</fullname>
		<path>/home/<your_username>/MAMESDLPlus/roms</path>
		<extension>.zip .ZIP</extension>
		<command>cd /home/<your_username>/MAMESDLPlus; ./mame_linux32 %ROM%</command>
		<platform>arcade</platform>
		<theme>mame</theme>
	</system>
</systemList>
```

Passiamo all'avvio automatico di EmulationStation. Dal Desktop di LXDE procedete così:

__Preferences --> Default applications for LXSession --> Autostart__

Aggiungete questo:

`/home/<your_username>/.emulationstation/emulationstation.sh`

nella casella di testo accanto al pulsante __+Add__ e premetelo.

Infine per far sì che l'opzione di riavvio e spegnimento dal menù di EmulationStation funzioni seguite questi ultimi passi:

`sudo visudo`

e aggiungete in fondo questo:

```
<your_username> ALL=NOPASSWD:/sbin/reboot
<your_username> ALL=NOPASSWD:/sbin/shutdown
```

Adesso dovete attivare l'autologin, ci sono miliardi di modi (che non funzionano!), io ho fatto così:

`sudo nano /etc/lightdm/lightdm.conf`

Cercate __la sezione__ che inizia con __[Seat:*]__ e decommentate e configurate queste opzioni:

```
#autologin-user=
#autologin-user-timeout=0
```

Copiate M.A.M.E. SDL Plus e tutte le sue cartelle in

`/home/<your_username>/MAMESDLPlus`

e riavviate con

`sudo shutdown -r now`

> ATTENZIONE: __al primo avvio__ di EmulationStation, _dopo aver configurato la tastiera_, riavviatelo subito dal suo menù onde evitare che all'uscita dall'emulatore l'input da tastiera non funzioni!!!

> Su qualche hardware potrebbe rendersi necessaria la disinstallazione di PulseAudio. Nel caso in cui l'audio qualche volta non funzioni eseguite:
`sudo apt remove --purge pulseaudio`

__Guide originali Debian LXDE:__ https://www.retropie-italia.it/viewtopic.php?p=11454#p11454 a cura di Yojimbo

### AIUTO / RICHIESTA FUNZIONALITA'
Se avete dubbi, pensate di aver trovato un bug o volete proporre nuove funzionalità, scrivete senza problemi in [questo](https://www.retropie-italia.it/viewtopic.php?p=8301#p8301) thread. L'emulatore a ogni avvio crea un file di nome __M.A.M.E. SDL Plus.log__ che contiene diverse informazioni che possono risultare utili in caso di problemi e non.

Direi che non resta niente da aggiungere se non __Buon M.A.M.E.__ a tutti :D

