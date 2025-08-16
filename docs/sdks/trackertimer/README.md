# TrackerTimer
(*trackerTimer*)

## Overview

### Available Operations

* [startTimer](#starttimer) - Start a timer
* [stopTimer](#stoptimer) - Stop a timer
* [getCurrentTimer](#getcurrenttimer) - Get current timer
* [getTimerStatus](#gettimerstatus) - Get timer status

## startTimer

Start a new timer or continue from a paused entry.

### Example Usage

<!-- UsageSnippet language="php" operationID="startTimer" method="post" path="/tracker-entries/timer/start" -->
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

$request = new Operations\StartTimerRequest(
    projectId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
    assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
    description: 'Working on implementing timer feature',
    start: Utils\Utils::parseDateTime('2024-04-15T09:00:00.000Z'),
    continueFromEntry: 'c4d5e6f7-2a3b-4c5d-8e9f-3a4b5c6d7e8f',
);

$response = $sdk->trackerTimer->startTimer(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `$request`                                                                   | [Operations\StartTimerRequest](../../Models/Operations/StartTimerRequest.md) | :heavy_check_mark:                                                           | The request object to use for the request.                                   |

### Response

**[?Operations\StartTimerResponse](../../Models/Operations/StartTimerResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## stopTimer

Stop the current running timer or a specific timer entry.

### Example Usage

<!-- UsageSnippet language="php" operationID="stopTimer" method="post" path="/tracker-entries/timer/stop" -->
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

$request = new Operations\StopTimerRequest(
    entryId: 'b3b6e2c2-1f2a-4e3b-9c1d-2a4b6e2c21f2',
    assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
    stop: Utils\Utils::parseDateTime('2024-04-15T17:00:00.000Z'),
);

$response = $sdk->trackerTimer->stopTimer(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `$request`                                                                 | [Operations\StopTimerRequest](../../Models/Operations/StopTimerRequest.md) | :heavy_check_mark:                                                         | The request object to use for the request.                                 |

### Response

**[?Operations\StopTimerResponse](../../Models/Operations/StopTimerResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getCurrentTimer

Get the currently running timer for the authenticated user.

### Example Usage

<!-- UsageSnippet language="php" operationID="getCurrentTimer" method="get" path="/tracker-entries/timer/current" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->trackerTimer->getCurrentTimer(
    assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `assignedId`                         | *?string*                            | :heavy_minus_sign:                   | N/A                                  | a1b2c3d4-e5f6-7890-abcd-ef1234567890 |

### Response

**[?Operations\GetCurrentTimerResponse](../../Models/Operations/GetCurrentTimerResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getTimerStatus

Get timer status including elapsed time for the authenticated user.

### Example Usage

<!-- UsageSnippet language="php" operationID="getTimerStatus" method="get" path="/tracker-entries/timer/status" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->trackerTimer->getTimerStatus(
    assignedId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `assignedId`                         | *?string*                            | :heavy_minus_sign:                   | N/A                                  | a1b2c3d4-e5f6-7890-abcd-ef1234567890 |

### Response

**[?Operations\GetTimerStatusResponse](../../Models/Operations/GetTimerStatusResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |