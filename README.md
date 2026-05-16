# stellarium_starplot
Mapping entre les références *common_names* dans Stellarium et la librairie [Starplot](https://starplot.dev)

### Context

I'm working on GrapheStellar, a personal project showcasing American skycultures, currently using Stellarium as my primary data source. I generate the maps with Starplot.

[Exemple Lokono](https://www.inimod.org/graphestellar_0.5/lokono/map.html)

### Besoin

Pouvoir ajouter les objets nommés sur les cartes avec [Starplot](https://starplot.dev) : DSO,Planet, Moon, Sun  

### Problème 
Dans le format de définition Json d'une SkyCulture l'attribut **common_names**.

L'exemple de la culture Anutan illustre parfaitement mon problème.
- un mixe entre HIP and NAME pour désigner des étoiles
- NAME inconsistant pour la recherche DSO.get(name=) de StarPlot (Open NGC)

```json
  "common_names": {
    "NAME Sirius": [{"english": "The Bird's Body", "native": "Te Tino A Manu"}],
    "NAME Canopus": [{"english": "The East Wing", "native": "Te Kapakau Tonga"}],
    "NAME Procyon": [{"english": "The North Wing", "native": "Te Kapakau Pakatokerau"}],
    "NAME Antares": [{"english": "Its Stem", "native": "Na Kau"}],
    "HIP 32607": [{"english": "The East Wing's Precursor", "native": "Te Taki O Te Kapakau Tonga"}],
    "HIP 677": [{"english": "Middle Precursor", "native": "Taki Roto", "description": "It is uncertain whether this star name is attached to this or a neighbouring star in the Square of Pegasus."}],
    "NAME Pleiades": [{"english": "Small Face", "native": "Matariki"}],
    "NAME Milky Way": [{"native": "Te Tukaniva"}],
    "NAME Large Magellanic Cloud": [{"english": "The Running Cloud", "native": "Te Ao Rere"}],
    "NAME Small Magellanic Cloud": [{"english": "The Restrained Cloud", "native": "Te Ao Toka", "description": "The English gloss is marked uncertain."}],
    "NAME Venus": [{"english": "The Morning Star", "native": "Te Petuu Ao"}, {"english": "The Evening Star", "native": "Tiuriuri"}]
  }
```
[Source](https://github.com/Stellarium/stellarium-skycultures/blob/master/anutan/index.json)

### Solution : 

J'ai scannée (14/05/2026), le répertoire [stellarium-skycultures](https://github.com/Stellarium/stellarium-skycultures), j'ai compilé les **common_names** en réjectant les HIP, il reste donc les **Clefs exotiques**.

J'ai créé un fichier de Mapping en m'appuyant sur les trois sources citées en références.

```json
{
  "comment_1" : " Specifique à StarPlot , bypass milkyay,  starplot.Sun, starplot.Moon ", 
  "NAME Milky Way": "spe_milkyay",
  "NAME Sun":  "spe_sun",
  "NAME Moon":  "spe_moon",
  
  "comment_2" : "  straplot.Planet.get(name='Mercury')",    
  "NAME Mercury":  "planet_Mercury",
  "NAME Venus":  "planet_Venus",
  "NAME Mars":  "planet_Mars",
  "NAME Jupiter":  "planet_Jupiter",
  "NAME Saturn":  "planet_Saturn",

  
  "comment_3" : " Star Plot starplot.DSO.get(name='C099') ",
  "C 99": "dso_C099",
  "C 76":  "dso_NGC6231",
  "C 41": "dso_C041",
  "M 44": "dso_NGC2632",
  "M 45": "dso_Orion",
  "M 7":  "dso_NGC6475",
  "NGC 292": "dso_NGC292",
  "NGC 869":  "dso_IC0869",
  "NGC 884": "dso_NGC884",
  "NAME Orion Nebula":"dso_Orion",
  "NAME Carina Nebula": "dso_NGC3372",
  "NAME ω Cen Cluster": "dso_NGC5139",
  "NAME Large Magellanic Cloud":"dso_ESO056-115",
  "NAME Pleiades": "dso_Mel022",
  "NAME Small Magellanic Cloud": "dso_NGC0292",
  "NAME Coalsack Nebula":  "dso_C099",
  "NAME Andromeda Galaxy": "dso_NGC0224",
  "NAME Beehive Cluster": "dso_NGC2632",

  "comment_4":" starplot.Star.get(hip=80763) ",
  "NAME Antares": "star_80763",
  "NAME Procyon":  "star_37279",
  "NAME Sirius":  "star_32349",
  "NAME Canopus": "star_30438"
    
}
```

# Références 

**Caldwell -> NGC**
[http://www.messier.seds.org/xtra/similar/caldwell.html](http://www.messier.seds.org/xtra/similar/caldwell.html)
  
**Messier  -> NGC**
[https://www.rasc.ca/sites/default/files/messier.pdf](https://www.rasc.ca/sites/default/files/messier.pdf)

**StarPlot**
[https://starplot.dev/object-names/dsos](https://starplot.dev/object-names/dsos)
