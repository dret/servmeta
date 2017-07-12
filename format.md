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



 * title
 * description
 * contact
 * date
 * concepts   
