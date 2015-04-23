## Query la Overpass

http://overpass-turbo.eu/

```
node
  [amenity=cafe]
  ({{bbox}});
out;
```

screenshots/overpass.jpg

* ne uităm la datele osm xml
* export - geojson
* open in geojson.io
* export - save as gist

### query "și"
```
node
  [amenity=cafe]
  [wheelchair=yes]
  ({{bbox}});
out;
```

### query "sau"
```
(
  node
    [amenity=cafe]
    ({{bbox}});
  node
    [amenity=restaurant]
    ({{bbox}});
);
out;
```

### query "tot"
```
(
  node({{bbox}});
  <;
);
out meta;
```

* `<;` înseamnă "ia obiectele părinte" (poligoane și relații care conțin noduri
  din zonă)

### query "unde sunt?"


### query regiune
```
relation
  [place=city]
  [name="Cluj-Napoca"];

>;
out;
```

* `>;` înseamnă "ia obiectele copil" (nodurile care formează poligonul)


### limit query to city
```
area
  [place=city]
  [name="Cluj-Napoca"];
out;

node
  [amenity=cafe]
  (area);
out;
```

### Optimizare

* `out skel qt;` înseamnă "dă-mi rezultate fără tag-uri și nesortate" (mai rapid)


## QGIS

* open geojson file
* install openlayers plugin
* show osm background (harta a schimbat proiecția)