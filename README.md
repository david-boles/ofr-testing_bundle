# JSON API
All OFR dynamically retrived data is JSON files parsable into an object.

## `Manifest` Objects
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

## `ResourceInfo` Objects
`ResourceInfo` objects contain metadata about resources provided by a bundle. At a minimum they need a `name` and a `type`:
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

`ResourceInfo` objects can also __optionally__ specify a `description` attribute:
```json
{
  "name": "Your Resource's Name",
  "type": "resourceType",
  "description": "Your resource's description."
}
```

## `DocumentInfo` Objects
`DocumentInfo` objects are a subset of `ResourceInfo` objects and contain metadata about documents provided by a bundle. In addition to a `name`, optional `description`, and `type` of `document` attributes they require a `url` attribute:
```json
{
  "name": "Your Documents's Name",
  "type": "document",
  "url": "https://your.document/url.json"
}
```
The value of `url` must begin with `https://` and should point to a valid `Document` object served as JSON.
