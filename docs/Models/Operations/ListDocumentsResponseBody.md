# ListDocumentsResponseBody

Response containing a list of documents and pagination metadata.


## Fields

| Field                                                                               | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `meta`                                                                              | [Operations\ListDocumentsMeta](../../Models/Operations/ListDocumentsMeta.md)        | :heavy_check_mark:                                                                  | Pagination metadata for the documents list.                                         |
| `data`                                                                              | array<[Operations\ListDocumentsData](../../Models/Operations/ListDocumentsData.md)> | :heavy_check_mark:                                                                  | Array of document objects.                                                          |