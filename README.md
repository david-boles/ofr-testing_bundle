# JSON API
All OFR dynamically retrived data is JSON files parsable into an object.

## Manifest Objects
Minimal requirement:
```json
{
  "metadata": {
    "name": "Your Resource Bundle's Name"
  },
  "resources": {}
}
```
The objects `.resources` object contains resourceID keys and ResourceInfo values. E.g.
```json
{
  "metadata": {
    "name": "Your Resource Bundle's Name"
  },
  "resources": {
    "resourceID1": ResourceInfo,
    "resourceID2": ResourceInfo
  }
}
```

## ResourceInfo Objects
ResourceInfo objects contain metadata about resources provided by a bundle. At a minimum they need a `name` and a `type`:
```json
{
  "name": "Your Resource's Name",
  "type": "resourceType"
}
```
The `type` key is required to have one of the following `resourceType`s. Each corresponds to a definition on this page:

type | description
--- | ---
document | A page of information.
term | A term that should be included in the glossary and can be used in other resources.
index | A resource providing links to other resources.
collection | A resource that includes other resources into it's own page as a linear progression.
