# Fractal

Fractal is rich and scalable map style based on the free data from collaborative
mapping project [OpenStreetMap](https://www.openstreetmap.org) (OSM), using 
[CartoCSS](https://github.com/mapbox/carto) stylesheet processor as a tool 
for maintaining compact rendering rules and [Mapnik](https://mapnik.org/)
as rendering backend.

Fractal is general purpose, but it focuses on high zoom levels and aims to support 
so called "micromapping". It will be probably less usable for rural and outdoor areas, 
where almost all the objects are important and should be amplified to be visible.
On the other hand, urban areas filled with lot of POIs should be less cluttered,
because objects are moved to the corresponding zoom levels according to their size,
and at the same time showing more things, because high zoom levels can fit more.
In particular, zoom level 20 (z20) can contain a lot of useful details, not included
in other map styles.

![screenshot](https://raw.github.com/openstreetmap-polska/fractal/master/preview.png)

# Installation

You need a PostGIS database populated with OpenStreetMap data along with auxillary 
shapefiles. See [INSTALL.md](INSTALL.md). 

The easiest way to start is probably to deploy a [Docker container](DOCKER.md), 
which allows to easily preview the changes.

If you want to make a production server using Fractal, look at the tutorials at
[Switch2OSM](https://switch2osm.org) and follow the instructions.

# Contributing

Contributions to this project are welcome, see [CONTRIBUTING.md](CONTRIBUTING.md)
for full details.

Please follow [Code of Conduct](CODE_OF_CONDUCT.md) when interacting with
other people.

General guidelines are outlined in [CARTOGRAPHY.md](CARTOGRAPHY.md). It should
give you the idea about different aspects of the project, however this is not 
a rule book.

# Customization

These stylesheets can be used in your own cartography projects, and are designed
to be easily customised. They work with [Kosmtik](https://github.com/kosmtik/kosmtik)
and also with the command-line [CartoCSS](https://github.com/mapbox/carto) processor.

Currently Fractal uses "name" key for rendering names, which holds the common names 
used on a given area. If you want to apply different language rules, check the 
[l10n data preprocessor](https://github.com/giggls/mapnik-german-l10n) from German style.

# Versioning

This project follows a common MAJOR.MINOR.PATCH versioning scheme
([semantic versioning](https://semver.org)). In the context of a cartographic 
project you can expect the following:

* PATCH: When a patch version is released, there would be no reason not to
  upgrade. PATCH versions contain only bugfixes e.g. stylesheets won't compile,
  features are missing by mistake, etc.
* MINOR: These are routine releases. They will contain changes to what's shown 
  on the map, how they appear, new features added and old features removed. 
  They may rarely contain changes to assets i.e. shapefiles and fonts but will 
  not contain changes that require software or database upgrades.
* MAJOR: Any change the requires reloading a database or upgrading software
  dependecies will trigger a major version change.

# Related resources

This project started as a fork of a default OSM map style
[OpenStreetMap Carto](https://github.com/gravitystorm/openstreetmap-carto) 
(OSM Carto) about version 5.3.1. Fractal shares a lot of the ideas and code with it, 
including [CC0 1.0 license](LICENSE.txt), but some of them might need rework 
in the future:

* You can look at the [changelog](CHANGELOG.md) to see what has changed in the past
* [Release process](RELEASES.md) will be probably more relaxed
* [Usecases](USECASES.md) were meant as a high level help for developing the style,
  however that did not work well enough

Basic documentation about OSM Carto is provided on the OSM wiki page
[Standard tile layer](https://wiki.openstreetmap.org/wiki/Standard_tile_layer). It includes such useful links as:

* [Map key](https://wiki.openstreetmap.org/wiki/Standard_tile_layer/Key) - this is 
  quite big and still incomplete list of the features found in this style
* [OpenStreetMap Carto Tutorials](https://ircama.github.io/osm-carto-tutorials/) 
  - this is a good place to get more informations about the project
  
Map scalabillity issues using the most neutral properties of objects, like typical
and relative size, are discussed in these two blog entries:

* [OpenStreetMap Carto - my thoughts on development (part 1)](https://www.openstreetmap.org/user/kocio/diary/44769)
* [OpenStreetMap Carto - my thoughts on development (part 2)](https://www.openstreetmap.org/user/kocio/diary/44852)
