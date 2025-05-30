# UpdateTransactionsResponseBody

Transactions updated


## Fields

| Field                                                                                   | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `meta`                                                                                  | [Operations\UpdateTransactionsMeta](../../Models/Operations/UpdateTransactionsMeta.md)  | :heavy_check_mark:                                                                      | Pagination metadata for the transactions response                                       |
| `data`                                                                                  | array<[Components\TransactionResponse](../../Models/Components/TransactionResponse.md)> | :heavy_check_mark:                                                                      | Array of transactions matching the query criteria                                       |