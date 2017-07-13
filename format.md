# Servmeta Format

## Overview
TK

## Format Basics
Servmeta is serialized as a JSON format

 * You MUST NOT create a property that uses a name that appears in the [IANA Link Relations registry](https://www.iana.org/assignments/link-relations/link-relations.xml).


## Example

```javascript
{
  "service" : {},
  "links": {},
  "title": "",
  "description": "",
  "contact": ""
}
```

### Service Property
The `service` property is OPTIONAL. If it appears, it MUST be a link or an object. If it is a link, that link MUST point to another servmeta document. If it is an object it MUST be an embedded servmeta object.

For example:
```javascript
{
  ...
  "service" : "http://api.example.org/services/servmeta.json",
  ...
}
```
OR
```javascript
{
  ...
  "service" : {
     "title" : "...",
     "description" : "...",
     "contact" : "..."
     "links" : {}
  }
  ...
}
```

TK:(what about two hops?)

### Link Properties
The `links` property is OPTIONAL. If it appears, it MUST be an object with pairs of relationship type (RFC5988 compliant) and an array of URI strings.

For example:

```javascript
{
  ...
  "links" : {
    "service-doc" : [
      "http://api.example.org/services/docs/person",
      "http://api.eample.org/services/docs/place"
    ]
  }
  ...
}
```

## IANA Link Relation Values
There are interesting values to consider

 * author
 * copyright
 * help
 * home (defined in [JSON Home I-D](https://tools.ietf.org/html/draft-nottingham-json-home))
 * license
 * profile
 * service-desc
 * service-doc
 * service-meta
 * terms-of-service
 * version-history

## The Servmeta Registry
For each property that you put into the registry you have to provide:
 * name
 * short description
 * JSON type(string, object, array)


Below is an initial list of Servmeta Registry entries:
 * **title** : (string) title of the service
 * **description** : (string) description of the service
 * **contact** : (string) name of the primary contact for this service
 * **date** : (RFC3339 string) date this document was last modified
 * **concepts** : (array of URLs)


## TO DO

Validator should create an annotated version of your submitting servmeta document.
