# ListCustomersResponseBody

Retrieve a list of customers for the authenticated team.


## Fields

| Field                                                                               | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `meta`                                                                              | [Operations\ListCustomersMeta](../../Models/Operations/ListCustomersMeta.md)        | :heavy_check_mark:                                                                  | Pagination metadata for the customers response                                      |
| `data`                                                                              | array<[Operations\ListCustomersData](../../Models/Operations/ListCustomersData.md)> | :heavy_check_mark:                                                                  | Array of customers matching the query criteria                                      |