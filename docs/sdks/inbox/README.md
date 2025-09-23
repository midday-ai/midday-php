# Inbox
(*inbox*)

## Overview

### Available Operations

* [list](#list) - List all inbox items
* [get](#get) - Retrieve a inbox item
* [delete](#delete) - Delete a inbox item
* [update](#update) - Update a inbox item
* [getPreSignedUrl](#getpresignedurl) - Generate pre-signed URL for inbox attachment

## list

Retrieve a list of inbox items for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listInboxItems" method="get" path="/inbox" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Components;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
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
use Midday\Midday\Models\Components;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
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
use Midday\Midday\Models\Components;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
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
use Midday\Midday\Models\Components;
use Midday\Midday\Models\Operations;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
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

## getPreSignedUrl

Generate a pre-signed URL for accessing an inbox attachment. The URL is valid for 60 seconds and allows secure temporary access to the attachment file.

### Example Usage

<!-- UsageSnippet language="php" operationID="getInboxPreSignedUrl" method="post" path="/inbox/{id}/presigned-url" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Components;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
    )
    ->build();



$response = $sdk->inbox->getPreSignedUrl(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4',
    download: true

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4 |
| `download`                           | *?bool*                              | :heavy_minus_sign:                   | N/A                                  | true                                 |

### Response

**[?Operations\GetInboxPreSignedUrlResponse](../../Models/Operations/GetInboxPreSignedUrlResponse.md)**

### Errors

| Error Type                                     | Status Code                                    | Content Type                                   |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| Errors\GetInboxPreSignedUrlBadRequestException | 400                                            | application/json                               |
| Errors\GetInboxPreSignedUrlNotFoundException   | 404                                            | application/json                               |
| Errors\GetInboxPreSignedUrlInternalServerError | 500                                            | application/json                               |
| Errors\APIException                            | 4XX, 5XX                                       | \*/\*                                          |