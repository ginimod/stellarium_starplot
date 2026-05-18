# Des Catalogues StarPlot pour Stellarium

Le catalogue de DSO et d'étoiles de Stellarium pour la librairie [Starplot](https://starplot.dev)

### Context

I'm working on GrapheStellar, a personal project showcasing American skycultures, currently using Stellarium as my primary data source. I generate the maps with Starplot.


### Data
- Source :  **[stellarium-skycultures](https://github.com/Stellarium/stellarium-skycultures)**
- Skycultures : **39**
- liste : anutan,arabic_al-sufi,arabic_ancient,arabic_arabian_peninsula,arabic_lunar_stations,aztec,belarusian,blackfoot,boorong,bugis,chinese,chinese_contemporary,egyptian,hawaiian_starlines,indian,inuit,japanese_moon_stations,kamilaroi,korean,lokono,macedonian,mandar,maori,mongolian,navajo,norse,northern_andes,romanian,ruelle,sami,sardinian,siberian,tongan,tukano,tupi,western,western_hlad,western_rey,western_SnT

### Process
- Date du scan : **17/05/2026**
- Catalogue Star : **3722**  manquante **hip115125 (94 Aquarii)**
- Catalogue DSO :  **18**

### Usage
Avec la librairie StarPlot

```python
    stellarium_star = Catalog("stellarium-star-v0.1.parquet")
    stellarium_dso = Catalog("stellarium-dso-v0.1.parquet")

    hip = 32349 # Sirius ok
    print(f"Test hip{hip} => ", Star.get(hip=hip, catalog = stellarium_star) )

    hip = 115125  #94 Aquarii -> manquante
    print(f"Test hip{hip} => ", Star.get(hip=hip, catalog = stellarium_star) )

    name="NGC0884" # chi Persei Cluster
    print(f"Test DSO {name} =>", DSO.get(name=name,catalog=stellarium_dso))
```
### Todo

 - Régler le pb **hip115125 (94 Aquarii)** impact pour chinese,chinese_contemporary,korean
 

