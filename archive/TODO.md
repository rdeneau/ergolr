- Base : [Ergo-L](https://ergol.org/) : layout de clavier adapté à clavier 4x60 Sofle
  - Même principe de touche morte pour accéder aux caractères accentués ou spéciaux
  - Variations :
    - [C] entre [X] et [V] comme en AZERTY et QWERTY
    - [B] remplace [C] entre [Q] et [O]
    - [,/;] remplace le [B], en symétrie du [./:]
    - [-/_] : nouvelle combinaison de caractères qui remplace [,/;] entre [G] et [K]
    - [?/!] : nouvelle combinaison de caractères qui remplace [Enter] à droite du [U]
  - Les symboles associés aux chiffres sont aussi modifiés
    - [$] sur [1] au lieu du [4]
    - [€] sur [2] au lieu de [1]
    - ["] sur [3] et ['] sur [4] (iso AZERTY) à la place de [«] et [»], eux mis en 1dk sur cette ligne, à gauche et sur ["]
    - [(] et [)] en [5] et [6], [&] et [^] sont accessibles uniquement dans la couche "Symbol"
    - [@] sur [7] plutôt que [9]
    - [#] sur [8] - caractère que j'utilise beaucoup, citant mes langages de programmation principaux, C# et F#
    - [/] sur [9] - mais je ne m'en sert jamais ; je préfère le taper depuis la couche "Symbol", avec [\] juste en dessous
    - [=/=] en bout de ligne, comme sur un clavier AZERTY
  - La couche 1dk contient moins de caractères accentués - que ceux français - pour avoir plus de caractères spéciaux, dont des émojis
    - J'ai mis ceux les plus courants directement sur la touche de voyelles (à é î û) et les autres à droite ou à gauche, selon la place, sauf le [æ] au dessus.
    - Même principe de similarité pour placer les caractères spéciaux :
      - les guillemets (vu avant),
      - l'apostrophe [’]
      - [°] rappelant [%]
      - [§] (symbol du paragraphe) est sur [P]
      - [TAB] (le caractère) sur [TAB] (la touche)

---

A changer :

- C1; [Ctrl] en bas, sous [Shift] comme en AZERTY ; double tap [Shift] = [CapsLock]
- Pas de besoin de [Nav] ni [AltGr]
- [Alt] à gauche est pratique
- [Win] à droite; plus de touche [Prop] qui devient 1dk Win
- TailorKey pour la suite de la ligne du pouce
  - G: Alt, Left, Right, Del, Backspace (hold declenche Cursor)
  - D: Space (hold de:clenche Symbol), Enter, Up, Down, Win
- C6 : =/+ */µ ?/! PrintScreen (hold double-tap declenche Nav/Lower/keypad)

---

## Vial

### Tap dances

- TD0, TD1, TD2, TD5..TD9 servent aux touches de la ligne des chiffres
- TD3  = ,/;
- TD4  = ./:
- TD10 = -/_

---

- J'ai modifié légèrement la couche Symbol - cf. ergolrl-v11.vil. Par contre `` et ``` ne marchaient pas - je les ai enlevés - je te laisse les supprimer du code.
- Le RGB sous les touches ne marchent que sur les couches 0 et 1, mais pas sur les couches 2, 3, 4. On va uniformiser et utiliser la touche Esc pour indiquer la couche active.
  - Couche 0 Base   : supprimer le RGB des touches du pouce - déplacer le RGB orange vers la touche PrtScr.
  - Couche 1 NavNum : idem couche 1 + Orange sur Esc
  - Couche 2 Symbol : idem couche 1 + Bleu   sur Esc
  - Couche 3 1dk    : idem couche 1 + Rouge  sur Esc
  - Couche 3 Emoji  : idem couche 1 + Violet sur Esc
- Ajouter un README.md dans C:\Dev\_github\rdeneau\ergolr\ pour expliquer ce layout ;
  - ses inspirations (Ergo-L, TailorKey), ses spécificités et les raisons associées (par exemples revenir vers le AZERTY parfois : XCV, =/=, ...), ses couches.
  - Montrer les parallèles entre les couches entre touche, comme les flèches, Enter, Space et leur caractères associés en 1dk
  - Le Shift et l'AutoShift, marchant sur toutes les touches concernées (A-Z yc accents, 1dk).
  - Le hold (MO) et double tap (TG) supportés pour les couches 1 et 2.
  - Les différentes versions de ErgoLR :
    - Le 1er sur le Sofle devait avoir un clavier créé par Kalamine et à installer sur le poste Windows
    - Le 2em sur le Glove80 avec le script AHK pour gérer certains caractères spéciaux et les emojis
    - Le 3em de nouveau Sofle, nécessitant seulement WinCompose
  - Pointe vers le path du code du repo vial-qmk-keebart (mon fork sur github.com/rdeneau).
  - Copie C:\Dev\_github\kalamine\layouts\ergolr-rde.svg (image multi-couches d'une vieille version) dans dans ce repo en deux copies. Met les à jour :
    - 1ere copie concernant les couches 0, 1, 2, 3. Déplace les fonds de couleurs sur les bonnes touches (Bleu => Symbol => Space, Orange => NavNum => PrtScr). Voici ce que cela donnait pour le Glove80 fait àla main avec Google Slides : ![Glove80](2026-09-14_03h20_20.png)
    - 2e copie pour la couche Emoji
- Committe cela dans chaque repo

- ergolr-layers.svg
  - Pour les lettres, retirer les minuscules non accentuées et les majuscules accentuées - exemple :
    ```
    [ Q    ]
    [   à  ]
    [ Redo ]
    ```
  - Pour les touches [,] et [.], ono ne voit pas bien les ";" et ":" => mettre à la même taille que "," et "." et en gras aussi
  - Erreur : dans la derniere colonne, 3e ligne, ce n'est pas Bspc mais ? / !
  - Renommer "Bspc" en "Backspc"
  - Pour les flèches sur les touches du pouce:
    - Pour la couche BASE, indiquer le nom de la flèche (ex : Left, Right, Up, Down) pour ne pas faire doublon avec le caractère typo (← → ...)
    - Couche 1dk : comme sur les touches des lettres :
      - aligner à droite de la touche
      - mettre sur la ligne du dessus la version grasse de la flèche (⇐ ⇒ ...)
  - Au centre, au-dessus des 2 cases carrées, indiquer l'action des rotary encoders :
    - Titre centré, dépendant de la couche
      - Couche Base: "Cursor"
      - Couche NavNum: "Scroll"
    - Entre ce titre et les touches [Space] [Enter], 2 cercles de même diamètre qu'une touche
      - Cercle à gauche : "⮟ Up / Down ⮝"
      - Cercle à droite : "⮟ Left / Right ⮝"²
- ergolr-emoji.svg
  - Dans le coin haut gauche des touches
    - Sur la 1ère ligne, mettre les chiffres plutot ($ => 1, € => 2, ...)
    - Les lettres sont en majuscules
    - Les emojis sont trop bas => les centrer verticalement.
    - Mettre sous les emojis leur nom - ex : Q => Question, B => Bug, O => Ok, ... - cf. "C:\Dev\_github\rdeneau\ergolr\ergol-r_moergo.json"

---

- J'ai modifié les SVG pour améliorer le rendu et aussi correspondre à des modifs faites avec Vial - cf. "C:\Dev\_github\rdeneau\ergolr\ergolrl-v12.vil"
- ergolr-layers.svg
  - NBSP devrait être en vert. Or il est blanc actuellement
- En dernière colonne, 3e ligne, la touche est ?/!, pas [Backspace]
- AutoShift ne marche pas avec les autres modifiers [Ctrl], [Win], …
  - [Ctrl]+Hold[P] devrait faire [Ctrl]+[Shift]+[P]
  - [Win]+Hold[,] devrait faire apparaître l'emoji picker
- Mettre en place Double-tap [Shift] ⇒ [CapsLock], tap again => unlock caps.
- Les caractères ^ et ~ dans la couche symbol nécessite aussi un tap Space pour les saisir ⇒ corriger pour que un seul tap suffise. Puis l'indiquer dans le § "The backtick" dans le README.md
- A la place de `\\`, placer `°` avec `0` ; du coup, mettre `‰` en 1dk de `% 5` (comme ergo-l)
- Ajouter `¶` en 1dk sur le W (à droite de P §)
- Dans la 1dk, déplacer `÷` de `0` à `D` (comme "divide") et `±` de 1dk shifté vers `0`
- Couche Emojis :
  - remettre les Keycaps 1️⃣ 2️⃣ 3️⃣ 4️⃣ 5️⃣ 6️⃣ 7️⃣ 8️⃣ 9️⃣ 0️⃣
  - définir ➖ Minus  pour la touche [- _ ]
  - définir ➕ Plus pour la touche [= +]
  - définir *️⃣ Asterisk pour la touche [\* µ]
  - définir ⭐ Star pour la touche 1dk
  - définir ◀️ pour la touche [Alt] (thumb)
  - définir ▶️ pour la touche [Del] (thumb)
  - définir 🚢 Ship pour la touche [Space] (thumb)
  - définir 🧹 Broom pour la touche [Backspace] (thumb)
- Améliorer le README.md:
  - Citer les touches chacune dans une balise KBD - j'ai commencé à le faire en fin de document.
  - Corriger "sit directly on their vowel (`à é î û`); the rest go left or right of it, wherever there is room — `æ` above `à` being the exception" : c'est désormais faux pour le A (â above to preserve Shift, æ on F after the E-s)
  - Citer la relation entre `#` et `♯` (sharp en 1dk)

---

- "literal Tab character" ne marche pas dans vscode : pas de diff avec la touche [TAB]
- RGB
  - la Touche allumée en vert du CapsLock doit être [Shift] au lieu de [Ctrl]
  - la Touche 1dk doit être en violet (au lieu du rouge) sur la couche 1dk
- README.md
  - expliquer la logique de placement des symboles - cela permet de saisir aisément les flèches fines `->` et grasses `=>` (pour les lambdas en F# et C#), l'opérateur pipe `|>` (utilisé en F#), … – cf. Sunaku's Symbol Layer https://sunaku.github.io/moergo-glove80-keyboard.html#symbol-layer
  - WinCompose marche mieux que mon Script AHK qui avait des râtés parfois (affichage du code, au lieu du char)