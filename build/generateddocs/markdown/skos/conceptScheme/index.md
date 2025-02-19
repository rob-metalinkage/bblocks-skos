
# SKOS ConceptScheme (Schema)

`ogc.skos.conceptScheme` *v0.1*

A Concept Scheme as defined in SKOS

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
$defs:
  conceptSchemeOrId:
    oneOf:
    - $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
    - $ref: '#'
  conceptSchemeOrIdArray:
    oneOf:
    - $ref: '#/$defs/conceptSchemeOrId'
    - type: array
      items:
        $ref: '#/$defs/conceptSchemeOrId'
type: object
properties:
  id:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
  concepts:
    $ref: https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/concept/schema.yaml#/$defs/conceptOrIdArray
    x-jsonld-reverse: skos:inScheme
    x-jsonld-type: '@id'
  topConcepts:
    $ref: https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/concept/schema.yaml#/$defs/conceptOrIdArray
    x-jsonld-id: skos:hasTopConcept
    x-jsonld-type: '@id'
allOf:
- $ref: https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/common/schema.yaml
oneOf:
- not:
    required:
    - skosType
- required:
  - skosType
  properties:
    skosType:
      const: ConceptScheme

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/conceptScheme/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/conceptScheme/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "concepts": {
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
      "@reverse": "skos:inScheme",
      "@type": "@id"
    },
    "topConcepts": {
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
      "@id": "skos:hasTopConcept",
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
[context.jsonld](https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/conceptScheme/context.jsonld)

## Sources

* [SKOS Reference](https://www.w3.org/TR/skos-reference/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-skos](https://github.com/ogcincubator/bblocks-skos)
* Path: `_sources/conceptScheme`

