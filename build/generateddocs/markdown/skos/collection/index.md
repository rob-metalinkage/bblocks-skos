
# SKOS Collection (Schema)

`ogc.skos.collection` *v0.1*

A Collection as defined in SKOS

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
$defs:
  collectionOrId:
    oneOf:
    - $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
    - $ref: '#'
  collectionOrIdArray:
    oneOf:
    - $ref: '#/$defs/collectionOrId'
    - type: array
      items:
        $ref: '#/$defs/collectionOrId'
type: object
allOf:
- $ref: https://rob-metalinkage.github.io/bblocks-skos/build/annotated/skos/common/schema.yaml
oneOf:
- not:
    required:
    - skosType
- required:
  - skosType
  not:
    required:
    - memberList
  properties:
    skosType:
      const: Collection
    members:
      $ref: https://rob-metalinkage.github.io/bblocks-skos/build/annotated/skos/concept/schema.yaml#/$defs/conceptOrIdArray
      x-jsonld-id: skos:members
      x-jsonld-type: '@id'
- required:
  - skosType
  not:
    required:
    - members
  properties:
    skosType:
      const: OrderedCollection
      memberList:
        $ref: https://rob-metalinkage.github.io/bblocks-skos/build/annotated/skos/concept/schema.yaml#/$defs/conceptOrIdArray
x-jsonld-extra-terms:
  memberList:
    x-jsonld-id: skos:memberList
    x-jsonld-type: '@id'
    x-jsonld-container: '@list'

```

Links to the schema:

* YAML version: [schema.yaml](https://rob-metalinkage.github.io/bblocks-skos/build/annotated/skos/collection/schema.json)
* JSON version: [schema.json](https://rob-metalinkage.github.io/bblocks-skos/build/annotated/skos/collection/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "id": "@id",
    "skosType": "@type",
    "prefLabel": {
      "@id": "skos:prefLabel",
      "@container": "@language"
    },
    "altLabel": {
      "@id": "skos:altLabel",
      "@container": "@language"
    },
    "notation": {
      "@id": "skos:notation",
      "@container": "@language"
    },
    "note": {
      "@id": "skos:note",
      "@container": "@language"
    },
    "changeNote": {
      "@id": "skos:changeNote",
      "@container": "@language"
    },
    "definition": {
      "@id": "skos:definition",
      "@container": "@language"
    },
    "editorialNote": {
      "@id": "skos:editorialNote",
      "@container": "@language"
    },
    "example": {
      "@id": "skos:example",
      "@container": "@language"
    },
    "historyNote": {
      "@id": "skos:historyNote",
      "@container": "@language"
    },
    "scopeNote": {
      "@id": "skos:scopeNote",
      "@container": "@language"
    },
    "ConceptScheme": "skos:ConceptScheme",
    "Concept": "skos:Concept",
    "Collection": "skos:Collection",
    "OrderedCollection": "skos:OrderedCollection",
    "members": {
      "@context": {
        "topConceptOf": {
          "@id": "skos:topConceptOf",
          "@type": "@id"
        },
        "inScheme": {
          "@id": "skos:inScheme",
          "@type": "@id"
        },
        "broaderConcepts": {
          "@id": "skos:broaderConcepts",
          "@type": "@id"
        },
        "narrowerConcepts": {
          "@id": "skos:narrowerConcepts",
          "@type": "@id"
        },
        "relatedConcepts": {
          "@id": "skos:relatedConcepts",
          "@type": "@id"
        },
        "closeMatches": {
          "@id": "skos:closeMatches",
          "@type": "@id"
        },
        "exactMatches": {
          "@id": "skos:exactMatches",
          "@type": "@id"
        },
        "broadMatches": {
          "@id": "skos:broadMatches",
          "@type": "@id"
        },
        "narrowMatches": {
          "@id": "skos:narrowMatches",
          "@type": "@id"
        },
        "relatedMatches": {
          "@id": "skos:relatedMatches",
          "@type": "@id"
        },
        "collections": {
          "@id": "skos:collections",
          "@type": "@id"
        }
      },
      "@id": "skos:members",
      "@type": "@id"
    },
    "memberList": {
      "@id": "skos:memberList",
      "@type": "@id",
      "@container": "@list"
    },
    "skos": "http://www.w3.org/2004/02/skos/core#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://rob-metalinkage.github.io/bblocks-skos/build/annotated/skos/collection/context.jsonld)

## Sources

* [SKOS Reference](https://www.w3.org/TR/skos-reference/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/rob-metalinkage/bblocks-skos](https://github.com/rob-metalinkage/bblocks-skos)
* Path: `_sources/collection`

