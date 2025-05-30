# Transactions
(*transactions*)

## Overview

### Available Operations

* [list](#list) - List all transactions
* [create](#create) - Create a transaction
* [get](#get) - Retrieve a transaction
* [delete](#delete) - Delete a transaction
* [update](#update) - Update a transaction
* [createMany](#createmany) - Bulk create transactions
* [deleteMany](#deletemany) - Bulk delete transactions
* [updateMany](#updatemany) - Bulk update transactions

## list

Retrieve a list of transactions for the authenticated team.

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

$request = new Operations\ListTransactionsRequest(
    cursor: 'eyJpZCI6IjEyMyJ9',
    sort: [
        'date',
        'desc',
    ],
    pageSize: 50,
    q: 'office supplies',
    categories: [
        'office-supplies',
        'travel',
    ],
    tags: [
        'tag-1',
        'tag-2',
    ],
    start: '2024-04-01T00:00:00.000Z',
    end: '2024-04-30T23:59:59.999Z',
    accounts: [
        'account-1',
        'account-2',
    ],
    assignees: [
        'user-1',
        'user-2',
    ],
    statuses: [
        'pending',
        'completed',
    ],
    recurring: [
        'monthly',
        'annually',
    ],
    attachments: Operations\Attachments::Include,
    amountRange: [
        100,
        1000,
    ],
    amount: [
        '150.75',
        '299.99',
    ],
    type: Operations\ListTransactionsType::Expense,
);

$response = $sdk->transactions->list(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                | Type                                                                                     | Required                                                                                 | Description                                                                              |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `$request`                                                                               | [Operations\ListTransactionsRequest](../../Models/Operations/ListTransactionsRequest.md) | :heavy_check_mark:                                                                       | The request object to use for the request.                                               |

### Response

**[?Operations\ListTransactionsResponse](../../Models/Operations/ListTransactionsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a transaction

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

$request = new Operations\CreateTransactionRequest(
    name: '<value>',
    amount: 5744.12,
    currency: 'Forint',
    date: '2024-01-12',
    bankAccountId: '<id>',
);

$response = $sdk->transactions->create(
    request: $request
);

if ($response->transactionResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `$request`                                                                                 | [Operations\CreateTransactionRequest](../../Models/Operations/CreateTransactionRequest.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |

### Response

**[?Operations\CreateTransactionResponse](../../Models/Operations/CreateTransactionResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a transaction by its ID for the authenticated team.

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



$response = $sdk->transactions->get(
    id: '391723c9-de99-4039-b8e2-4fa5bbdf9480'
);

if ($response->transactionResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `id`               | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetTransactionByIdResponse](../../Models/Operations/GetTransactionByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a transaction for the authenticated team. Only manually created transactions can be deleted via this endpoint or the form. Transactions inserted by bank connections cannot be deleted, but can be excluded by updating the status.

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



$response = $sdk->transactions->delete(
    id: '92766ee2-a2bc-44aa-97af-6891695fc321'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `id`               | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\DeleteTransactionResponse](../../Models/Operations/DeleteTransactionResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a transaction for the authenticated team. If there's no change, returns it as it is.

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

$requestBody = new Operations\UpdateTransactionRequestBody();

$response = $sdk->transactions->update(
    id: 'f0c1d0ef-5679-4c1b-9698-2c64e97e8c1d',
    requestBody: $requestBody

);

if ($response->transactionResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `id`                                                                                                | *string*                                                                                            | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `requestBody`                                                                                       | [?Operations\UpdateTransactionRequestBody](../../Models/Operations/UpdateTransactionRequestBody.md) | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |

### Response

**[?Operations\UpdateTransactionResponse](../../Models/Operations/UpdateTransactionResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## createMany

Bulk create transactions for the authenticated team.

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

$request = [
    new Operations\RequestBody(
        name: '<value>',
        amount: 6684.51,
        currency: 'Libyan Dinar',
        date: '2024-05-10',
        bankAccountId: '<id>',
    ),
];

$response = $sdk->transactions->createMany(
    request: $request
);

if ($response->transactionResponses !== null) {
    // handle response
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `$request`                                 | [array<Operations\RequestBody>](../../.md) | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[?Operations\CreateTransactionsResponse](../../Models/Operations/CreateTransactionsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## deleteMany

Bulk delete transactions for the authenticated team. Only manually created transactions can be deleted via this endpoint or the form. Transactions inserted by bank connections cannot be deleted, but can be excluded by updating the status.

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

$request = [
    'cc0db9ee-175c-4562-914a-20c38d2dc310',
];

$response = $sdk->transactions->deleteMany(
    request: $request
);

if ($response->responseBodies !== null) {
    // handle response
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `$request`                                 | [array<string>](../../.md)                 | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[?Operations\DeleteTransactionsResponse](../../Models/Operations/DeleteTransactionsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## updateMany

Bulk update transactions for the authenticated team. If there's no change, returns it as it is.

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

$request = new Operations\UpdateTransactionsRequest(
    ids: [
        '<value>',
    ],
);

$response = $sdk->transactions->updateMany(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `$request`                                                                                   | [Operations\UpdateTransactionsRequest](../../Models/Operations/UpdateTransactionsRequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |

### Response

**[?Operations\UpdateTransactionsResponse](../../Models/Operations/UpdateTransactionsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |