# ListDocumentsMeta

Pagination metadata for the documents list.


## Fields

| Field                             | Type                              | Required                          | Description                       | Example                           |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `cursor`                          | *?string*                         | :heavy_minus_sign:                | Cursor for pagination.            | 20                                |
| `hasPreviousPage`                 | *bool*                            | :heavy_check_mark:                | Whether there is a previous page. | false                             |
| `hasNextPage`                     | *bool*                            | :heavy_check_mark:                | Whether there is a next page.     | true                              |