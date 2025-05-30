# ListInvoicesMeta

Pagination metadata


## Fields

| Field                                                | Type                                                 | Required                                             | Description                                          | Example                                              |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| `cursor`                                             | *string*                                             | :heavy_check_mark:                                   | Cursor for pagination; null if there is no next page | 25                                                   |
| `hasPreviousPage`                                    | *bool*                                               | :heavy_check_mark:                                   | Indicates if there is a previous page of results     | false                                                |
| `hasNextPage`                                        | *bool*                                               | :heavy_check_mark:                                   | Indicates if there is a next page of results         | true                                                 |