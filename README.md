# stellarium_starplot
Mapping entre les références DSO dans stellarium et la librairie StarPlot

### Context
I'm working on GrapheStellar, a personal project showcasing American skycultures, currently using Stellarium as my primary data source. I generate the maps with Starplot.

[Exmple Lokono](https://www.inimod.org/graphestellar_0.5/lokono/map.html)

### Need
I now want to add named objects such as DSO, and Comet, Planet, Moon, Sun in Zénithal 

### Pb 
In the Stellarium source files, this is the **common_names** attribute.
The following example, Anutan, although Oceanic, illustrates my problem.
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

- a mix of HIP and NAME to designate the stars
- NAME inconsistent with Open NGC and StarPlot search

I scanned the 39 JSON files in the skycultures directory, I excluded the keys with HIP in the common_names attribute. So I'm left with the **exotic keys**.

### Proposal : 
I propose to work on a mapping file of the following form:
 key : Stellarium (or a slug)
 Val :  The Starplot **object type**_**object id**
          spe for special sun,moon,milkyway
My need is for a plotting
```json
{
  "NAME Milky Way": "spe_milkyay",
  "NAME Sun":  "spe_Sun",
  "NAME Moon":  "spe_Moon",

  "NAME Mercury":  "planet_Mercury",
  "NAME Venus":  "planet_Venus",
  "NAME Mars":  "planet_Mars",  
  "NAME Jupiter":  "planet_Jupiter",
  "NAME Saturn":  "planet_Saturn",
  
  "C 99": "comet_id",    
  "C 76":  "comet_id",
  "C 41": "comet_id",
  
  "NAME Orion Nebula":"dso_id",
  "NAME Carina Nebula": "dso_id",  
  "NGC 869":  "dso_id",  
  "NAME ω Cen Cluster": "dso_id",
  "NAME Large Magellanic Cloud":"dso_id",
  "NAME Pleiades": "dso_id",
  "NAME Small Magellanic Cloud": "dso_id",
  "NAME Coalsack Nebula":  "dso_id",
  "NAME Andromeda Galaxy": "dso_id",
  "NGC 292": "dso_id",
  "NAME Beehive Cluster": "dso_id",
  "NGC 884": "dso_id",
  "M 44": "dso_id",
  "M 45": "dso_id",
  "M 7":  "dso_id",

  "NAME Antares": "star_hip",
  "NAME Procyon":  "star_hip",
  "NAME Sirius":  "star_hip",
  "NAME Canopus": "star_hip"
    
}
```

I would appreciate some feedback and comments _avant de plonger dans un terrier de lapin..._
