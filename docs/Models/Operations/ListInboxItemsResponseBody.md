# ListInboxItemsResponseBody

Retrieve a list of inbox items for the authenticated team.


## Fields

| Field                                                                                 | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `meta`                                                                                | [Operations\ListInboxItemsMeta](../../Models/Operations/ListInboxItemsMeta.md)        | :heavy_check_mark:                                                                    | Pagination metadata for the inbox list response.                                      |
| `data`                                                                                | array<[Operations\ListInboxItemsData](../../Models/Operations/ListInboxItemsData.md)> | :heavy_check_mark:                                                                    | List of inbox items                                                                   |