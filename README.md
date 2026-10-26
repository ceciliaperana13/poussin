#  Poussin Destroyer

> **Une usine steampunk, un poussin, une seule mission : s'échapper.**

![Genre](https://img.shields.io/badge/genre-plateforme%203D-D4AF37)
![Style](https://img.shields.io/badge/style-steampunk%20%C2%B7%20humour-6E4E2E)
![Moteur](https://img.shields.io/badge/moteur-Unity-2B2B2B)
![Plateforme](https://img.shields.io/badge/plateforme-PC-2F5D7C)
![PEGI](https://img.shields.io/badge/PEGI-12%20(vis%C3%A9)-D64545)
![Statut](https://img.shields.io/badge/statut-prototype%20%2F%20pr%C3%A9-production-F28C3B)

---

## Sommaire

1. [Présentation](#-présentation)
2. [Pitch et USP](#-pitch-et-usp)
3. [Univers et histoire](#-univers-et-histoire)
4. [Personnages](#-personnages)
5. [Gameplay](#-gameplay)
6. [Contrôles](#-contrôles)
7. [Ennemis et obstacles](#-ennemis-et-obstacles)
8. [Niveau 1 : la chaîne de production](#-niveau-1--la-chaîne-de-production)
9. [Direction artistique](#-direction-artistique)
10. [Caméra](#-caméra)
11. [Ambiance sonore](#-ambiance-sonore)
12. [Public cible](#-public-cible)
13. [Références](#-références)
14. [Faisabilité et priorités](#-faisabilité-et-priorités)
15. [Documentation](#-documentation)

---

##  Présentation

**Poussin Destroyer** est un jeu de **plateforme 3D** à l'humour décalé, situé dans une immense usine de nuggets steampunk. Le joueur incarne un poussin minuscule qui doit **observer chaque salle, comprendre ses dangers et ses mécanismes**, puis choisir sa propre façon de progresser pour s'échapper et libérer ses semblables.

| | |
|---|---|
| **Genre** | Plateforme 3D, puzzle léger |
| **Ambiance** | Steampunk sombre, humour absurde |
| **Mode** | Solo, coopération à deux joueurs (priorité 2) |
| **Plateforme** | PC (clavier / manette) |
| **Moteur** | Unity |
| **Durée du niveau 1** | 10 à 15 minutes |
| **Classification visée** | PEGI 12 (à confirmer selon le rendu final) |

---

##  Pitch et USP

Le jeu commence sur une chaîne de production où tout est prévu pour fabriquer des nuggets. Sauf qu'un poussin s'est retrouvé sur la chaîne. Il court, saute, plane, donne des coups de bec et utilise un lasso pour franchir les obstacles. **Il n'y a pas toujours une seule bonne route** : activer un mécanisme, faire tomber un robot ou prendre un détour plus tranquille, chaque joueur avance à sa manière.

### Ce qui différencie le jeu

1. **Une coopération qui change la manière de jouer** : un grand et un petit poussin aux capacités complémentaires.
2. **Plusieurs façons de franchir les obstacles**, sans chemin imposé.
3. **Un humour né du contraste** : un poussin minuscule face à une usine démesurée, dialogues décalés, chutes et piaillements.

### Intention de design

Le jeu doit être **drôle et donner envie d'expérimenter**. Les dangers restent toujours faciles à comprendre pour que le joueur trouve le jeu amusant plutôt qu'injuste. Les essais sont illimités et les reprises rapides.

---

##  Univers et histoire

L'action se déroule dans l'usine de la célèbre entreprise **CHIKENTOWN**. En façade, elle promet les meilleurs nuggets du monde ; en réalité, c'est une boucherie qui s'attaque sans relâche aux poussins de la région.

Le **Patron** de CHIKENTOWN n'apparaît jamais en public et ne s'exprime que par haut-parleurs, sur un ton monotone de publicité. Pour lui, les poussins ne sont que des numéros et de futurs profits.

Un jour, le **poussin n°404** s'échappe de sa cage pendant un incident sur la chaîne. Voyant les autres prisonniers, il refuse de partir seul. Peureux mais déterminé, il transforme chaque salle en **mission secrète**, récupère un lasso, rencontre un mini-poussin capable de se faufiler dans les conduits et commence à saboter l'usine pour ouvrir les cages.

---

##  Personnages

### Poussin n°404 (héros)

Corps rond, petites ailes, grands yeux expressifs, silhouette jaune qui ressort sur les décors sombres. Stylisé en 3D, non photoréaliste. Il parle comme un héros de film d'action tout en découvrant les dangers en même temps que le joueur.

**Capacités** : courir, sauter, planer, coup de bec, lasso.

### Mini-poussin

Plus petit, silhouette facile à distinguer, gestes rapides et expressions calmes. Il réfléchit avant d'agir et se moque gentiment des discours du héros.

**Capacités** : traverser les conduits, atteindre leviers et boutons cachés. Il ne peut ni planer ni utiliser le lasso.

### Les autres poussins

Enfermés dans des cages, ils rappellent pourquoi 404 traverse l'usine. Leurs réactions à l'ouverture d'une cage sont montrées sans comportement complexe dans le prototype.

### Caractéristiques

| Élément | Poussin 404 | Mini-poussin |
|---|---|---|
| Unité de référence | 1 bloc ≈ 1 mètre | 1 bloc ≈ 1 mètre |
| Taille | 0,75 bloc de haut, 0,6 de large | ≈ 0,4 bloc de haut |
| Vitesse | 3 blocs/s | 2 blocs/s |
| Saut | ≈ 2,5 blocs de haut, 3 de portée | n/a |
| Portée avec planage | ≈ 5 blocs *(à tester)* | Pas de planage |
| Points de vie | 1 | 1 |
| Délai entre attaques | 0,5 s | n/a |

---

##  Gameplay

### Boucle de jeu

```
Explorer la salle → Repérer dangers et mécanismes → Choisir une stratégie
        → Utiliser ses capacités → Franchir l'obstacle → Continuer vers la sortie
                         ↑
         En cas d'échec : retour au dernier checkpoint
```

### Mécanique principale : le lasso

- **Auto-visée** : le jeu repère automatiquement la cible autorisée la plus proche, devant le poussin (portée ≈ 4 blocs, cône ≈ 60°). Pas de visée manuelle.
- **Points d'accroche** : anneaux et bras mécaniques, signalés par un indicateur **cyan**.
- **Usages** : franchir les fosses, se balancer, attaquer les robots.
- **Robot tireur** : détruit par un coup de lasso.
- **Araignée robotique** : paralysée **5 secondes** (jamais détruite).
- **Limites** : ne détruit pas le décor, ne fonctionne pas à travers un obstacle ni hors de portée.

### Mécaniques secondaires

| Mécanique | Description |
|---|---|
| **Saut et planage** | Maintenir Espace en l'air ralentit la chute et corrige légèrement la trajectoire. L'inertie est conservée, une ombre au sol aide à anticiper l'atterrissage. Pas de remontée possible. |
| **Mini-poussin** | Active leviers et boutons via les conduits. En solo, on alterne entre les deux poussins ; à deux, chacun contrôle le sien. |
| **Coup de bec** | Portée ≈ 1 bloc, uniquement sur les boutons et objets dédiés, avec retour visuel clair. |
| **Ascenseurs et mécanismes** | Activés par levier ou bouton, entrée et sortie lisibles, voyant et son d'activation. Jamais de situation bloquante. |
| **Chemins alternatifs** | Route rapide mais risquée ou détour plus sûr (10 à 25 s). Aucun choix ne bloque définitivement le joueur. |

### Règles

- **1 point de vie** : un dégât ou une chute mortelle renvoie au dernier checkpoint.
- **Essais illimités** pour encourager l'expérimentation.
- **Victoire** : atteindre la porte de sortie.
- En coopération, les deux joueurs repartent ensemble.

### Types de défis

| Type | Principe | Progression |
|---|---|---|
| Observation | Repérer mécanismes et points de lasso | Indices d'abord évidents, puis plus discrets |
| Sauts | Plateformes ou lasso | Plateformes plus petites, plus éloignées, mobiles |
| Choix | Détour sûr ou passage rapide | Risques et récompenses variés |
| Timing | Sols qui tombent, scies, araignée | Dangers lents, puis combinés |
| Ennemis | Contourner ou utiliser le décor | Un ennemi seul, puis plusieurs menaces |
| Exploration | Passages cachés | Secrets de moins en moins évidents |

---

##  Contrôles

| Action | Clavier / souris | Manette (idée) |
|---|---|---|
| Se déplacer | `Z` `Q` `S` `D` / flèches | Stick gauche |
| Sauter / planer | `Espace` (maintenir pour planer) | A / Croix |
| Coup de bec | Clic gauche | X / Carré |
| Lasso (accrocher / lâcher) | `G` | RB / R1 |
| Attaque au lasso | Clic droit | Y / Triangle |
| Interagir | `F` | B / Rond |
| Changer de poussin (solo) | `Tab` | R3 |
| Recentrer la caméra | `C` | Stick droit |
| Pause | `Échap` | Menu / Options |

Les touches seront reconfigurables. Si bec et lasso sont pressés simultanément, **le bec est prioritaire**.

---

##  Ennemis et obstacles

### Ennemis

**Araignée robotique** : ennemi de poursuite
- Grosse araignée mécanique en métal sombre, pattes articulées, pistons, tuyaux de vapeur et voyant rouge bien visible.
- Patrouille sur les murs et au plafond, poursuit 404 dans une zone dédiée, peut lancer une toile qui le ralentit ou l'immobilise (se libérer en appuyant plusieurs fois sur Espace).
- Signal d'attaque : arrêt bref, changement du voyant et bruit mécanique.
- Un coup de lasso la paralyse exactement 5 secondes, avec effets visuels et sonores au début et à la fin.

**Robot tireur arrondi** : ennemi de lecture
- Petit robot de sécurité à coque ronde, rivets, canon, œil lumineux, engrenages apparents et fuite de vapeur.
- Voyant allumé ≈ 0,6 s avant le tir, projectile en ligne droite, cadence ≈ 1,5 s *(valeurs provisoires)*.
- Peut être évité (couvert, saut, contournement) ou détruit au lasso.

### Obstacles

| Obstacle | Description |
|---|---|
| **Scies** | Fixes ou mobiles sur rail de 3 à 5 blocs, mortelles au contact et indestructibles. |
| **Zones instables** | Sols fissurés qui s'effondrent après ≈ 1 s ; plafonds qui tremblent et lâchent de la poussière avant de tomber (≈ 0,8 s d'alerte). |
| **Bras mécanique** | Oscille lentement et sert de point d'accroche pour le lasso. |

---

##  Niveau 1 : la chaîne de production

Premier niveau de 10 à 15 minutes, conçu pour introduire les mécaniques une à une.

| Zone | Contenu | Apprentissage |
|---|---|---|
| **A. Départ** | Sol plat, libération du mini-poussin, porte visible au loin | Déplacement, saut, changement de personnage, conduit et levier |
| **B. Passage bloqué** | Mécanisme d'ascenseur, détour supérieur | Coup de bec, activation de l'ascenseur |
| **C. Robot** | Plateforme avec robot tireur et petite fosse | Contourner ou attaquer au lasso |
| **D. Scie** | Fosse avec scie, bras mécanique au-dessus | Premier anneau, traversée au lasso |
| **E. Sol instable** | Couloir de blocs fissurés | Repérer les indices, agir sans trop attendre |
| **F. Checkpoint** | Plateforme sûre avec panneau lumineux | Point de reprise avant la dernière partie |
| **G. Dernière salle** | Robot tireur, araignée, route haute et basse | Combiner toutes les mécaniques |
| **H. Sortie** | Porte de livraison | Fin du niveau et courte animation humoristique |

**Chemin principal** : A → B → C → D → E → F → G → H

**Chemins optionnels** : route haute par l'ascenseur ou le bras mécanique, combat contre le robot, détour sûr autour de la scie, conduit secret avec objet à récupérer.

---

##  Direction artistique

### Pourquoi le steampunk ?

Chaudières, engrenages, tuyaux, pistons et vapeur donnent une identité forte à l'usine, au-delà d'un décor industriel moderne. Le thème sert aussi le gameplay : ascenseurs à chaînes, bras actionnés par pistons, robots aux engrenages visibles, ce qui aide à comprendre quelles machines sont dangereuses.

### Style graphique

- Personnages en **3D stylisée**, simples et expressifs.
- Usine immense, sombre et détaillée ; matériaux métal, cuivre et laiton, **sans photoréalisme**.
- Vapeur et ombres au service de l'ambiance, **sans jamais masquer** plateformes ni ennemis.
- Contraste visuel entre un poussin jaune et un décor écrasant, pour renforcer l'humour.

### Palette de couleurs

**Environnement et fond**

| Couleur | Hex | Usage |
|---|---|---|
| Gris métal | `#8B8686` | Structures, murs, surfaces métalliques |
| Beige vapeur | `#D4AF37` | Lumière principale, zones de vapeur |
| Bronze | `#6E4E2E` | Pièces mécaniques, engrenages |
| Acier | `#6B6F72` | Machines et plateformes |
| Ombre charbon | `#2B2B2B` | Zones d'ombre, profondeur, contrastes |

**Accents et gameplay**

| Couleur | Hex | Usage |
|---|---|---|
| Bleu acier | `#2F5D7C` | Éléments interactifs (leviers, points d'accroche) |
| Rouge danger | `#D64545` | Ennemis, pièges, zones mortelles |
| Orange lumière | `#F28C3B` | Alarmes, lasers, scies, effets de mouvement |
| Jaune poussin | `#FFD54F` | Joueur et points d'intérêt |
| Beige clair | `#EDE0C8` | Éléments secondaires et décoratifs |

**Règle de lisibilité** : lumière chaude réservée à la sortie, rouge-orange aux dangers, teinte froide pour les interactions.

### Inspirations visuelles

| Référence | Ce qu'on en retient |
|---|---|
| *Oddworld: Soulstorm* | Environnement industriel oppressant, cheminées, tuyaux, palette sombre |
| *Little Nightmares* | Échelle et mise en scène : un petit personnage face à un décor écrasant |
| *Shadow of the Colossus* | Effet de gigantisme face à l'environnement |
| *Ratchet & Clank: Rift Apart* | Éclairage : néons colorés et lumière chaude sur les zones importantes |
| *Stray* | Éclairage : ruelles sombres et lumière chaude guidant vers la sortie |
| *LittleBigPlanet* | Lisibilité des points d'accroche du lasso |

**Design des ennemis** : automates et araignées en laiton, machines à vapeur et chaudières rondes pour le robot tireur, mains robotiques steampunk.

---

##  Caméra

- **Caméra 3D fixe sur rails**, inspirée de *Little Nightmares* et *Oddworld: Soulstorm*.
- Suit automatiquement le poussin, sans que le joueur ait à la gérer.
- S'éloigne dans les grandes salles pour montrer dangers et chemins possibles.
- S'arrête aux limites des salles et se stabilise pendant les sauts importants.
- Se décale si un tuyau ou une machine masque le poussin, pour un rendu cinématographique.
- Recentrage manuel possible (`C`).

---

##  Ambiance sonore

**Principe général** : le son rend l'usine vivante, aide à comprendre les dangers et renforce le contraste entre un environnement inquiétant et un petit poussin attachant. Le ton reste *cartoon* (ni angoissant, ni gore).

| Pilier | Contenu |
|---|---|
| **Direction musicale** | Percussions métalliques, rouages et rythmes répétitifs ; mélodies mystérieuses en exploration ; tempo plus rapide pendant poursuites et dangers ; touches légères et absurdes pour l'humour. |
| **Bruitages** | Moteurs, engrenages, pistons, vapeur, convoyeurs ; ventilations, alarmes lointaines, métal qui grince ; piaillements, pas rapides, battements d'ailes ; lasso, rebonds, glissades, chutes. |
| **Feedback sonores** | Clic métallique ou tintement en cas de réussite ; claquement de corde puis tension au lasso ; bip ou montée inquiétante pour un danger ; son sourd ou comique en cas d'échec ; signal distinct pour la coopération. |

Chaque danger majeur dispose d'une signature sonore propre (bips du robot tireur, cliquetis de l'araignée, scies métalliques, signaux avant attaque).

---

##  Public cible

Joueurs d'environ **12 à 16 ans et plus**, amateurs de plateforme, de jeux indépendants et d'humour visuel. Les commandes restent simples tandis que l'exploration et la recherche de chemins variés apportent de la profondeur.

> **Persona : Ilies, 16 ans.** Il aime explorer, dénicher des passages cachés et tester plusieurs solutions face à un obstacle. Il préfère recommencer vite plutôt que d'être puni longtemps.

---

##  Références

| Jeu | Apport |
|---|---|
| *Super Mario Odyssey* | Déplacements |
| *Little Nightmares* | Contraste d'échelle, cadrage |
| *LittleBigPlanet* | Plusieurs façons d'aborder un passage |
| *Oddworld: Abe's Oddysee* | Usine et humour |
| *Oddworld: Soulstorm* | Caméra et lisibilité du platforming |

---

##  Faisabilité et priorités

| Priorité | Contenu |
|---|---|
| **1. Essentiel** | Déplacement, saut, lasso avec auto-visée, salles 3D, caméra automatique, collisions, mini-poussin, niveau de base, araignée robotique, une scie, checkpoint |
| **2. Important** | Mode coopératif, effondrements, robot tireur, chemin alternatif, animations, éclairage détaillé |
| **3. Bonus** | Objets cachés, variantes de parcours, effets sonores poussés |

**Plateforme** : PC sous Unity, avec clavier et manette. Diffusion envisagée plus tard sur Steam ou itch.io.

**Valeurs à valider en playtest** : portée du lasso, délais d'attaque, cadence du robot tireur, durée de paralysie, effort pour se libérer de la toile, nombre de checkpoints.

---

##  Documentation

| Document | Contenu |
|---|---|
| `GDD_Poussin_destroyer.pdf` | Game Design Document complet et fiches mécaniques |
| `Poussin_destroyer.pdf` | Dashboard de direction artistique (environnement, échelle, design, caméra, éclairage, son, palette) |

---

<p align="center"><strong>Poussin Destroyer</strong> · Plateforme 3D · Steampunk · Humour<br><em>Pitch Me A Game</em></p>