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

 * [author](https://www.w3.org/TR/html5/links.html#link-type-author)
 * [copyright](http://www.w3.org/TR/1999/REC-html401-19991224)
 * [help](http://www.w3.org/TR/html5/links.html#link-type-help)
 * [home](https://tools.ietf.org/html/draft-nottingham-json-home)
 * [license](http://www.iana.org/go/rfc4946)
 * [profile](http://www.iana.org/go/rfc6906)
 * [service-desc](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [service-doc](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [service-meta](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [status](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [terms-of-service](http://www.iana.org/go/rfc6903)
 * [version-history](http://www.iana.org/go/rfc5829)
 * [payment](RFC 5988)

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
