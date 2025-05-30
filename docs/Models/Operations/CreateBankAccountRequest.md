# CreateBankAccountRequest

Schema for creating a new bank account.


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        | Example                                            |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `name`                                             | *string*                                           | :heavy_check_mark:                                 | The name of the bank account.                      | Checking Account                                   |
| `currency`                                         | *?string*                                          | :heavy_minus_sign:                                 | The currency code for the bank account (ISO 4217). | USD                                                |
| `manual`                                           | *?bool*                                            | :heavy_minus_sign:                                 | Whether the bank account is a manual account.      | false                                              |