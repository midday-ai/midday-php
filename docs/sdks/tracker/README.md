# Tracker
(*tracker*)

## Overview

### Available Operations

* [delete](#delete) - Delete a tracker entry

## delete

Delete a tracker entry for the authenticated team.

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



$response = $sdk->tracker->delete(
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