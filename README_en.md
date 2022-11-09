# M.A.M.E. SDL Plus
A fast and optimized M.A.M.E. cross-platform emulator with a __real CRT effect__!

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=LDCDAQUTH5A9Y)

![RealCRT](/images/ffight_real-crt.png)

### Table of Contents:

* #### Overview:
  * [BIRTH OF THE PROJECT](README_en.md#birth-of-the-project)
  * [REAL CRT VERSION](README_en.md#real-crt-version)
  * [DEMO VIDEOS](README_en.md#demo-videos)

* #### Features and benefits:
  * [TRACKBALL SUPPORT](README_en.md#trackball-support)
  * [SPINNER SUPPORT](README_en.md#spinner-support)
  * [ADDED / MODIFIED ROMSET](README_en.md#added--modified-romset)
  * [ADAPTIVE DYNAMIC FRAMESKIPPING](README_en.md#adaptive-dynamic-frameskipping)
  * [CUSTOMIZABLE FRAMEBUFFER](README_en.md#customizable-framebuffer)
  * [FRAMEBUFFER ROTATION](README_en.md#framebuffer-rotation)
  * [HD ARTWORKS](README_en.md#hd-artworks)
  * [SIMPLE SCANLINES](README_en.md#simple-scanlines)
  * [CRT PIXEL EFFECTS](README_en.md#crt-pixel-effects)
  * [VIDEO INTERPOLATION - CRT BLUR](README_en.md#video-interpolation---crt-blur)
  * [VERTICAL REFRESH SYNCHRONIZATION](README_en.md#vertical-refresh-synchronization)
  * [AUDIO DEVICE SELECTION](README_en.md#audio-device-selection)
  * [HIGH SCORES SAVE](README_en.md#high-scores-save)
  * [CONFIGURATION FILE](README_en.md#configuration-file)
  * [CONFIGURATION FOR SINGLE ROMSET](README_en.md#configuration-for-single-romset)

* #### Romset:
  * [ROMSET VERSION TO USE](README_en.md#romset-version-to-use)

* #### Controls configuration:
  * [KEYBOARD](README_en.md#keyboard)
  * [JOYPAD](README_en.md#joypad)
  * [TRACKBALL](README_en.md#trackball)
  * [SPINNER](README_en.md#spinner)
  * [MOUSE](README_en.md#mouse)

* #### Supported Operating Systems:
  * [RASPBERRY PI OS VERSION](README_en.md#raspberry-pi-os-version)
  * [UBUNTU VERSION AND DERIVATIVES](README_en.md#ubuntu-version-and-derivatives)
  * [WINDOWS VERSION](README_en.md#windows-version)
  * [OSX/MACOS VERSION](README_en.md#osxmacos-version)

* #### How to integrate in RetroPie:
  * [INTEGRATION IN RETROPIE ON RASPBERRY PI](README_en.md#integration-in-retropie-on-raspberry-pi)
  * [INTEGRATION IN RETROPIE ON UBUNTU AND DERIVATIVE SYSTEMS](README_en.md#integration-in-retropie-on-ubuntu-and-derivative-systems)

* #### Create a system with Debian LXDE (x86-64):
  * [INSTALL DEBIAN LXDE + EMULATIONSTATION + MAME SDL PLUS](README_en.md#install-debian-lxde--emulationstation--mame-sdl-plus)

* #### Support:
  * [HELP / FEATURE REQUEST](README_en.md#help--feature-request)


## BIRTH OF THE PROJECT
The purpose from which it all started was __to be able to use the M.A.M.E. on Raspberry Pi v1 with the additional support for the artworks__.

The base code is the one from version 0.61: someone may ask, __why 0.61__? Initially I chose it because it was the first version with native support for external artworks but then I realized that there was no possibility to use them in High Definition. At that point, however, some of the work had already been done, which is why I subsequently wrote from scratch the code to support them. Furthermore, 0.61 is an intermediate and mature version between 0.37b5 (used in the past by other porting) and the _very famous 0.78_, so I went ahead on this path

> The porting is __not deliberately__ burdened by the additional layer of the Libretro versions (so nothing __lr-__ in front of the name) and of the 0.61 version it only keeps the basic core. If you don't believe that Libretro cores are heavy try to run lr-mame2003 on a Raspberry Pi v1 ;-)

__The code is highly optimized__, I have used lookup tables and a whole bunch of logic to reduce the CPU load, __and it works on different systems__! To achieve the goal of multiplatform, the layer towards the operating system uses the SDL library so that the code can be compiled for any system that supports it, i.e. Windows, Linux, macOS etc. Furthermore, compared to version 0.61, whose core is the starting point, more games have been added, at time of writing __M.A.M.E. SDL Plus is the only port based on a version lower than 0.126 that features__ __World Rally (set 1)__ (romset name __wrally__) perfectly __working__, (and if necessary others will be added) and this is one of the reasons, in addition to the new features compared to the starting version, for which the project is called M.A.M.E. __SDL__ _Plus_ :D

Among the various changes, which you find illustrated in the topics, there is the __possibility__, as mentioned at the beginning, __to use artworks in high resolution (.lyt format) as well as being able to play with 4 trackballs and 4 spinners at the same time__!

The port easily holds __real__ 60 frames per second on Raspberry Pi, apart from the first model. For RPi v1, however, the code I wrote comes in handy where, by implementing an __automatic and dynamic frameskipping system__, some frames are skipped _when needed_ making the execution on the first Raspberry Pi practically full speed for many games! Fortunately our eyes don't notice when this happens :lol:

For the Raspberry Pi v1 overclocking is required (as with all M.A.M.E.), follow [this guide](https://www.retropie-italia.it/viewtopic.php?p=7808#p7808) on the forum

### REAL CRT VERSION
The __Real CRT__ version of the emulator is a special version with an effect realized by directly programming a low level shader with OpenGL. Currently, it is only available for Raspberry Pi v4 and x86 architecture systems. The executable to use is the one with the suffix __real_crt__. In this mode, of course, no other video effects are available

### DEMO VIDEOS
To give you an idea of ​​the work done right away, here are a couple of demonstration videos!

__Development PC vs Raspbery Pi v1__

Here is a video with a run comparison between the laptop I'm developing on and the Raspberry Pi v1:

[PC vs Raspberry Pi v1](https://drive.google.com/file/d/1XLGHF3zitmshKRqBJhUJhVQGYpB2ucCm/view?usp=sharing)

Seeing is believing ;-)

__M.A.M.E. SDL Plus vs lr-mame2003__

This video shows the performance difference on __Raspberry Pi v1__ between lr-mame2003 and my emulator:

[Raspberry Pi v1: lr-mame2003 vs M.A.M.E. SDL Plus](https://drive.google.com/file/d/127u8PJ_vs-OoQVXb9tuyVK3fv-FRlaAd/view?usp=sharing)

I don't think I'm biased if I say that lr-mame2003 doesn't hold up to comparison ;-)

### TRACKBALL SUPPORT
The versions for Raspberry Pi and the one for Ubuntu-based systems support the use of __4 trackballs connected at the same time__, which is the maximum number of players available in games that used this control system.

The versions for __Windows and OSX/macOS__ _only support one player_ with this control system and __no [configuration](README_en.md#trackball) is needed__.

M.A.M.E. doesn't distinguish between analog movement of a trackball and analog movement of a spinner. The core of the M.A.M.E. deals with the movement of the Players, does not distinguish the request by type of peripheral, if there are both trackballs and spinners associated with the same Player (always true on the versions for Windows and OSX/macOS) it is possible to use both peripherals to control it.

This __does not involve any gameplay problems__, it is clear that you will have to avoid playing __Missile Command II__ with the trackball while the spiteful nephew/friend fumbles on the spinner :lol:

Obviously, to play the best you have to use the peripheral for which the game was designed. If you don't know what it is, press Tab and move to __Analog Controls__, if you find the word __Dial__ the game used a spinner (or a steering wheel as in __Championship Sprint__), if you find the word __Track__ it used a trackball, if the submenu __Analog Controls__ is not present it used neither one nor the other. Still in the __Analog Controls__ menu it is possible to increase the sensitivity of the device if necessary.

If by increasing the sensitivity of the device through the M.A.M.E. you do not get the desired effect you can use the command line parameter __analog-boost__, which is disabled by default, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arcadecl -analog-boost`

In addition to this in the M.A.M.E. menu there is the possibility to configure the __Boost Analog Sensitivity On/Off__ option to enable/disable the sensitivity increase using a button while M.A.M.E. is running.

List of games using the trackball:

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

### SPINNER SUPPORT
The versions for Raspberry Pi and the one for Ubuntu-based systems support the use of __4 spinners connected at the same time__.

The versions for __Windows and OSX/macOS__ _only support one player_ with this control system and __no [configuration](README_en.md#spinner) is needed__.

The M.A.M.E. it does not distinguish between analog movement of a trackball and analog movement of a spinner. The core of the M.A.M.E. deals with the movement of the Players, does not distinguish the request by type of peripheral, if there are both trackballs and spinners associated with the same Player (always true on the versions for Windows and OSX/macOS) it is possible to use both peripherals to control it.

This __does not involve any gameplay problems__, it is clear that you will have to avoid playing __Missile Command II__ with the trackball while the spiteful nephew/friend fumbles on the spinner :lol:

Obviously, to play the best you have to use the peripheral for which the game was designed. If you don't know what it is, press Tab and move to __Analog Controls__, if you find the word __Dial__ the game used a spinner (or a steering wheel as in __Championship Sprint__), if you find the word __Track__ it used a trackball, if the submenu __Analog Controls__ is not present he used neither one nor the other. Still in the __Analog Controls__ menu it is possible to increase the sensitivity of the device if necessary.

If by increasing the sensitivity of the device through the M.A.M.E. you do not get the desired effect you can use the command line parameter __analog-boost__, which is disabled by default, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arkanoid -analog-boost`

In addition to this in the M.A.M.E. menu there is the possibility to configure the __Boost Analog Sensitivity On/Off__ option to enable/disable the sensitivity increase using a button while M.A.M.E. is running.

List of games using the spinner:

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

### ADDED / MODIFIED ROMSET
At time of writing __M.A.M.E. SDL Plus is the only port based on a version lower than 0.126 that features__ __World Rally (set 1)__ (romset name __wrally__) perfectly __working__ :-)

> To recreate the correct set use [MAME Set Rebuilder](https://www.retropie-italia.it/viewtopic.php?p=3868#p3868) (or [Clrmamepro](https://mamedev.emulab.it/clrmamepro/)) with the file __0.61+.dat__ that you find in the archive containing the emulator or [extract it](https://www.retropie-italia.it/viewtopic.php?p=3867#p3867) directly from the executable of M.A.M.E. SDL Plus

Compared to version 0.61 there are several changes:

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

> Some of the above games are already present in version 0.61. If they are indicated in this list it is because they are trivially __passed from not working to working__ or because their code is different from version 0.61

### ADAPTIVE DYNAMIC FRAMESKIPPING
I totally changed the frameskipping logic present in the M.A.M.E. greatly improving performance on Raspberry Pi v1 and v0. To understand how the execution went when the emulator is closed you will see in the log, among others, this information:

```
End game summary:
Main loop frequency: 60.000802 Hz
Nominal FPS: 60.000000
Real FPS: 60.000802

Total play time: 3192.074000 seconds
```

__Real FPS__ refers to the frames per second shown on the screen, if the value is the same as __Nominal FPS__ the performance will be in all respects the same as that of the original cabinet. But beware, the magic is this: __Main loop frequency__ refers to the cycles per second of the game's main loop, i.e. input, sound, video, etc. If this value is close to or identical to the __Nominal FPS__ value, the performance _perceived_ will be the same to that of the original cabinet _even if_ __Real FPS__ does not coincide with __Nominal FPS__.

Normally when __Main loop frequency__ and __Real FPS__ coincide, it means that no frame has been skipped during execution: however, if the vertical sync is active they could be different for synchronization reasons

> The audio/video synchronization, as well as the maintenance of nominal frames per second, uses a logic based on the audio hardware. If you have audio problems, an incorrect configuration, not working audio, etc., the FPS may not be respected (for example, you may run into exceeding the nominal framerate with games that will be accelerated)

### CUSTOMIZABLE FRAMEBUFFER
It is possible to arbitrarily set the size of the video framebuffer, that is the size of the area in which the game will be shown, when the emulator is running _in fullscreen_ mode. Just launch the emulator with the parameters __framebuffer-width__ and __framebuffer-height__, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -framebuffer-width 1280 -framebuffer-height 996`

The code is intelligent so the final dimensions will be recalculated at the start of the game so that the __aspect ratio__ of the original cabinet is __maintained__.

This can be __particularly useful if you have a very large screen and want to reduce the size of the game__, or you have built an arcade cabinet but the opening in the wood slightly covers the edges of the screen: in this second case you can use this feature and then center the framebuffer with respect to the cabinet opening with the controls placed on your monitor.

Besides that it is possible to rotate the framebuffer as explained [here](README_en.md#framebuffer-rotation)

### FRAMEBUFFER ROTATION
It is possible to rotate the video framebuffer when using the __fullscreen mode__. Just launch the emulator with the option __rotate-clockwise__ or __rotate-counterclockwise__, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus puckman -rotate-counterclockwise`

As for the [customizable framebuffer](README_en.md#customizable-framebuffer), the code is intelligent so the final dimensions will be recalculated so that the __aspect ratio__ of the original cabinet (and possibly the artwork) is __maintained__ by exploiting the most space possible

### HD ARTWORKS
The artworks are the graphics that surrounded the monitor of the cabinets

> __Retrostory__: The origin of the artworks is very varied.
The support was initially only hardcoded in the game driver, this up to version 0.60: in other words it was not possible to add an, generically said, external overlay, (which is why I often read about people asking why in M.A.M.E. 0.37b5 the artworks _not work_ albeit present in the artwork folder).
Version 0.61 was the first version that allowed the use of artworks in .art format, artworks which, however, could only be in low resolution. From version 0.107, the artworks are supported (also in high resolution) in .lay format.
The source code was then modified __with M.A.M.E. SDL Plus artworks in high resolution can be used__ in .lyt format. Just insert the image in .png format in the artwork folder with the same name as the romset (for Final Fight it will therefore be ffight.png) and a text file, with the .lyt extension and always with the name of the romset (for Final Fight so it will be ffight.lyt).

For example, for the romset __sf2ce__ you have the following content of the file __sf2ce.lyt__:

```
Width="4000" Height="3743"
GameAreaWidth="2920" GameAreaHeight="2190"
GameAreaX="540" GameAreaY="822"
ArtworkType="merged"
```

__Width__ and __Height__ are trivially width and height in pixels of the .png image, nothing mysterious.

__GameAreaWidth__ and __GameAreaHeight__ represent the width and height of the area where you want the game to be shown, in the case of __sf2ce__ they represent the "hole" in the image, expressed in pixels with respect to the image.

__GameAreaX__ and __GameAreaY__ are the X coordinate and the Y coordinate, expressed in pixels, where the game will be positioned (the origin is top left) and in this case they represent the top left corner of the "hole" in the image.

__ArtworkType__ accepts the _ontop_ and _merged_ options. The default value is __merged__ so if the parameter is missing the behavior will be __merged__ type. The meaning is quickly explained:

* __merged__: for example in the romset __warrior__ the artwork linked below is nothing more than the background of the game, so the final result shown on the screen will be a fusion of images, the game frame, the artwork and any active video effects
* __ontop__: unlike the _merged_ mode, the artwork is drawn above the game frame. In this way, if the artwork overlaps the game area, the final effect will be, in my opinion, cuter at the expense of not seeing a part of the game area.

To make you understand even better, here you can observe the difference between __merged__ and __ontop__ in __Bubble Bobble__ respectively:

![bublbobl-merged](/images/bublbobl_merged.png)
![bublbobl-ontop](/images/bublbobl_ontop.png)

In the end it is a matter of taste, clearly if in the romset __warrior__ you use the __ontop__ option, and the artwork itself does not provide transparency (as in the case of the one attached below), you will not see the game but only the background :lol:

__Warrior__ configured correctly:

![warrior](/images/warrior.png)

The code is intelligent so subsequently the dimensions will be recalculated so that the aspect ratio of the original cabinet is maintained, so if __GameAreaWidth__ and __GameAreaHeight__ are not for example 4:3 (as for example the original cabinet of __sf2ce__ wants) it does not matter, M.A.M.E. SDL Plus will recreate everything correctly (let's say I thought about it with several lines of code :lol:).

Once this is done, just launch the emulator with the __hd-artwork__ parameter, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -hd-artwork`

In addition to this in the M.A.M.E. menu there is the possibility to configure the __HD Artwork On/Off__ option to show/hide the artwork using a button while M.A.M.E. is running.

These are some example artworks in .lyt format created by the users of the [forum](https://www.retropie-italia.it):

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
Scanlines are used to imitate the video effect of old CRT screens and by default they are disabled: you can add the __simple-scanlines__ parameter to the command line to enable them, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -simple-scanlines`

This effect cannot be activated if one of the [CRT pixel](README_en.md#crt-pixel-effects) effects is active.

In addition to this in the M.A.M.E. menu there is the possibility to configure the __Scanlines On/Off__ option to enable/disable scanlines using a button while M.A.M.E. is running


### CRT PIXEL EFFECTS
I created 3 video effects to mimic the rendering of a CRT screen (in terms of "pixels") on modern HD displays. The effects are these and by default they are all disabled:

* __crt-pixel__ --> emulate CRT pixel (mutually exclusive with simple scanlines)
* __crt-pixel-scanlines-flicker__ --> emulate CRT pixel with scanlines flickering (mutually exclusive with simple scanlines)
* __crt-pixel-shape-flicker__ --> emulate CRT pixel with pixel shape flickering (mutually exclusive with simple scanlines)

The second and third effects add (to the simulation of a pixel generated by a cathode ray tube) the flickering typical of CRT screens, one with the help of scanlines, the other through the distortion of the pixel itself.

These 3 effects cannot be activated if the [scanlines](README_en.md#simple-scanlines) effect is active. From the command line you can start the emulator with a predefined effect, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -crt-pixel-scanlines-flicker`

In addition to this in the M.A.M.E. menu there is the possibility to configure the __Change CRT Pixel effect__ option to "scroll" the 3 effects using a button while M.A.M.E. is running. The flow is as follows:

`all disabled --> crt-pixel --> crt-pixel-scanlines-flicker --> crt-pixel-shape-flicker --> all disabled`

### VIDEO INTERPOLATION - CRT BLUR
There is the possibility to activate a video filter used in image scaling, at the expense of adding a [blur effect](https://en.wikipedia.org/wiki/Gaussian_blur), which smooths the pixels. To use it you can pass the __linear-filter__ parameter or the __best-filter__ parameter, on the command line, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -linear-filter`

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -best-filter`

> Currently there is no difference to use one or the other

### VERTICAL REFRESH SYNCHRONIZATION
I added the possibility to activate, or not, the vertical sync to avoid [tearing](https://en.wikipedia.org/wiki/Screen_tearing) phenomena. By default vertical sync is active but you can disable it by passing the __novsync__ parameter from the command line, for example

`./mame_rpi3 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -novsync`

On PC (Windows or Linux) and on Raspberry Pi v0, v1, v2 and v3 you decide whether to leave the option active while on Raspberry Pi v4 it is __necessary__ _not deactivate it_ due to a bug in the video driver (read [here](https://www.retropie-italia.it/viewtopic.php?p=9715#p9715) to understand what happens). From what I've seen on Raspberry Pi v1 it is slightly deleterious (you can lose around 1 FPS)

> Pay attention to the fact that if your screen has a refresh of 50 Hz you will never go beyond 50 frames per second with vertical sync active

Here is an example of what happens on a 50 Hz display (about 15 seconds of runtime just to give the idea):

Option __vsync disabled__

```
End game summary:
Main loop frequency: 60.152317 Hz
Nominal FPS: 60.000000
Real FPS: 60.152317

Total play time: 15.494000 seconds
```

Option __vsync enabled__

```
End game summary:
Main loop frequency: 60.052562 Hz
Nominal FPS: 60.000000
Real FPS: 49.737188

Total play time: 15.220000 seconds
```

As you can see (parameter __Real FPS__) if the vsync is disabled despite being the screen at 50 Hz the game runs at the nominal framerate, that is 60 FPS. Conversely, with vsync activated being the screen at 50 Hz the game runs at 50 FPS

> Obviously if a game has a nominal framerate of 37Hz and the screen has a higher video refresh value (e.g. 50Hz or 60Hz) the game will run smoothly at 37 FPS

> __Summarizing__:
if you have a Raspberry Pi v4 __don't disable__ vsync, in the other cases it's your choice ;-)

### AUDIO DEVICE SELECTION
You can select the audio device by passing the __audio-device__ command line parameter, for example

`./mame_rpi3 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -audio-device 1`

where the number after the parameter refers to the device __1__

> To view a mnemonic list of devices, start the emulator, close it, and check the available ones listed in the __M.A.M.E log. SDL Plus.log__ so you can use the correct number

### HIGH SCORES SAVE
Not all arcade games had the ability to save high scores but in this port is supported a logic that allows the aforementioned games to do so.

In the directory that contains the executable of the M.A.M.E., _not in the folder_ __hi__, there must be the file __hiscore.dat__ which you find attached together with the executables system by system.

__This file does not contain the high scores but indicates to the M.A.M.E. the game memory area from which to save (and then restore) the value__

Once this is done if the romset is supported by the hiscore.dat file, and especially if the data contained in the file is correct, when you exit the game a file will be created in the __hi__ folder with the name of the romset and the extension .hi.

To find out if a game is supported, open the __hiscore.dat__ file and search for the name of the romset you are interested in.

Even today the __hiscore.dat__ file is supported by the current version of the M.A.M.E., the format is very similar so you can potentially also try to insert some game (with the appropriate modifications) that is not present in the included file but which is in the current version, you can find it [here](https://github.com/mamedev/mame/blob/master/plugins/hiscore/hiscore.dat).

The differences to switch from the new format to the old format are in fact trivial, this for example is Final Fight:

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

### CONFIGURATION FILE
If your command line is getting too long you can use a configuration file instead of passing parameters to the command line. Just create the __mame.ini__ file and place it in the same folder that contains the executable of M.A.M.E. SDL Plus. Once the file has been created, add the parameters, for example:

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

> __1__ stands for True, active, while __0__ stands for False, inactive

If you want you can take advantage of the __ini__ folder present in the same path as the executable and place the file inside it. The priority of this file is _lower than the command line_, so if in the file you insert

`window 1`

but at the command line pass __nowindow__ the game will start in fullscreen. The configuration can also be created for single romset as described [here](README_en.md#configuration-for-single-romset)


### CONFIGURATION FOR SINGLE ROMSET
In a similar way to the global [configuration file](README_en.md#configuration-file), you can take advantage of the __ini__ folder in the same path as the executable and place a configuration file inside it for each romset.

For example you may want to play the __puckman__ romset with a 16/9 monitor positioned vertically using the __rotate-counterclockwise__ command line option. The problem is that in this way all the games would be rotated ... The solution then is to create the configuration file of the single romset, in the case of the example __puckman.ini__, and insert the option in it:

`rotate-counterclockwise 1`

> __1__ stands for True, active, while __0__ stands for False, inactive

The priority of this file is _higher than that of file_ __mame.ini__ (but _lower than the command line_)

### ROMSET VERSION TO USE
All you have to do is copy your roms __version 0.61+__ in the __roms__ folder or, if you are integrating the emulator in RetroPie, in the __mamesdlplus__ folder as explained in the appropriate sections.

To recreate the right set use [MAME Set Rebuilder](https://www.retropie-italia.it/viewtopic.php?p=3868#p3868), or [Clrmamepro](https://mamedev.emulab.it/clrmamepro/), with the .dat file attached to the program or extract it directly from the executable of M.A.M.E. SDL Plus as explained in detail [here](https://www.retropie-italia.it/viewtopic.php?p=3867#p3867)

### KEYBOARD
As usual, by default, press Tab to configure the commands via the M.A.M.E. configuration menu. (use the arrows and Enter), press Esc to go back (or cancel a previous association) and, if the menu is not displayed, to close the emulator. Also by default, the 5 and 1 keys are used respectively to insert coins and press Start for player 1.

The configurable keys are all letters from A to Z, all digits 0 to 9 (numeric keypad _included_), the function keys from F1 to F12, the Escape, Backspace, Tab, Enter, Space, Del keys, the directional arrows (numeric keypad _excluded_), the caps lock, Shift, Ctrl, Alt (the latter 3 both right and left). All the others have been deliberately excluded in order not to create confusion with their different position depending on the keyboard layout chosen (Italian, English, etc.).

For example you could use W, S, A, D, J, K and L reasonably associated in a game to Up, Down, Left, Right, Button 1, Button 2 and Button 3 of player 1

### JOYPAD
You can connect up to 4 joypads at the same time and proceed as usual to their configuration by pressing Tab on a keyboard connected with the emulator running (by default use the arrows and Enter, press Esc to go back or cancel a previous association and, if the menu is not displayed, to close the emulator).

When configuring the joypads via the M.A.M.E. the configuration is based on the ID that the operating system assigns to the joypads. So at the first start connect the joypads, each joypad in a specific USB port, and configure them in the M.A.M.E. as explained above. If during the game you disconnect and reconnect a joypad, or more than one, even if you change the USB port you will not have any impact on the mapping you have performed, i.e. you can continue playing with the same joypads associated with the same players. The magic works at runtime, but if you close the emulator and restart it you will need to have the joypads connected to the same USB ports as when you did the first configuration, especially if you use different joypads, XBOX 360, PlayStation etc.

This is a surplus, no emulator cares about this fact leaving the user the task of not disconnecting the joypads during execution. It required several lines of code and a very complicated data management system for disconnected joypads, maybe I wasted time, but I like it more like this ;-)

### TRACKBALL
Like the [spinner](README_en.md#spinner), in order to use a trackball you need to add these parameters to the command line when starting the emulator:

```
trackball-id-1
trackball-id-2
trackball-id-3
trackball
```

For the IDs to be used together with the __trackball-id-*__ parameters you need to know the name of the device as created by Linux during boot, so just run this command

`ls -lh /dev/input/by-id`

and use strings ending with __-event-mouse__. For example on my system that command reports this:

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

and therefore to play for example with 2 trackballs the emulator launch command line will be this:

`./mame_rpi4 arcadecl -trackball-id-1 usb-Logitech_USB_Optical_Mouse-event-mouse -trackball-id-2 usb-PixArt_Microsoft_USB_Optical_Mouse-event-mouse -spinner-id-1 usb-1ea7_2.4G_Mouse-event-mouse`

As you may have noticed in the launch line there is also a spinner, so you should know that the M.A.M.E. it does not distinguish between analog movement of a trackball and analog movement of a spinner. The core of the M.A.M.E. deals with the movement of the Players, does not distinguish the request by type of peripheral, and since there is both a trackball and a spinner associated with Player 1 (both have ID 1) it is possible to use both peripherals to control it.

This __does not involve any gameplay problems__, it is clear that you will have to avoid playing __Missile Command II__ with the trackball while the spiteful nephew/friend fumbles on the spinner :lol:

Obviously, to play the best you have to use the peripheral for which the game was designed. If you don't know what it is, press Tab and move to __Analog Controls__, if you find the word __Dial__ the game used a spinner (or a steering wheel as in __Championship Sprint__), if you find the word __Track__ it used a trackball, if the submenu __Analog Controls__ is not present he used neither one nor the other. Still in the __Analog Controls__ menu it is possible to increase the sensitivity of the device if necessary.

> Do not try to modify the input, __Track X__, __Track Y__, through the menu accessible with the Tab key, it is not necessary

If by increasing the sensitivity of the device through the M.A.M.E. you do not get the desired effect you can use the command line parameter __analog-boost__, which is disabled by default, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arcadecl -analog-boost`

In addition to this in the M.A.M.E. menu there is the possibility to configure the __Boost Analog Sensitivity On/Off__ option to enable/disable the sensitivity increase using a button while M.A.M.E. is running

### SPINNER
Like the [trackball](README_en.md#trackball), in order to use a spinner you need to add these parameters to the command line when starting the emulator:

```
spinner-id-1
spinner-id-2
spinner-id-3
spinner-id-4
```

For the IDs to be used together with the __spinner-id-*__ parameters you need to know the name of the device as created by Linux during boot, so just run this command

`ls -lh /dev/input/by-id`

and use strings ending with __-event-mouse__. For example on my system that command reports this:

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

and then to play with a spinner the emulator launch command line will be this:

`./mame_rpi4 arcadecl -trackball-id-1 usb-Logitech_USB_Optical_Mouse-event-mouse -trackball-id-2 usb-PixArt_Microsoft_USB_Optical_Mouse-event-mouse -spinner-id-1 usb-1ea7_2.4G_Mouse-event-mouse`

As you may have noticed in the launch line there are also 2 trackballs, so you should know that the M.A.M.E. it does not distinguish between analog movement of a trackball and analog movement of a spinner. The core of the M.A.M.E. deals with the movement of the Players, does not distinguish the request by type of peripheral, and since there is both a trackball and a spinner associated with Player 1 (both have ID 1) it is possible to use both peripherals to control it.

This __does not involve any gameplay problems__, it is clear that you will have to avoid playing __Missile Command II__ with the trackball while the spiteful nephew/friend fumbles on the spinner :lol:

Obviously, to play the best you have to use the peripheral for which the game was designed. If you don't know what it is, press Tab and move to __Analog Controls__, if you find the word __Dial__ the game used a spinner (or a steering wheel as in __Championship Sprint__), if you find the word __Track__ it used a trackball, if the submenu __Analog Controls__ is not present he used neither one nor the other. Still in the __Analog Controls__ menu it is possible to increase the sensitivity of the device if necessary.

> Do not try to modify the input, __Dial__, via the menu accessible with the Tab key, it is not necessary

If by increasing the sensitivity of the device through the M.A.M.E. you do not get the desired effect you can use the command line parameter __analog-boost__, which is disabled by default, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arkanoid -analog-boost`

In addition to this in the M.A.M.E. menu there is the possibility to configure the __Boost Analog Sensitivity On/Off__ option to enable/disable the sensitivity increase using a button while M.A.M.E. is running

### MOUSE
Like a trackball or spinner you can use a mouse to play, very often a great replacement if you don't own a trackball. In the Windows and OSX/macOS versions it is not necessary to perform any configuration, just plug in the mouse and use it!

In __Raspberry Pi__ and __Ubuntu-based__ systems versions it is necessary to run the [configuration](README_en.md#trackball) as if it's a trackball.

In addition to this it is possible to set up to 3 mouse buttons (for one player only) by pressing Tab as usual to access the configuration menu of the M.A.M.E.

Obviously, to play the best you have to use the peripheral for which the game was designed. If you don't know what it is, press Tab and move to __Analog Controls__, if you find the word __Dial__ the game used a spinner (or a steering wheel like A.P.B.), if you find the word __Track__ it used a trackball, if the submenu __Analog Controls__ is not present it did not use neither one nor the other. Still in the __Analog Controls__ menu it is possible to increase the sensitivity of the device if necessary.

If by increasing the sensitivity of the device through the M.A.M.E. you do not get the desired effect you can use the command line parameter __analog-boost__, which is disabled by default, for example

`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus arkanoid -analog-boost`

In addition to this in the M.A.M.E. menu there is the possibility to configure the __Boost Analog Sensitivity On/Off__ option to enable/disable the sensitivity increase using a button while M.A.M.E. is running

### RASPBERRY PI OS VERSION
Currently the __SDL Image__ library that can be installed with Raspberry Pi OS (formerly Raspbian), the operating system underlying Raspberry Pi, is an older version that relies on a version of the __libpng__ library (v1.6.36) which contains a bug. In order to use the emulator correctly you have to compile both libraries from the source code with some simple steps that I am going to show you

> If you have the library installed remove it with this command:
`sudo apt remove --purge libsdl2-image-2.0-0 libsdl2-image-dev`

The necessary libraries are these, [libpng16.zip](https://github.com/glennrp/libpng/archive/libpng16.zip) and [SDL2_image-2.0.5.zip](https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip), to install them run these commands in sequence (between one step and the other you will have to wait some time, wait for each operation to complete correctly):

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
cd build
../configure
make -j$(nproc)
sudo make install
sudo ldconfig
```

At this point you can run the emulator from the command line or integrate it into RetroPie as explained [here](README_en.md#integration-in-retropie-on-raspberry-pi)

> If your Raspberry Pi is connected to a VGA-DVI monitor, then audio uses the appropriate jack, in the command line you may need to add the parameter __audio-device__, for example:
`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -audio-device 1`
It depends on the version of the operating system you are using, check the log and verify which audio devices are present as described [here](README_en.md#audio-device-selection)

### UBUNTU VERSION AND DERIVATIVES
The emulator was compiled on Ubuntu 20.04 (may not work on older versions) as a __32-bit executable__ and, as with the Raspberry Pi, you must have the __SDL__ and __SDL Image__ libraries installed, both in __32-bit version__. I'll explain in a few simple steps how to compile them from source.

_*Prerequisites*_
From the terminal execute these commands in sequence followed by enter:

```
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo apt install gcc-multilib build-essential git make cmake autoconf automake libtool libasound2-dev:i386 libpulse-dev libpulse-dev:i386 libaudio-dev:i386 libx11-dev:i386 libxext-dev:i386 libxrandr-dev:i386 libxcursor-dev:i386 libxfixes-dev:i386 libxi-dev:i386 libxss-dev:i386 libgl1-mesa-dev:i386 libdbus-1-dev:i386 libudev-dev:i386 libgles2-mesa-dev:i386 libegl1-mesa-dev:i386 libibus-1.0-dev:i386 fcitx-libs-dev:i386 libsamplerate0-dev:i386 libsndio-dev:i386 libwayland-dev:i386 libxkbcommon-dev:i386 libdrm-dev:i386 libgbm-dev:i386 libpng-dev:i386
```

_*SDL*_
Download SDL from [here](https://www.libsdl.org/release/SDL2-2.0.20.zip), copy the package to your user's home, extract the source code and rename the extracted folder to SDL, then execute these commands in sequence in the terminal:

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
Download SDL Image from [here](https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip), copy the package to your user's home, extract the source code and rename the folder extracted in SDL_IMAGE, then execute these commands in sequence in the terminal:

```
cd SDL_IMAGE
mkdir build
cd build
../configure "CFLAGS=-m32" "CXXFLAGS=-m32" "LDFLAGS=-m32" --libdir=/usr/lib32
make -j$(nproc)
sudo make install
sudo ldconfig
```

At this point you can run the emulator from the command line, integrate it into RetroPie as explained [here](README_en.md#integration-in-retropie-on-ubuntu-and-derivative-systems) or use it via [MAME Simple Frontend](https://www.retropie-italia.it/viewtopic.php?p=4568#p4568)

> Add MAME Simple Frontend where the M.A.M.E. SDL Plus __artwork__, __cfg__ etc. folders are present

### WINDOWS VERSION
The emulator was compiled on Windows 10 (it may not work on previous versions) and it is sufficient to launch the executable from the command line as the necessary libraries are contained in the folder together with the M.A.M.E.

For convenience __it is advisable to use a frontend__, one is as good as the other, if you want one with no frills there is always [MAME Simple Frontend](https://www.retropie-italia.it/viewtopic.php?p=4568#p4568) that I develop myself

> Add MAME Simple Frontend where the M.A.M.E. SDL Plus __artwork__, __cfg__ etc. folders are present

### OSX/MACOS VERSION
Compiled on OSX El Capitan 10.11.6 (may not work on previous versions), you need, as for other systems, to use the __SDL__ and __SDL Image__ libraries, both in __32 bit version__. I'll explain in a few simple steps how to compile them from source.

_*SDL*_
Download SDL from [here](https://www.libsdl.org/release/SDL2-2.0.20.zip), copy the package to your user's home, extract the source code and rename the extracted folder to SDL, then execute these commands in sequence in the terminal:

```
cd SDL
mkdir build
cd build
CFLAGS=-m32 CXXFLAGS=-m32 LDFLAGS=-m32 ../configure
make -j$(nproc)
sudo make install
```

_*SDL Image*_
Download SDL Image from [here](https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.0.5.zip), copy the package to your user's home, extract the source code and rename the folder extracted in SDL_IMAGE, then execute these commands in sequence in the terminal:

```
cd SDL_IMAGE
mkdir build
cd build
CFLAGS=-m32 CXXFLAGS=-m32 LDFLAGS=-m32 ../configure
make -j$(nproc)
sudo make install
```

At this point restart, even if it should not be necessary, and you can launch it from the command line or use it via [MAME Simple Frontend](https://www.retropie-italia.it/viewtopic.php?p=4568#p4568 )

> Add MAME Simple Frontend where the M.A.M.E. SDL Plus __artwork__, __cfg__ etc. folders are present

### INTEGRATION IN RETROPIE ON RASPBERRY PI
After following [this section](README_en.md#raspberry-pi-os-version), download the emulator and extract it to your computer. On the Raspberry Pi open the file [es_systems.cfg](https://www.retropie-italia.it/viewtopic.php?f=60&t=265) with this command

`sudo nano /etc/emulationstation/es_systems.cfg`

> ... if you use the custom file [es_systems.cfg](https://www.retropie-italia.it/viewtopic.php?f=16&t=11) you have to add the configuration in that file ...

and add this configuration at the bottom of the file

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

> __Attention__: in the __command__ tag replace _mame_rpi4_ with the M.A.M.E. compatible with your Raspberry Pi, for example for a Raspberry Pi v2 write _mame_rpi2_

> If you want to change the logo/theme to the system, follow [this](https://www.retropie-italia.it/viewtopic.php?p=9263#p9263) guide

Create the __mamesdlplus__ folder and the __MAMESDLPlus__ folder respectively with these commands:

`mkdir /home/pi/RetroPie/roms/mamesdlplus`

`mkdir /home/pi/MAMESDLPlus`

Copy the emulator executable, in our example __mame_rpi4__, together with the folders present in the .zip archive in the __MAMESDLPlus__ folder.

Restart EmulationStation (or the system) ;-)

> If you want to start a game directly when the system starts, read [this](https://www.retropie-italia.it/viewtopic.php?p=7088#p7088) guide

> If your Raspberry Pi is connected to a VGA-DVI monitor, then audio uses the appropriate jack, in the command line you may need to add the parameter __audio-device__, for example:
`./mame_rpi4 -rompath /home/pi/RetroPie/roms/mamesdlplus dino -audio-device 1`
It depends on the version of the operating system you are using, check the log and verify which audio devices are present as described [here](README_en.md#audio-device-selection)

### INTEGRATION IN RETROPIE ON UBUNTU AND DERIVATIVE SYSTEMS
If you want to integrate the emulator into RetroPie make a configuration similar to [that](README_en.md#integration-in-retropie-on-raspberry-pi) explained for Raspberry Pi bearing in mind that the path to the file __es_systems.cfg__ could be different

### INSTALL DEBIAN LXDE + EMULATIONSTATION + MAME SDL PLUS
With this guide you will be installing Debian LXDE (x86-64) from scratch with EmulationStation and M.A.M.E. SDL Plus so you'll run a system that will start directly on EmulationStation at boot, ideal for a cabinet :-)

__Before and during installation:__

- Disable, if present, the Fast Boot from the BIOS

- If during the installation you are unable to connect to the wireless network, choose the option "Enter ESSID manually"

- Create a 512MB EFI partition

- Create an 8GB swap partition at the end of the disk

- When prompted _deselect_ Debian desktop environment and GNOME, add LXDE and SSH server instead

- When installation is complete, re-enable Fast Boot from the BIOS if you have disabled it

> In the guide replace __<your_username>__, in all the following commands, with your username

__On first start:__

From the LXDE Desktop connect to the network via __Preferences --> Connman Settings__

`nano /home/<your_username>/.bashrc`

Add this line at the bottom:

`export PATH=$PATH:/usr/sbin`

Switch to user __root__ and run:

```
/usr/sbin/usermod -aG sudo <your_username>
nano /etc/default/grub
```

Change this line:

`GRUB_TIMEOUT="5"`

in this:

`GRUB_TIMEOUT="1"`

Run this command:

`update-grub`

Return to the normal user and run:

`/usr/sbin/reboot`

After reboot:

```
sudo apt update
sudo apt upgrade
sudo apt install net-tools
```

To compile 32-bit applications on 64-bit systems you have to proceed as follows:

`sudo apt install make gcc-i686-linux-gnu`

Compile SDL with these steps:

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

Compile SDL Image with these steps:

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

Now let's proceed with EmulationStation and everything else, do not start EmulationStation before the end of the guide!!!

__Compilation:__

```
sudo apt install git cmake g++ libgles2-mesa-dev libsdl2-dev libfreetype-dev libfreeimage-dev libcurl4-openssl-dev libvlc-dev rapidjson-dev
cd /home/<your_username>/
git clone --recursive https://github.com/RetroPie/EmulationStation.git
cd EmulationStation/
cmake -DUSE_MESA_GLES=On .
make
```

__Installation:__

```
mkdir ~/.emulationstation
cp emulationstation ~/.emulationstation/
cp emulationstation.sh ~/.emulationstation/
cp -r resources/ ~/.emulationstation/
```

__Theme installation:__

```
mkdir ~/.emulationstation/themes
cd ~/.emulationstation/themes
wget https://github.com/RetroPie/es-theme-carbon-2021/archive/refs/heads/master.zip
unzip master.zip
rm master.zip
```

__M.A.M.E. SDL Plus configuration__

`nano ~/.emulationstation/es_systems.cfg`

Add this and save:

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

Let's move on to the automatic startup of EmulationStation. From the LXDE Desktop proceed as follows:

__Preferences --> Default applications for LXSession --> Autostart__

Add this:

`/home/<your_username>/.emulationstation/emulationstation.sh`

in the text box next to the __+Add__ button and press it.

Finally, to make the restart and shutdown option from the EmulationStation menu work, follow these last steps:

`sudo visudo`

and add this at the bottom:

```
<your_username> ALL=NOPASSWD:/sbin/reboot
<your_username> ALL=NOPASSWD:/sbin/shutdown
```

Now you have to activate the autologin, there are billions of ways (that don't work!), I did this:

`sudo nano /etc/lightdm/lightdm.conf`

Find __the section__ starting with __[Seat:*]__ and uncomment and configure these options:

```
#autologin-user=
#autologin-user-timeout=0
```

Copy M.A.M.E. SDL Plus and all its folders in

`/home/<your_username>/MAMESDLPlus`

and restart with

`sudo shutdown -r now`

> ATTENTION: __during the first start__ of EmulationStation, _after configuring the keyboard_, restart it immediately from its menu to avoid that keyboard input does not work when exiting the emulator!!!

> PulseAudio may need to be uninstalled on some hardware. In case the audio sometimes does not work, execute:
`sudo apt remove --purge pulseaudio`

__Debian LXDE original guides:__ https://www.retropie-italia.it/viewtopic.php?p=11454#p11454 by Yojimbo

### HELP / FEATURE REQUEST
If you have any doubts, think you have found a bug or want to propose new features, write without problems in [this](https://www.retropie-italia.it/viewtopic.php?p=8301#p8301) thread. The emulator at each start creates a file named __M.A.M.E SDL Plus.log__ which contains various information that can be useful in case of problems and not.

I would say that there is nothing left to add, __Good M.A.M.E .__ to all :D

