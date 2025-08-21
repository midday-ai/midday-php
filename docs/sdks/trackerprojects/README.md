# TrackerProjects
(*trackerProjects*)

## Overview

### Available Operations

* [list](#list) - List all tracker projects
* [create](#create) - Create a tracker project
* [get](#get) - Retrieve a tracker project
* [delete](#delete) - Delete a tracker project
* [update](#update) - Update a tracker project

## list

List all tracker projects for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listTrackerProjects" method="get" path="/tracker-projects" -->
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

$request = new Operations\ListTrackerProjectsRequest(
    cursor: 'eyJpZCI6IjEyMyJ9',
    pageSize: 20,
    q: 'website',
    start: '2024-04-01',
    end: '2024-04-30',
    status: Operations\ListTrackerProjectsStatus::InProgress,
    customers: [
        'customer-1',
        'customer-2',
    ],
    tags: [
        'tag-1',
        'tag-2',
    ],
    sort: [
        '-createdAt',
        'name',
    ],
);

$response = $sdk->trackerProjects->list(
    request: $request
);

if ($response->trackerProjectsResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `$request`                                                                                     | [Operations\ListTrackerProjectsRequest](../../Models/Operations/ListTrackerProjectsRequest.md) | :heavy_check_mark:                                                                             | The request object to use for the request.                                                     |

### Response

**[?Operations\ListTrackerProjectsResponse](../../Models/Operations/ListTrackerProjectsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a tracker project for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="createTrackerProject" method="post" path="/tracker-projects" -->
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

$request = new Operations\CreateTrackerProjectRequest(
    name: 'New Project',
    billable: true,
);

$response = $sdk->trackerProjects->create(
    request: $request
);

if ($response->trackerProjectResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `$request`                                                                                       | [Operations\CreateTrackerProjectRequest](../../Models/Operations/CreateTrackerProjectRequest.md) | :heavy_check_mark:                                                                               | The request object to use for the request.                                                       |

### Response

**[?Operations\CreateTrackerProjectResponse](../../Models/Operations/CreateTrackerProjectResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a tracker project for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getTrackerProjectById" method="get" path="/tracker-projects/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->trackerProjects->get(
    id: 'b7e6c8e2-1f2a-4c3b-9e2d-1a2b3c4d5e6f'
);

if ($response->trackerProjectResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b7e6c8e2-1f2a-4c3b-9e2d-1a2b3c4d5e6f |

### Response

**[?Operations\GetTrackerProjectByIdResponse](../../Models/Operations/GetTrackerProjectByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a tracker project for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="deleteTrackerProject" method="delete" path="/tracker-projects/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->trackerProjects->delete(
    id: 'b7e6c8e2-1f2a-4c3b-9e2d-1a2b3c4d5e6f'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b7e6c8e2-1f2a-4c3b-9e2d-1a2b3c4d5e6f |

### Response

**[?Operations\DeleteTrackerProjectResponse](../../Models/Operations/DeleteTrackerProjectResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a tracker project for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateTrackerProject" method="patch" path="/tracker-projects/{id}" -->
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

$requestBody = new Operations\UpdateTrackerProjectRequestBody(
    name: 'Website Redesign',
    description: 'Complete redesign of the company website with modern UI/UX and improved performance',
    estimate: 120,
    billable: true,
    rate: 75,
    currency: 'USD',
    status: Operations\UpdateTrackerProjectStatus::InProgress,
    customerId: 'a1b2c3d4-e5f6-7890-abcd-1234567890ef',
    tags: [
        new Operations\UpdateTrackerProjectTag(
            id: 'f1e2d3c4-b5a6-7890-1234-567890abcdef',
            value: 'Design',
        ),
        new Operations\UpdateTrackerProjectTag(
            id: 'e2d3c4b5-a6f1-7890-1234-567890abcdef',
            value: 'Frontend',
        ),
    ],
);

$response = $sdk->trackerProjects->update(
    id: 'b7e6c8e2-1f2a-4c3b-9e2d-1a2b3c4d5e6f',
    requestBody: $requestBody

);

if ($response->trackerProjectResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               | Example                                                                                                   |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                      | *string*                                                                                                  | :heavy_check_mark:                                                                                        | N/A                                                                                                       | b7e6c8e2-1f2a-4c3b-9e2d-1a2b3c4d5e6f                                                                      |
| `requestBody`                                                                                             | [?Operations\UpdateTrackerProjectRequestBody](../../Models/Operations/UpdateTrackerProjectRequestBody.md) | :heavy_minus_sign:                                                                                        | N/A                                                                                                       |                                                                                                           |

### Response

**[?Operations\UpdateTrackerProjectResponse](../../Models/Operations/UpdateTrackerProjectResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |