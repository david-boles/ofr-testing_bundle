# JSON API
Note: 'must' means 'invalid if not' while 'should' means 'it is recommended but not necessary'.

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
  "name": "Your Document's Name",
  "type": "document",
  "url": "https://your.document/url.json"
}
```
The value of `url` must begin with `https://` and should point to a valid `Document` object served as JSON.

## `TermInfo` Objects
`TermInfo` objects are a subset of `ResourceInfo` objects and contain metadata about terms provided by a bundle. A `TermInfo` object must have `type` be `term` and one or more of `description`, `url` or `docID` parameters.
```json
{
  "name": "Your Term's Name",
  "type": "term",
  "docID": "docID1"
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
There are no restrictions as to the contents of the URL. If both a `docID` and `url` are specified, OFR will try to link to the document if it exists, otherwise it will fall back to the URL.
