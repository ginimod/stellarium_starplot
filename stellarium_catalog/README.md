# Des Catalogues StarPlot pour Stellarium

Le catalogue de DSO et d'étoiles de Stellarium pour la librairie [Starplot](https://starplot.dev)

### Contexte

Je travaille sur GrapheStellar, un projet personnel de documentation des cultures stellaires américaines, et j'utilise pour l'instant Stellarium () comme source primaire de données et [Starplot](https://starplot.dev) pour le tracé des cartes.

Ces deux catalogues me permettent de réduire la taille et le nombre de mes dépendances.

Catalogues génériques
- hyg-v4.2.parquet (7.2 Mo)
- stars.bigksy.0.1.3.mag9.parquet (8 Mo)
- ongc.0.1.2.parquet (15 Mo)

Catalogue Stellarium  
- stellarium-star-v0.1.parquet (262  Ko)
- stellarium-dso-v0.1.parquet  (45.3 Ko)

### Data
- Source :  **[stellarium-skycultures](https://github.com/Stellarium/stellarium-skycultures)**
- Skycultures : **39**
- liste : anutan,arabic_alsufi,arabic_ancient,arabic_arabian_peninsula,arabic_lunar_stations,aztec,belarusian,blackfoot,boorong,bugis,chinese,chinese_contemporary,egyptian,hawaiian_starlines,indian,inuit,japanese_moon_stations,kamilaroi,korean,lokono,macedonian,mandar,maori,mongolian,navajo,norse,northern_andes,romanian,ruelle,sami,sardinian,siberian,tongan,tukano,tupi,western,western_hlad,western_rey,western_SnT

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
 

