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
The `service` property is OPTIONAL. If it appears, it MUST be a link or an object. If it is a link, that link MUST point to another servmeta document. If it is an object it MUST be an embedded servemeta object.

TK:(what about two hops?)




## IANA Link Relation Values
There are interesting values to consider

 * author
 * copyright
 * help
 * license
 * profile
 * terms-of-service
 * version-history
 
## The Servmeta Registry
For each property that you put into the registry you have to provide:
 * name
 * short description
 * JSON type(string, object, array)


Below is an initial list of Servmeta Registry entries:
 * *title* : (string) title of the service
 * *description* : (string) description of the service
 * *contact* : (string) name of the primary contact for this service
 * *date* : (RFC3339 string) date this document was last modified
 * *concepts* : (array of URLs)
