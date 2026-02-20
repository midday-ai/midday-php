# NotificationsResponseSchemaMeta

Pagination metadata


## Fields

| Field                                         | Type                                          | Required                                      | Description                                   | Example                                       |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| `cursor`                                      | *string*                                      | :heavy_check_mark:                            | Cursor for pagination (null if no more pages) | 40                                            |
| `hasPreviousPage`                             | *bool*                                        | :heavy_check_mark:                            | Whether there are previous pages available    | true                                          |
| `hasNextPage`                                 | *bool*                                        | :heavy_check_mark:                            | Whether there are more pages available        | false                                         |