# TrackerEntries
(*trackerEntries*)

## Overview

### Available Operations

* [list](#list) - List all tracker entries

## list

List all tracker entries for the authenticated team.

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