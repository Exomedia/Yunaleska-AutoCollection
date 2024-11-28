# Live demo
[exomedia.io](https://exomedia.io/Yunaleska-AutoCollection/)

# Automatisation
## QoL
Fonction pour modifier la taille du texte en fonction de sa longueur, les noms des jeux devraient rester sur une ligne sans faire de cas par cas
```js
function adjustFontSizes() {
    document.querySelectorAll('.game-name').forEach(element => {
        const length = element.textContent.length;
        element.style.fontSize = length > 20 ? '12px' : length > 15 ? '13px' : length > 10 ? '14px' : '15px';
    });
}
```

## Index
- Liste les jeux en cours via index_games.json
- Cherche automatiquement le nom du jeu dans le fichier json de la plateforme pour récupérer les images, achievements, etc...
```json
[
    {
        "name": "Tomb Raider II Remastered",
        "platform": "ps4"
    },
    {
        "name": "Final Fantasy VII Remake",
        "platform": "ps5"
    },
    {
        "name": "Lies of P",
        "platform": "steam"
    }
]
```

## Nintendo
- Rempli automatiquement le nombre de jeux possédés
- Créé les entrées des jeux DS et Switch dans leurs collections respectives
- ds_data.json
```json
  {
      "img_src": "https://m.media-amazon.com/images/I/818MNsl62QL._AC_SL1500_.jpg",
      "name": "Pokémon Ultra-Lune",
      "completions": [
          "8 Badges / 8 Badges",
          "Pokédex incomplet"
      ]
  }
```
- switch_data.json
```json
  {
      "img_src": "https://cdn.cultura.com/cdn-cgi/image/width=1024/media/pim/pokemon-epee-0045496424763_0.jpg",
      "name": "Pokémon Epée",
      "completions": [
          "Histoire et pokédex complétés",
          "125h+ jouées"
      ]
  }
```

## Playstation
- Unification du CSS pour les trois pages HTML : games-ps.css
- Calcul automatique des trophées : Base + DLC
- Barre de complétion dynamique en fonction du pourcentage
- Nombre de trophés acquis / Nombre de trophés totaux
- N'affiche le texte "DLC + liste des trophées" que s'il y a au moins un trophée disponible
```json
  {
      "img_src": "alice-madness-returns.png",
      "name": "Alice Madness Returns",
      "bronze_trophies": "30/30",
      "silver_trophies": "12/12",
      "gold_trophies": "2/2",
      "date_platined": "01/09/2015",
      "bronze_trophies_dlc": "0/4",
      "silver_trophies_dlc": "0/1",
      "gold_trophies_dlc": "0/1"
  }
```

## Steam
- Calcul du nombre de jeux possédés
- Calcul des jeux complétés à 100%
- Barre de complétion dynamique en fonction du pourcentage
- Nombre de succès acquis / Nombre de succès totaux
```json
  {
      "img_src": "borderlands-3.jpg",
      "name": "Borderlands 3",
      "amount_achievement": "62/81"
  }
```

## Wishlist
- Créé les entrées dans les sections Playstation et Steam, message alternatif en cas de fichier {plateforme}_wishlist.json vide
```json
  {
      "name": "Voice of Cards Trilogy",
      "platform": "ps4",
      "img_src": "voice-of-cards-trilogy.png",
      "text": "Platine disponible : Oui\n\t\t\t\t\t\t\t\tPriorité : Haute"
  },
  {
      "name": "Assassin's Creed Ezio Collection",
      "platform": "ps5",
      "img_src": "assassins-creed-ezio-collection.png",
      "text": "Platine disponible : Oui\n\t\t\t\t\t\t\t\tPriorité : Haute"
  }
```

# Non pris en charge
- Jeux Nintendo dans les jeux en cours de l'index.html
- CSS unifié sur la page wish-list.html
- Jeux Nintendo dans la wishlist
