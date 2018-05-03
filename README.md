# JSON API
All OFR dynamically retrived data is JSON files parsable into an object.
## Manifests
Minimal requirement:
```json
{
  "metadata": {
    "name": "Your Resource Bundle's Name"
  },
  "documents": {},
  "terms": {}
}
```
The objects `.documents` and `.terms` contain document/termID key-Document/TermInfo object pairs. E.g.
```json
{
  "metadata": {
    "name": "Your Resource Bundle's Name"
  },
  "documents": {
    "docID1": DocumentInfo,
    "docID2": <a DocumentInfo object>
  },
  "terms": {
    "termID1": <a TermInfo object>,
    "termID2": <a TermInfo object>
  }
}
```
