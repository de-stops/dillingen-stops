# dillingen-stops

This is a simple script to download [LK Dillingen](http://www.landkreis-dillingen.de/index.php?id=0,92) stops as [GTFS-compatible CSV](https://developers.google.com/transit/gtfs/reference/stops-file).

The script uses the following endpoint:

```
http://efa.mobilitaetsverbund.de/web/XML_COORD_REQUEST?&jsonp=&boundingBox=&boundingBoxLU={minx}%3A{miny}%3AWGS84%5BDD.DDDDD%5D&boundingBoxRL={maxx}%3A{maxy}%3AWGS84%5BDD.DDDDD%5D&coordOutputFormat=WGS84%5BGGZHTXX%5D&type_1=STOP&outputFormat=json&inclFilter=1
```

It starts from bounding box `(10.2, 48.4, 10.9, 48.9)` and works down to smaller quadrants.

The script produces CSV output in the following format:

```
stop_id,stop_name,stop_lon,stop_lat,stop_code
"2505557","Lauingen (Donau), Weisinger Str. 30",10.4503345726,48.5586336291,"de:9773:5557"
```

# Prerequisites

These scrips use PostGIS to filter stops belonging to administrative regions covered by the transport company.  
See [this project](https://github.com/highsource/postgis-verwaltungsgebiete) for a simple way to create a PostGIS database with administrative regions.

# Usage

## Windows

```
npm install
00-export-unfiltered-stops
01-filter-stops
```

# Disclaimer

Usage of this script may or may not be legal, use on your own risk.  
This repository provides only source code, no data.

# License

Source code is licensed under [BSD 2-clause license](LICENSE). No license and no guarantees implied on the produced data, produce and use on your own risk.