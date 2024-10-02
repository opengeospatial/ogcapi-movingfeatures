# OGC API - Moving Features

This GitHub repository contains the OGC API - Moving Features for providing query and access to geospatial data and services, especially movement data.

The [OGC API - Moving Features](https://ogcapi.ogc.org/movingfeatures/) Standard is part of the OGC API suite of standards.
[OGC API Standards](https://ogcapi.ogc.org) define modular API building blocks to spatially enable Web APIs in a consistent way.
[OpenAPI](http://openapis.org) is used to define the reusable API building blocks.

## Overview of OGC API - Moving Features - Part 1: Core

The summary of the OGC API – MovingFeatures – Part 1: Core is described in the below table. 

| URL Path                                                        | Supported HTTP(s) Methods |
|-----------------------------------------------------------------|---------------------------|
| /collections/{c_id}                                             | GET,DELETE,PUT            |
| /collections/{c_id}/items                                       | GET,POST                  |
| /collections/{c_id}/items/{mf_id}                               | GET,DELETE                |
| /collections/{c_id}/items/{mf_id}/tgsequence                    | GET,POST                  |
| /collections/{c_id}/items/{mf_id}/tgsequence/{tg_id}            | DELETE                    |
| /collections/{c_id}/items/{mf_id}/tgsequence/{tg_id}/{tg_query} | GET                       |
| /collections/{c_id}/items/{mf_id}/tproperties                   | GET,POST                  |
| /collections/{c_id}/items/{mf_id}/tproperties/{tp_name}         | GET,POST,DELETE           |
| /collections/{c_id}/items/{mf_id}/tproperties/{tp_name}/{tv_id} | DELETE                    |

<details>
<summary> MovingFeatures Collection Catalog </summary>

```
GET /collections    
```

Retrieve catalogs of a moving features collection.

```
POST /collections
```

Register metadata about a collection of moving features.

```
GET /collections/{collectionId}
```

Access metadata about the collection with id `{collectionId}`.

```
DELETE /collections/{collectionId}
```

The collection catalog with id `{collectionId}` and including metadata and moving features SHOULD be deleted.

```
PUT /collections/{collectionId}
```

Replace metadata about the collection with id `{collectionId}`.
</details>

<details>
<summary> MovingFeatures </summary>

<details>
<summary> MovingFeature </summary>

```
GET /collections/{collectionId}/items
```

Retrieve the moving feature collection to access the static information of the moving feature by simple filtering and a limit.

```
POST /collections/{collectionId}/items
```

Insert a set of moving features or a moving feature into a collection with id `{collectionId}`.

```
GET /collections/{collectionId}/items/{mFeatureId}
```

Access the static data of the moving feature with id `{mFeatureId}`.
The static data of a moving feature is not included temporal geometries and temporal properties.

```
DELETE /collections/{collectionId}/items/{mFeatureId}
```

Delete a single moving feature with id `{mFeatureId}`.
</details>

<details>
<summary> TemporalGeometrySequence </summary>

```
GET /collections/{collectionId}/items/{mFeatureId}/tgsequence
```

Retrieve the movement data of the single moving feature with id `{mFeatureId}`.

```
POST /collections/{collectionId}/items/{mFeatureId}/tgsequence
```

Add movement data into the moving feature with id `{mFeatureId}`.

```
DELETE /collections/{collectionId}/items/{mFeatureId}/tgsequence/{tGeometryId}
```

Delete a single temporal geometry with id `{tGeometryId}`.
</details>

<details>
<summary> TemporalGeometryQuery </summary>

```
GET /collections/{collectionId}/items/{mFeatureId}/tgsequence/{tGeometryId}/distance
```

Get a time-to-distance curve of a temporal primitive geometry with id `{tGeometryId}`.

```
GET /collections/{collectionId}/items/{mFeatureId}/tgsequence/{tGeometryId}/velocity
```

Get a time-to-velocity curve of a temporal primitive geometry with id `{tGeometryId}`.

```
GET /collections/{collectionId}/items/{mFeatureId}/tgsequence/{tGeometryId}/acceleration
```

Get a time-to-acceleration curve of a temporal primitive geometry with id `{tGeometryId}`.

</details>

<details>
<summary> TemporalProperties </summary>

```
GET /collections/{collectionId}/items/{mFeatureId}/tproperties
```

Retrieve the static information of the temporal property data that included a single moving feature with id `{mFeatureId}`.
The static data of a temporal property is not included temporal values (property `values`).

```
POST /collections/{collectionId}/items/{mFeatureId}/tproperties
```

Add temporal property data into a moving feature with id `{mFeatureId}`.

```
GET /collections/{collectionId}/items/{mFeatureId}/tproperties/{tPropertyName}
```

Retrieve temporal values with a specified name `{tPropertyName}` of temporal property.

```
POST /collections/{collectionId}/items/{mFeatureId}/tproperties/{tPropertyName}
```

Add more temporal values data into a temporal property with id `{tPropertyName}`.

```
DELETE /collections/{collectionId}/items/{mFeatureId}/tproperties/{tPropertyName}
```

Delete a single temporal property with id `{tPropertyName}`.

```
DELETE /collections/{collectionId}/items/{mFeatureId}/tproperties/{tPropertyName}/{tValueId}
```

Delete a single temporal primitive value with id `{tValueId}`.


</details>

</details>

## Building the Standard document

```
git clone https://github.com/opengeospatial/ogcapi-movingfeatures.git

cd ogcapi-movingfeatures

docker pull metanorma/metanorma

docker run -v "$(pwd)":/metanorma -v ${HOME}/.fontist/fonts/:/config/fonts  metanorma/metanorma  metanorma compile --agree-to-terms -t ogc -x html,pdf standard/document.adoc
```

## Using the Standard
An **OGC API - Moving Features - Part 1: Core** Standard is available:

* [HTML version](https://docs.ogc.org/DRAFTS/22-003.html)
* [PDF version](https://docs.ogc.org/DRAFTS/22-003.pdf)

Those who want to just see the endpoints and responses can explore the generic OpenAPI definition on Swagger:

* [OpenAPI (generated by Redocly)](https://developer.ogc.org/api/movingfeatures/index.html)

There have been several implementations of the Standard, though they are against different versions of the evolving draft:

* [MF-API Server](https://github.com/aistairc/mf-api)
* **T.B.D**

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership, shall be incorporated into OGC API - Moving Features Standards documents and that all copyright and intellectual property shall be vested to the OGC.

The OGC's Moving Features Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the Standard, but is working to do as much work in public as possible.

* [Moving Features Standards Working Group Charter](https://www.ogc.org/projects/groups/movfeatswg)
* [Open issues](https://github.com/opengeospatial/ogcapi-movingfeatures/issues)
* [Copy of License Language](https://github.com/opengeospatial/ogcapi-movingfeatures/blob/master/LICENSE)

Pull Requests from contributors are welcomed. However, please note that by sending a Pull Request or Commit to this GitHub repository, you are agreeing to the terms in the Observer Agreement https://portal.ogc.org/files/?artifact_id=92169
