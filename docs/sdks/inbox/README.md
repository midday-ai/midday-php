# Inbox
(*inbox*)

## Overview

### Available Operations

* [list](#list) - List all inbox items
* [get](#get) - Retrieve a inbox item
* [delete](#delete) - Delete a inbox item
* [update](#update) - Update a inbox item

## list

Retrieve a list of inbox items for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listInboxItems" method="get" path="/inbox" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->inbox->list(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `$request`                                                                           | [Operations\ListInboxItemsRequest](../../Models/Operations/ListInboxItemsRequest.md) | :heavy_check_mark:                                                                   | The request object to use for the request.                                           |

### Response

**[?Operations\ListInboxItemsResponse](../../Models/Operations/ListInboxItemsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a inbox item by its unique identifier for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getInboxItemById" method="get" path="/inbox/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->inbox->get(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4 |

### Response

**[?Operations\GetInboxItemByIdResponse](../../Models/Operations/GetInboxItemByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a inbox item by its unique identifier for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="deleteInboxItem" method="delete" path="/inbox/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->inbox->delete(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4 |

### Response

**[?Operations\DeleteInboxItemResponse](../../Models/Operations/DeleteInboxItemResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update fields of an inbox item by its unique identifier for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateInboxItem" method="patch" path="/inbox/{id}" -->
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

$requestBody = new Operations\UpdateInboxItemRequestBody();

$response = $sdk->inbox->update(
    id: '<id>',
    requestBody: $requestBody

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `id`                                                                                           | *string*                                                                                       | :heavy_check_mark:                                                                             | N/A                                                                                            |
| `requestBody`                                                                                  | [Operations\UpdateInboxItemRequestBody](../../Models/Operations/UpdateInboxItemRequestBody.md) | :heavy_check_mark:                                                                             | N/A                                                                                            |

### Response

**[?Operations\UpdateInboxItemResponse](../../Models/Operations/UpdateInboxItemResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |