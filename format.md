# Servmeta Format

## Overview

Servmeta is intended to be a format that exposes or links to metadata for a Web service (a.k.a. REST service or Web API). It can be seen as complementary to the *JSON Home* format. Whereas JSON Home serves as a starting point to start interacting with resources that are exposed as part of a Web service, Servmeta serves as a starting point to find and start interacting with resources that are *about* a Web service.

Servmeta is based on the assumption that service metadata is a diverse and constantly evolving field, with very different information needs based on the context and the constraints of Web service environments. For this reason, Servmeta is designed to be open and extensible and uses a [registry](https://tools.ietf.org/html/draft-wilde-registries) to make extensions discoverable.


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

Not all registered values in the [IANA registry of link relation types](https://www.iana.org/assignments/link-relations/link-relations.xhtml) are necessarily useful in context of the servmeta format. However, the goal of servmeta is to avoid duplication, so there should be a preference on reusing existing link relationship types over creating new properties for the servmeta format.

As an incomplete starting point when it comes to considering registered link relation types, here are interesting values to consider:

 * [`author`](https://www.w3.org/TR/html5/links.html#link-type-author)
 * [`copyright`](http://www.w3.org/TR/1999/REC-html401-19991224)
 * [`help`](http://www.w3.org/TR/html5/links.html#link-type-help)
 * [`home`](https://tools.ietf.org/html/draft-nottingham-json-home)
 * [`license`](http://www.iana.org/go/rfc4946)
 * [`profile`](http://www.iana.org/go/rfc6906)
 * [`service-desc`](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [`service-doc`](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [`service-meta`](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [`status`](https://tools.ietf.org/html/draft-wilde-service-link-rel)
 * [`sunset`](https://tools.ietf.org/html/draft-wilde-sunset-header)
 * [`terms-of-service`](http://www.iana.org/go/rfc6903)
 * [`version-history`](http://www.iana.org/go/rfc5829)
 * [`payment`](http://www.iana.org/go/rfc5988)


## The Servmeta Registry

Servmeta properties should not duplicate facilities that are already supported by exiting link relation types. Please first consult the [IANA registry of link relation types](https://www.iana.org/assignments/link-relations/link-relations.xhtml) before using and/or proposing additions to the existing vocabulary of servmeta properties.

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


## Potential Additional information

The idea of servmeta is to act as a starting point for exploring the information that is available for a service. This can be done via typed links, or through properties of the servmeta format. Below is an incomplete and evolving collection of information that would be interesting to capture, but where it is not quite clear how to best to it.

* *Client-side Libraries:* Information about software artifacts that client developers can use as a starting point when starting to write code against the service.


## TO DO

Validator should create an annotated version of your submitting servmeta document.
