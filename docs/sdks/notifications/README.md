# Notifications
(*notifications*)

## Overview

### Available Operations

* [list](#list) - List all notifications
* [updateStatus](#updatestatus) - Update notification status
* [updateAllStatus](#updateallstatus) - Update status of all notifications

## list

Retrieve a list of notifications for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listNotifications" method="get" path="/notifications" -->
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

$request = new Operations\ListNotificationsRequest(
    cursor: '20',
    pageSize: 20,
    status: [
        Operations\ListNotificationsStatusEnum2::Unread,
        Operations\ListNotificationsStatusEnum2::Read,
    ],
    userId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
    priority: 5,
    maxPriority: 3,
);

$response = $sdk->notifications->list(
    request: $request
);

if ($response->notificationsResponseSchema !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `$request`                                                                                 | [Operations\ListNotificationsRequest](../../Models/Operations/ListNotificationsRequest.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |

### Response

**[?Operations\ListNotificationsResponse](../../Models/Operations/ListNotificationsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## updateStatus

Update the status of a specific notification.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateNotificationStatus" method="patch" path="/notifications/{notificationId}/status" -->
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

$requestBody = new Operations\UpdateNotificationStatusRequestBody(
    status: Operations\UpdateNotificationStatusStatus::Read,
);

$response = $sdk->notifications->updateStatus(
    notificationId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
    requestBody: $requestBody

);

if ($response->notificationResponseSchema !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                         | Type                                                                                                              | Required                                                                                                          | Description                                                                                                       | Example                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `notificationId`                                                                                                  | *string*                                                                                                          | :heavy_check_mark:                                                                                                | N/A                                                                                                               | b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2                                                                              |
| `requestBody`                                                                                                     | [?Operations\UpdateNotificationStatusRequestBody](../../Models/Operations/UpdateNotificationStatusRequestBody.md) | :heavy_minus_sign:                                                                                                | N/A                                                                                                               |                                                                                                                   |

### Response

**[?Operations\UpdateNotificationStatusResponse](../../Models/Operations/UpdateNotificationStatusResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## updateAllStatus

Update the status of all notifications for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateAllNotificationsStatus" method="post" path="/notifications/update-all-status" -->
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

$request = new Components\UpdateAllNotificationsStatusSchema(
    status: Components\UpdateAllNotificationsStatusSchemaStatus::Read,
);

$response = $sdk->notifications->updateAllStatus(
    request: $request
);

if ($response->updateAllNotificationsStatusResponseSchema !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                      | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                     | [Components\UpdateAllNotificationsStatusSchema](../../Models/Components/UpdateAllNotificationsStatusSchema.md) | :heavy_check_mark:                                                                                             | The request object to use for the request.                                                                     |

### Response

**[?Operations\UpdateAllNotificationsStatusResponse](../../Models/Operations/UpdateAllNotificationsStatusResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |