Note: 'must' or 'requuires' means 'invalid if not' while 'should' means 'it is recommended but not necessary'.

# Objects That Store Content Metadata
## `Manifest` Objects
Resource bundle manifests contain metadata the bundle itself and all of it's resources. At a minimum they must contain the following:
```json
{
  "metadata": {
    "name": "Your Resource Bundle's Name"
  },
  "resources": {}
}
```
A manifest's `resources` object contains zero or more `resourceID` keys and `ResourceInfo` values. E.g.
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
Bundle manifests can also contain a `featured` array containing `resourceID`s:
```json
{
  "metadata": {
    "name": "Your Resource Bundle's Name"
  },
  "resources": {
    "resourceID1": ResourceInfo,
    "resourceID2": ResourceInfo
  },
  "featured": [
    "resourceID1",
    "resourceID2"
  ]
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
The `type` key is required to have one of the following `resourceType`s. Each corresponds to a definition on this page and each type has it's own additional requirements:

type | description
--- | ---
document | A page of information.
term | A term that should be included in the glossary and can be used in other resources.
index | A resource providing links to other resources.
collection | A resource that includes other resources into it's own page as a linear progression.

`ResourceInfo` objects can also optionally specify a `description` attribute which must be a string and/or an `unlisted` boolean attribute:
```json
{
  "name": "Your Resource's Name",
  "type": "resourceType",
  "description": "Your resource's description.",
  "unlisted": true
}
```
The `unlisted` attribute is intended for resources that will primarily be used within other resources and therefore shouldn't be found individually.

## `DocumentInfo` Objects
`DocumentInfo` objects are a subset of `ResourceInfo` objects and contain metadata about documents provided by a bundle. In addition to a `name`, optional `description`, and `type` of `document` attributes they require a `url` attribute:
```json
{
  "name": "Your Document's Name",
  "type": "document",
  "url": "https://your.document/url.json"
}
```
The value of `url` must begin with `https://` and should point to a valid `Document` object served as JSON.

## `TermInfo` Objects
`TermInfo` objects are a subset of `ResourceInfo` objects and contain metadata about terms provided by a bundle. A `TermInfo` object must have a `type` of `term` and should have one or more of `description`, `url` or `resourceID` parameters.
```json
{
  "name": "Your Term's Name",
  "type": "term",
  "resourceID": "resourceID1"
}
```
```json
{
  "name": "Your Term's Name",
  "type": "term",
  "description": "Description of the term.",
  "url": "http://www.example.com"
}
```
There are no restrictions as to the contents of the URL. If both a `resource` and `url` are specified, OFR will try to link to the resource if it exists, otherwise it will fall back to the URL.

## `IndexInfo` Objects
`TermInfo` objects are a subset of `ResourceInfo` objects. They require an additional `indexed` attribute containing an array of string `resourceID`s:
```json
{
  "name": "Your Index's Name",
  "type": "index",
  "indexed": [
    "resourceID1",
    "resourceID2"
  ]
}
```

## `CollectionInfo` Objects
`CollectionInfo` objects are a subset of `ResourceInfo` objects. They require an additional `collected` attribute containing an array of string `resourceID`s:
```json
{
  "name": "Your Index's Name",
  "type": "index",
  "collected": [
    "resourceID1",
    "resourceID2"
  ]
}
```
