# ListInvoicesRequest


## Fields

| Field                                    | Type                                     | Required                                 | Description                              | Example                                  |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `cursor`                                 | *?string*                                | :heavy_minus_sign:                       | N/A                                      | 25                                       |
| `sort`                                   | array<*string*>                          | :heavy_minus_sign:                       | N/A                                      | [<br/>"createdAt",<br/>"desc"<br/>]      |
| `pageSize`                               | *?float*                                 | :heavy_minus_sign:                       | N/A                                      | 25                                       |
| `q`                                      | *?string*                                | :heavy_minus_sign:                       | N/A                                      | Acme                                     |
| `start`                                  | *?string*                                | :heavy_minus_sign:                       | N/A                                      | 2024-01-01                               |
| `end`                                    | *?string*                                | :heavy_minus_sign:                       | N/A                                      | 2024-01-31                               |
| `statuses`                               | array<*string*>                          | :heavy_minus_sign:                       | N/A                                      | [<br/>"paid",<br/>"unpaid"<br/>]         |
| `customers`                              | array<*string*>                          | :heavy_minus_sign:                       | N/A                                      | [<br/>"customer-uuid-1",<br/>"customer-uuid-2"<br/>] |