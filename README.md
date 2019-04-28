
# 2019 Spring flood in Quebec


Sample of geospatial analysis from opendata on the 2019 spring floods in Quebec.

![](https://user-images.githubusercontent.com/10407788/56869292-f3709f80-69cc-11e9-982d-a3e0367dcfe3.jpg)

![](https://user-images.githubusercontent.com/10407788/56869645-e0f86500-69d0-11e9-8dcd-32d1130b0cf5.jpg)

## Mapbox Map: 

**QuebecFlood2019** : https://api.mapbox.com/styles/v1/vincentsarago/cjv17uopy9knc1ftlq5c71jnc.html?fresh=true&title=true&access_token=pk.eyJ1IjoidmluY2VudHNhcmFnbyIsImEiOiJjamxwa3JkaWkwZ3BjM3dudmZmazQwYjI2In0.eUzks_hqH-QVIlnXUKmKsA#13.53/45.60849/-73.84227

**QuebecFlood2019Satellite** : https://api.mapbox.com/styles/v1/vincentsarago/cjv1cxdbr3f0w1fo77847qepn.html?fresh=true&title=true&access_token=pk.eyJ1IjoidmluY2VudHNhcmFnbyIsImEiOiJjamxwa3JkaWkwZ3BjM3dudmZmazQwYjI2In0.eUzks_hqH-QVIlnXUKmKsA#18.6/45.518067/-73.854696/0

## Data

#### Quebec - Multirisk Event flux (point)

> La carte de Vigilance multirisque est un produit développé par le ministère de la Sécurité publique (MSP) qui regroupe des avertissements et des signalements sur des phénomènes, d’origine naturelle pouvant avoir des conséquences sur la sécurité des citoyens, des biens et des services à la population. Elle est mise à jour en continu de façon automatique. Elle permet d’effectuer une surveillance en continu du territoire de la province relativement aux phénomènes naturels dangereux.

- https://geoegl.msp.gouv.qc.ca/ws/igo_gouvouvert.fcgi?service=wfs&version=1.1.0&request=getfeature&typename=msp_vigilance_crue_publique_v_type&outputformat=geojson

#### Flood risk area ([ref](https://www.donneesquebec.ca/recherche/fr/dataset/grille-de-presence-de-zone-inondable-identifiee-par-les-mrc))

> Cette grille est une représentation spatiale des secteurs où une cartographie a été produite par les municipalités régionales de comté (MRC) ou les villes à compétence de MRC. Elle indique qu’une cartographie des zones inondables a été intégrée dans le schéma d’aménagement et de développement (SAD) ou dans un règlement de contrôle intérimaire (RCI) en vigueur dans la MRC.
> Cette information est fournie à titre indicatif et n’a aucune valeur légale. L'utilisateur est invité à communiquer avec les municipalités ou les MRC afin de connaitre les limites exactes des zones inondables cartographiées et la réglementation en vigueur applicable sur leur territoire.

- https://territoires.mamrot.gouv.qc.ca/DonneesOuvertes/DepotDonnees/grillepresencezoneinondable.json

#### Floods database ([ref](https://www.donneesquebec.ca/recherche/fr/dataset/base-de-donnees-des-zones-inondables))

> Les données sur les zones inondables regroupent la cartographie réalisée dans le cadre du programme de cartographie de la Convention Canada-Québec de 1976 à 2001, du Programme de détermination des cotes de crues de 2001 à 2004 (PDCC), ainsi que la cartographie réalisée après cette date par le Centre d’expertise hydrique du Québec (CEH) et ses différents partenaires.

- ftp://ftp.mddelcc.gouv.qc.ca/DONNEES_OUVERTES/Base_donnees_zones_inondables/Bdzi_sqlite.zip

#### Spring 2019 Floods ([ref](https://www.donneesquebec.ca/recherche/fr/dataset/cartographie-des-inondations-printemps-2019)) - Updated Daily

> Attention: les données d'étendue d'eau sont une interprétation en temps quasi réel de données satellites et n'ont pas encore été validées de manière exhaustive. Le produit peut contenir des erreurs, en particulier dans les zones urbaines.

> Liste des données disponibles :
> - le suivi des événements d’inondation et de glissement de terrain depuis le 14 avril 2019 en points géolocalisés (service web et téléchargement),
> - les limites d’étendue des eaux libres générées par Ressources naturelles Canada, dérivées des données satellitaires Radarsat 2 ou d'autres satellites radar et celles générées par Dromadaire Géo-Innovations, dérivées des données satellitaires Sentinel (service web et téléchargement),
des images satellitaires dans le visible et proche infrarouge sur les zones les plus gravement touchées (service web et téléchargement lorsque possible).
> - Toutes les données sont aussi consultables sur une carte interactive basée sur IGO2.

> Note:

> Les acquisitions satellites de Radarsat-2 sont planifiées en collaboration avec Ressources naturelles Canada. L’accès à des satellites radars d’autres agences spatiales canadiennes est possible grâce à l’activation de la Charte internationale espace et catastrophe majeure. Celle-ci est activée par Sécurité publique Canada. Les images obtenues via la charte internationale sont traitées par les services géomatiques d’urgence de Ressources naturelles Canada dans les meilleurs délais puis les polygones d'étendue d'eau libre sont diffusés en données ouvertes sur Données Canada et sur Données Québec. D’autres acquisitions optiques ou radars peuvent avoir été obtenues par le ministère de la Sécurité publique (MSP) de fournisseurs privés. Les acquisitions Sentinel-1 et Sentinel-2 diffusées en données ouvertes par l’agence spatiale européenne (ASE) ont été traitées par la firme Dromadaire-Geo-Innovations.

- https://geoegl.msp.gouv.qc.ca/partageDQ/inondations2019/msp_inondations2019_eaulibre_20190427_1600.zip

#### Waterbody map of Quebec (2010) ([ref](https://mern.gouv.qc.ca/territoire/portrait/portrait-donnees-mille.jsp))

> Cette base de données couvre l’ensemble du Québec à l’échelle de 1/1 000 000. Elle a été obtenue par la généralisation des éléments de la base de données à l’échelle de 1/250 000 produite par le Ministère. Son contenu permet une représentation du territoire à des échelles variant de 1/1 000 000 à 1/2 500 000. Des jeux de données en format vectoriel et matriciel sont offerts.

- https://mern.gouv.qc.ca/publications/territoire/portrait/1M/hydro_s.zip

#### Microsoft Buildings ([ref](https://github.com/Microsoft/CanadianBuildingFootprints)) ([mbtiles](https://s3.amazonaws.com/opendata.remotepixel.ca/ms_buildings/quebec_buildings.mbtiles))

- https://usbuildingdata.blob.core.windows.net/canadian-buildings/Quebec.zip 


#### CAN - Open Database of Buildings ([ref](https://www.statcan.gc.ca/eng/open-building-data/open-database)) ([mbtiles](https://s3.amazonaws.com/opendata.remotepixel.ca/odb/odb_quebec_buildings.mbtiles))

> The inputs for the ODB are datasets provided by municipal, regional or provincial sources available to the general public through open government portals under various types of open data licenses. The current version of the database (version 2.0) contains approximately 4.4 million records and includes provinces and territories where open building footprints were found during the collection period (from January to August 2018 for version 1.0, and February 2019 for additions made in version 2.0).

- https://www.statcan.gc.ca/sites/default/files/upload/media/ODB_v2_Quebec.zip

## Create PostGIS db

```
$ docker-compose up -d
```


### Load data to PG

```bash
# Load Flood Risk data
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/grillepresencezoneinondable.json"

# Load 2019 Spring Flood data
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/msp_inondations2019_eaulibre_20190425/msp_inondations2019_eaulibre.shp"

# Load Flood db data
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/Bdzi.sqlite"

# Load Water body data
$ fio cat data/hydro_s/hydro_s.shp | jq -c 'select(.properties.HYS_DE_IND=="Lac")' | fio collect > data/hydro_s/hydro_s.geojson

$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/hydro_s/hydro_s.geojson"

# Load MS buildings
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/Quebec.geojson"

# CAN - QC Buildings
$ ogr2ogr -nlt PROMOTE_TO_MULTI -lco GEOMETRY_NAME=geom -t_srs EPSG:4326 -f PostgreSQL PG:"dbname='postgres' host='localhost' port='5432' user='postgres' password='mysecretpassword'" "data/ODB_Quebec/odb_quebec.shp"
```

### Pre-Processing

http://blog.cleverelephant.ca/2018/09/postgis-external-storage.html

```sql
-- Change the storage type
ALTER TABLE msp_inondations2019_eaulibre
  ALTER COLUMN geom
  SET STORAGE EXTERNAL;
  
-- Force the column to rewrite
UPDATE msp_inondations2019_eaulibre
  SET geom = ST_SetSRID(geom, 4326);
```

```sql
-- Change the storage type
ALTER TABLE quebec
  ALTER COLUMN geom
  SET STORAGE EXTERNAL;

-- Force the column to rewrite
UPDATE quebec
  SET geom = ST_SetSRID(geom, 4326);
```

### Processing

### Find buildings inpacted by the 2019 spring flood (27/04/2019)
```sql
DROP TABLE IF EXISTS buildings_impacted ;
CREATE TABLE buildings_impacted
AS
SELECT
	buildings.*
FROM
	quebec buildings,
	msp_inondations2019_eaulibre flooded_area
WHERE
	st_intersects(buildings.geom, flooded_area.geom)
```

```sql
SELECT count(*) FROM buildings_impacted 
19 999
```

### Find buildings in known flood risk area

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

##### Find buildings at risk
```sql
DROP TABLE IF EXISTS buildings_at_risk ;
CREATE TABLE buildings_at_risk
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