
# WIP - Work in Progress

## Data

#### Flood risk area ([ref](https://www.donneesquebec.ca/recherche/fr/dataset/grille-de-presence-de-zone-inondable-identifiee-par-les-mrc))
```
Cette grille est une représentation spatiale des secteurs où une cartographie a été produite par les municipalités régionales de comté (MRC) ou les villes à compétence de MRC. Elle indique qu’une cartographie des zones inondables a été intégrée dans le schéma d’aménagement et de développement (SAD) ou dans un règlement de contrôle intérimaire (RCI) en vigueur dans la MRC.

Cette information est fournie à titre indicatif et n’a aucune valeur légale. L'utilisateur est invité à communiquer avec les municipalités ou les MRC afin de connaitre les limites exactes des zones inondables cartographiées et la réglementation en vigueur applicable sur leur territoire.
```
- https://territoires.mamrot.gouv.qc.ca/DonneesOuvertes/DepotDonnees/grillepresencezoneinondable.json



#### Floods database ([ref](https://www.donneesquebec.ca/recherche/fr/dataset/base-de-donnees-des-zones-inondables))
```
Les données sur les zones inondables regroupent la cartographie réalisée dans le cadre du programme de cartographie de la Convention Canada-Québec de 1976 à 2001, du Programme de détermination des cotes de crues de 2001 à 2004 (PDCC), ainsi que la cartographie réalisée après cette date par le Centre d’expertise hydrique du Québec (CEH) et ses différents partenaires.
```

- ftp://ftp.mddelcc.gouv.qc.ca/DONNEES_OUVERTES/Base_donnees_zones_inondables/Bdzi_sqlite.zip

#### Spring 2019 Floods ([ref](https://www.donneesquebec.ca/recherche/fr/dataset/cartographie-des-inondations-printemps-2019))
```
Attention: les données d'étendue d'eau sont une interprétation en temps quasi réel de données satellites et n'ont pas encore été validées de manière exhaustive. Le produit peut contenir des erreurs, en particulier dans les zones urbaines.

Liste des données disponibles :

le suivi des événements d’inondation et de glissement de terrain depuis le 14 avril 2019 en points géolocalisés (service web et téléchargement),
les limites d’étendue des eaux libres générées par Ressources naturelles Canada, dérivées des données satellitaires Radarsat 2 ou d'autres satellites radar et celles générées par Dromadaire Géo-Innovations, dérivées des données satellitaires Sentinel (service web et téléchargement),
des images satellitaires dans le visible et proche infrarouge sur les zones les plus gravement touchées (service web et téléchargement lorsque possible).
Toutes les données sont aussi consultables sur une carte interactive basée sur IGO2.

Note:

Les acquisitions satellites de Radarsat-2 sont planifiées en collaboration avec Ressources naturelles Canada. L’accès à des satellites radars d’autres agences spatiales canadiennes est possible grâce à l’activation de la Charte internationale espace et catastrophe majeure. Celle-ci est activée par Sécurité publique Canada. Les images obtenues via la charte internationale sont traitées par les services géomatiques d’urgence de Ressources naturelles Canada dans les meilleurs délais puis les polygones d'étendue d'eau libre sont diffusés en données ouvertes sur Données Canada et sur Données Québec. D’autres acquisitions optiques ou radars peuvent avoir été obtenues par le ministère de la Sécurité publique (MSP) de fournisseurs privés. Les acquisitions Sentinel-1 et Sentinel-2 diffusées en données ouvertes par l’agence spatiale européenne (ASE) ont été traitées par la firme Dromadaire-Geo-Innovations. 
```

- https://geoegl.msp.gouv.qc.ca/partageDQ/inondations2019/msp_inondations2019_eaulibre_20190425.zip

#### Microsfot Building ([ref](https://github.com/Microsoft/CanadianBuildingFootprints))

- https://usbuildingdata.blob.core.windows.net/canadian-buildings/Quebec.zip


## Create PostGIS db

```
$ docker-compose up -d
```


### Load data to PG

```bash
# Load buildings
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/Quebec.geojson"

# Load Flood data
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/grillepresencezoneinondable.geojson"

# Load Flood data
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/msp_inondations2019_eaulibre_20190425/msp_inondations2019_eaulibre.shp"

$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/Bdzi.sqlite"
```


### Process

##### Create building centroids
```sql
DROP TABLE IF EXISTS buildings_centroid ;
CREATE TABLE buildings_centroid
AS
SELECT
	quebec.ogc_fid, st_centroid(quebec.geom) as geom
FROM
	quebec
```

##### Find buildings in flood area
```sql
DROP TABLE IF EXISTS buildings_in_floodarea ;
CREATE TABLE buildings_in_floodarea
AS
SELECT
	centroids.*
FROM
	buildings_centroid centroids,
	grillepresencezoneinondable flood_risk
WHERE
	   ST_Within(centroids.geom, flood_risk.geom)
```

```sql
SELECT count(*) FROM buildings_in_floodarea
108 721
```