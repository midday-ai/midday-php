# TrackerEntries
(*trackerEntries*)

## Overview

### Available Operations

* [list](#list) - List all tracker entries
* [create](#create) - Create a tracker entry
* [createBulk](#createbulk) - Create multiple tracker entries
* [delete](#delete) - Delete a tracker entry
* [update](#update) - Update a tracker entry

## list

List all tracker entries for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listTrackerEntries" method="get" path="/tracker-entries" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->trackerEntries->list(
    from: '2024-04-01',
    to: '2024-04-30',
    projectId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2'

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `from`                               | *string*                             | :heavy_check_mark:                   | N/A                                  | 2024-04-01                           |
| `to`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | 2024-04-30                           |
| `projectId`                          | *?string*                            | :heavy_minus_sign:                   | N/A                                  | b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2 |

### Response

**[?Operations\ListTrackerEntriesResponse](../../Models/Operations/ListTrackerEntriesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a tracker entry for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="createTrackerEntry" method="post" path="/tracker-entries" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Operations;
use Midday\Midday\Utils;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();

$request = new Operations\CreateTrackerEntryRequest(
    start: Utils\Utils::parseDateTime('2024-04-15T09:00:00.000Z'),
    stop: Utils\Utils::parseDateTime('2024-04-15T17:00:00.000Z'),
    dates: [
        '2024-04-15',
        '2024-04-16',
    ],
    assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
    projectId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
    description: 'Worked on implementing user authentication feature',
    duration: 28800,
);

$response = $sdk->trackerEntries->create(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `$request`                                                                                   | [Operations\CreateTrackerEntryRequest](../../Models/Operations/CreateTrackerEntryRequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |

### Response

**[?Operations\CreateTrackerEntryResponse](../../Models/Operations/CreateTrackerEntryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## createBulk

Create multiple tracker entries in a single request for efficient data migration.

### Example Usage

<!-- UsageSnippet language="php" operationID="createTrackerEntriesBulk" method="post" path="/tracker-entries/bulk" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Operations;
use Midday\Midday\Utils;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();

$request = new Operations\CreateTrackerEntriesBulkRequest(
    entries: [
        new Operations\Entry(
            start: Utils\Utils::parseDateTime('2024-04-15T09:00:00.000Z'),
            stop: Utils\Utils::parseDateTime('2024-04-15T17:00:00.000Z'),
            dates: [
                '2024-04-15',
            ],
            assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
            projectId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
            description: 'Working on authentication feature',
            duration: 28800,
        ),
        new Operations\Entry(
            start: Utils\Utils::parseDateTime('2024-04-16T09:00:00.000Z'),
            stop: Utils\Utils::parseDateTime('2024-04-16T17:00:00.000Z'),
            dates: [
                '2024-04-16',
            ],
            assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
            projectId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
            description: 'Working on dashboard feature',
            duration: 28800,
        ),
    ],
);

$response = $sdk->trackerEntries->createBulk(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                               | [Operations\CreateTrackerEntriesBulkRequest](../../Models/Operations/CreateTrackerEntriesBulkRequest.md) | :heavy_check_mark:                                                                                       | The request object to use for the request.                                                               |

### Response

**[?Operations\CreateTrackerEntriesBulkResponse](../../Models/Operations/CreateTrackerEntriesBulkResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a tracker entry for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="deleteTrackerEntry" method="delete" path="/tracker-entries/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->trackerEntries->delete(
    id: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2 |

### Response

**[?Operations\DeleteTrackerEntryResponse](../../Models/Operations/DeleteTrackerEntryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a tracker entry for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateTrackerEntry" method="patch" path="/tracker-entries/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Operations;
use Midday\Midday\Utils;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();

$requestBody = new Operations\UpdateTrackerEntryRequestBody(
    start: Utils\Utils::parseDateTime('2024-04-15T09:00:00.000Z'),
    stop: Utils\Utils::parseDateTime('2024-04-15T17:00:00.000Z'),
    dates: [
        '2024-04-15',
        '2024-04-16',
    ],
    assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
    projectId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
    description: 'Worked on implementing user authentication feature',
    duration: 28800,
);

$response = $sdk->trackerEntries->update(
    id: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
    requestBody: $requestBody

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           | Example                                                                                               |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `id`                                                                                                  | *string*                                                                                              | :heavy_check_mark:                                                                                    | N/A                                                                                                   | b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2                                                                  |
| `requestBody`                                                                                         | [?Operations\UpdateTrackerEntryRequestBody](../../Models/Operations/UpdateTrackerEntryRequestBody.md) | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |                                                                                                       |

### Response

**[?Operations\UpdateTrackerEntryResponse](../../Models/Operations/UpdateTrackerEntryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |