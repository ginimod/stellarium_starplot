# stellarium_starplot
Mapping entre les références DSO dans stellarium et la librairie StarPlot

Dans Stellarium SkyCulture les références au DSo utiliseent la dénomination de Messier dans la v0.1 et un mixte NGC dans la 0.2

**cas de la culture Inuit model 0.1**
```json
  "common_names": {
    "M42":       [{"english": "Group of children", "native": "Qangimmaariik"}],
    "M45":       [{"english": "Breastbone", "native": "Sakiattiak"}]
  }
```
[source](https://github.com/ginimod/stellarium-skycultures/blob/master/inuit/index.json)

**cas de la culture Inuit model 0.2**
```json
 "common_names":{
   "NAME Orion Nebula": [{"english": "Nephews or Nieces","native": "Qangimmaariik","description": "A group of children"} ]
   }
```
[source](https://github.com/ginimod/stellarium-skycultures/blob/master/inuit/index_v2.json)

*on note la disparition de M45 (Pléiades au passage mais ça c'est un autre problème*
