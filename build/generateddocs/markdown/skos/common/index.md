
# Common SKOS properties (Schema)

`ogc.skos.common` *v0.1*

A generic SKOS object that can have labels and notes

[*Status*](http://www.opengis.net/def/status): Under development

## Examples

### Object with a single prefLabel
#### json
```json
{
  "prefLabel": "A single label"
}

```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/common/context.jsonld",
  "prefLabel": "A single label"
}
```

#### ttl
```ttl
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .

[] skos:prefLabel "A single label" .


```


### Object with prefLabel in two languages
#### json
```json
{
  "prefLabel": {
    "en": "This is a multilingual label",
    "fr": "Ceci est une étiquette multilingue"
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/common/context.jsonld",
  "prefLabel": {
    "en": "This is a multilingual label",
    "fr": "Ceci est une \u00e9tiquette multilingue"
  }
}
```

#### ttl
```ttl
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .

[] skos:prefLabel "This is a multilingual label"@en,
        "Ceci est une étiquette multilingue"@fr .


```


### Object with several altLabel's
#### json
```json
{
  "altLabel": [
    "A label with no language",
    {
      "en": "Another one with English and Spanish values",
      "es": "Otra con valores en inglés y español"
    }
  ]
}
```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/common/context.jsonld",
  "altLabel": [
    "A label with no language",
    {
      "en": "Another one with English and Spanish values",
      "es": "Otra con valores en ingl\u00e9s y espa\u00f1ol"
    }
  ]
}
```

#### ttl
```ttl
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .

[] skos:altLabel [ ],
        "A label with no language" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
$defs:
  languageString:
    oneOf:
    - type: string
    - type: object
      patternProperties:
        ^[A-Za-z]{1,8}(-[A-Za-z0-9]{1,8})*$:
          type: string
      additionalProperties: false
  languageStringArray:
    oneOf:
    - $ref: '#/$defs/languageString'
    - type: array
      items:
        $ref: '#/$defs/languageString'
  typedValue:
    oneOf:
    - type: string
    - type: object
      required:
      - '@value'
      properties:
        '@value':
          type: string
        '@type':
          type: string
type: object
properties:
  id:
    $ref: https://opengeospatial.github.io/bblocks/annotated-schemas/ogc-utils/iri-or-curie/schema.yaml
    x-jsonld-id: '@id'
  skosType:
    enum:
    - Concept
    - ConceptScheme
    - Collection
    - OrderedCollection
    x-jsonld-id: '@type'
  prefLabel:
    $ref: '#/$defs/languageString'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#prefLabel
    x-jsonld-container: '@language'
  altLabel:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#altLabel
    x-jsonld-container: '@language'
  hiddenLabel:
    $ref: '#/$defs/languageStringArray'
  notation:
    oneOf:
    - $ref: '#/$defs/typedValue'
    - type: array
      items:
        $ref: '#/$defs/typedValue'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#notation
    x-jsonld-container: '@language'
  note:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#note
    x-jsonld-container: '@language'
  changeNote:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#changeNote
    x-jsonld-container: '@language'
  definition:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#definition
    x-jsonld-container: '@language'
  editorialNote:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#editorialNote
    x-jsonld-container: '@language'
  example:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#example
    x-jsonld-container: '@language'
  historyNote:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#historyNote
    x-jsonld-container: '@language'
  scopeNote:
    $ref: '#/$defs/languageStringArray'
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#scopeNote
    x-jsonld-container: '@language'
x-jsonld-extra-terms:
  ConceptScheme: http://www.w3.org/2004/02/skos/core#ConceptScheme
  Concept: http://www.w3.org/2004/02/skos/core#Concept
  Collection: http://www.w3.org/2004/02/skos/core#Collection
  OrderedCollection: http://www.w3.org/2004/02/skos/core#OrderedCollection
x-jsonld-prefixes:
  skos: http://www.w3.org/2004/02/skos/core#

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/common/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/common/schema.yaml)


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
    "skos": "http://www.w3.org/2004/02/skos/core#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-skos/build/annotated/skos/common/context.jsonld)

## Sources

* [SKOS Reference](https://www.w3.org/TR/skos-reference/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-skos](https://github.com/ogcincubator/bblocks-skos)
* Path: `_sources/common`

