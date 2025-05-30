# ListTransactionsResponseBody

Retrieve a list of transactions for the authenticated team.


## Fields

| Field                                                                                   | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `meta`                                                                                  | [Operations\ListTransactionsMeta](../../Models/Operations/ListTransactionsMeta.md)      | :heavy_check_mark:                                                                      | Pagination metadata for the transactions response                                       |
| `data`                                                                                  | array<[Components\TransactionResponse](../../Models/Components/TransactionResponse.md)> | :heavy_check_mark:                                                                      | Array of transactions matching the query criteria                                       |