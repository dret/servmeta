# Servmeta Format

## Overview
TK

## Format Basics
Servmeta is serialized as a JSON format

 * You MUST NOT create a property that uses a name that appears in the [IANA Link Relations registry](https://www.iana.org/assignments/link-relations/link-relations.xml).
 

## dret Example

```javascript
{
  "service" : {},
  "links": {},
  "title": "",
  "description": "",
  "contact": ""
}
```
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
