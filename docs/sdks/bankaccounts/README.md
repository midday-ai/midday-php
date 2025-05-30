# BankAccounts
(*bankAccounts*)

## Overview

### Available Operations

* [list](#list) - List all bank accounts
* [create](#create) - Create a bank account
* [get](#get) - Retrieve a bank account
* [delete](#delete) - Delete a bank account
* [update](#update) - Update a bank account

## list

Retrieve a list of bank accounts for the authenticated team.

### Example Usage

```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->bankAccounts->list(
    enabled: false,
    manual: false

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `enabled`          | *?bool*            | :heavy_minus_sign: | N/A                |
| `manual`           | *?bool*            | :heavy_minus_sign: | N/A                |

### Response

**[?Operations\ListBankAccountsResponse](../../Models/Operations/ListBankAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a new bank account for the authenticated team.

### Example Usage

```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Operations;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();

$request = new Operations\CreateBankAccountRequest(
    name: 'Checking Account',
    currency: 'USD',
    manual: false,
);

$response = $sdk->bankAccounts->create(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `$request`                                                                                 | [Operations\CreateBankAccountRequest](../../Models/Operations/CreateBankAccountRequest.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |

### Response

**[?Operations\CreateBankAccountResponse](../../Models/Operations/CreateBankAccountResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a bank account by ID for the authenticated team.

### Example Usage

```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->bankAccounts->get(
    id: 'b7e6c2a0-1f2d-4c3b-9a8e-123456789abc'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b7e6c2a0-1f2d-4c3b-9a8e-123456789abc |

### Response

**[?Operations\GetBankAccountByIdResponse](../../Models/Operations/GetBankAccountByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a bank account by ID for the authenticated team.

### Example Usage

```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->bankAccounts->delete(
    id: 'b7e6c2a0-1f2d-4c3b-9a8e-123456789abc'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b7e6c2a0-1f2d-4c3b-9a8e-123456789abc |

### Response

**[?Operations\DeleteBankAccountResponse](../../Models/Operations/DeleteBankAccountResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a bank account by ID for the authenticated team.

### Example Usage

```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Operations;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();

$requestBody = new Operations\UpdateBankAccountRequestBody(
    id: 'b7e6c2a0-1f2d-4c3b-9a8e-123456789abc',
    name: 'Checking Account',
    enabled: true,
    balance: 1500.75,
    type: Operations\UpdateBankAccountType::Depository,
);

$response = $sdk->bankAccounts->update(
    id: 'b7e6c2a0-1f2d-4c3b-9a8e-123456789abc',
    requestBody: $requestBody

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                               | Type                                                                                                                                    | Required                                                                                                                                | Description                                                                                                                             | Example                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                    | *string*                                                                                                                                | :heavy_check_mark:                                                                                                                      | N/A                                                                                                                                     | b7e6c2a0-1f2d-4c3b-9a8e-123456789abc                                                                                                    |
| `requestBody`                                                                                                                           | [?Operations\UpdateBankAccountRequestBody](../../Models/Operations/UpdateBankAccountRequestBody.md)                                     | :heavy_minus_sign:                                                                                                                      | N/A                                                                                                                                     | {<br/>"id": "b7e6c2a0-1f2d-4c3b-9a8e-123456789abc",<br/>"name": "Checking Account",<br/>"enabled": true,<br/>"balance": 1500.75,<br/>"type": "depository"<br/>} |

### Response

**[?Operations\UpdateBankAccountResponse](../../Models/Operations/UpdateBankAccountResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |