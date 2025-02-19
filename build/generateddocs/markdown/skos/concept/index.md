
# SKOS Concept (Schema)

`ogc.skos.concept` *v0.1*

A Concept as defined in SKOS

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
$defs:
  conceptOrId:
    oneOf:
    - $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
    - $ref: '#'
  conceptOrIdArray:
    oneOf:
    - $ref: '#/$defs/conceptOrId'
    - type: array
      items:
        $ref: '#/$defs/conceptOrId'
type: object
properties:
  topConceptOf:
    $ref: https://raw.githubusercontent.com/ogcincubator/bblocks-skos/undefined/build/annotated/skos/conceptScheme/schema.yaml#/$defs/conceptSchemeOrIdArray
    x-jsonld-id: skos:topConceptOf
    x-jsonld-type: '@id'
  inScheme:
    $ref: https://raw.githubusercontent.com/ogcincubator/bblocks-skos/undefined/build/annotated/skos/conceptScheme/schema.yaml#/$defs/conceptSchemeOrIdArray
    x-jsonld-id: skos:inScheme
    x-jsonld-type: '@id'
  broaderConcepts:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:broaderConcepts
    x-jsonld-type: '@id'
  narrowerConcepts:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:narrowerConcepts
    x-jsonld-type: '@id'
  relatedConcepts:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:relatedConcepts
    x-jsonld-type: '@id'
  closeMatches:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:closeMatches
    x-jsonld-type: '@id'
  exactMatches:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:exactMatches
    x-jsonld-type: '@id'
  broadMatches:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:broadMatches
    x-jsonld-type: '@id'
  narrowMatches:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:narrowMatches
    x-jsonld-type: '@id'
  relatedMatches:
    $ref: '#/$defs/conceptOrIdArray'
    x-jsonld-id: skos:relatedMatches
    x-jsonld-type: '@id'
  collections:
    $ref: https://raw.githubusercontent.com/ogcincubator/bblocks-skos/undefined/build/annotated/skos/collection/schema.yaml#/$defs/collectionOrIdArray
    x-jsonld-id: skos:collections
    x-jsonld-type: '@id'
allOf:
- $ref: https://raw.githubusercontent.com/ogcincubator/bblocks-skos/undefined/build/annotated/skos/common/schema.yaml
oneOf:
- not:
    required:
    - skosType
- required:
  - skosType
  properties:
    skosType:
      const: Concept

```

Links to the schema:

* YAML version: [schema.yaml](https://raw.githubusercontent.com/ogcincubator/bblocks-skos/undefined/build/annotated/skos/concept/schema.json)
* JSON version: [schema.json](https://raw.githubusercontent.com/ogcincubator/bblocks-skos/undefined/build/annotated/skos/concept/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "topConceptOf": {
      "@context": {
        "concepts": {
          "@reverse": "skos:inScheme",
          "@type": "@id"
        },
        "topConcepts": {
          "@id": "skos:hasTopConcept",
          "@type": "@id"
        }
      },
      "@id": "skos:topConceptOf",
      "@type": "@id"
    },
    "inScheme": {
      "@context": {
        "concepts": {
          "@reverse": "skos:inScheme",
          "@type": "@id"
        },
        "topConcepts": {
          "@id": "skos:hasTopConcept",
          "@type": "@id"
        }
      },
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
    },
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
[context.jsonld](https://raw.githubusercontent.com/ogcincubator/bblocks-skos/undefined/build/annotated/skos/concept/context.jsonld)

## Sources

* [SKOS Reference](https://www.w3.org/TR/skos-reference/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-skos](https://github.com/ogcincubator/bblocks-skos)
* Path: `_sources/concept`

