# ListInvoicesResponseBody

Response containing a list of invoices and pagination metadata


## Fields

| Field                                                                             | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `meta`                                                                            | [Operations\ListInvoicesMeta](../../Models/Operations/ListInvoicesMeta.md)        | :heavy_check_mark:                                                                | Pagination metadata                                                               |
| `data`                                                                            | array<[Operations\ListInvoicesData](../../Models/Operations/ListInvoicesData.md)> | :heavy_check_mark:                                                                | Array of invoice objects                                                          |