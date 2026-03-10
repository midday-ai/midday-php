# PostOAuthTokenResponseBody

Token exchange successful


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `accessToken`                                                | *string*                                                     | :heavy_check_mark:                                           | Access token for API requests                                | mid_access_token_abcdef123456789                             |
| `tokenType`                                                  | [Operations\TokenType](../../Models/Operations/TokenType.md) | :heavy_check_mark:                                           | Token type, always 'Bearer'                                  | Bearer                                                       |
| `expiresIn`                                                  | *float*                                                      | :heavy_check_mark:                                           | Token expiration time in seconds                             | 3600                                                         |
| `refreshToken`                                               | *string*                                                     | :heavy_check_mark:                                           | Refresh token for obtaining new access tokens                | mid_refresh_token_abcdef123456789                            |
| `scope`                                                      | *string*                                                     | :heavy_check_mark:                                           | Space-separated list of granted scopes                       | transactions.read invoices.read                              |