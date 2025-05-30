# Users
(*users*)

## Overview

### Available Operations

* [get](#get) - Retrieve the current user
* [update](#update) - Update the current user

## get

Retrieve the current user for the authenticated team.

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



$response = $sdk->users->get(

);

if ($response->object !== null) {
    // handle response
}
```

### Response

**[?Operations\GetCurrentUserResponse](../../Models/Operations/GetCurrentUserResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update the current user for the authenticated team.

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

$request = new Operations\UpdateCurrentUserRequest(
    fullName: 'Jane Doe',
    teamId: 'team-abc123',
    email: 'jane.doe@acme.com',
    avatarUrl: 'https://cdn.midday.ai/avatars/jane-doe.jpg',
    locale: 'en-US',
    weekStartsOnMonday: true,
    timezone: 'America/New_York',
    timeFormat: 24,
    dateFormat: Operations\DateFormatRequest::YyyyDashMMDashdd,
);

$response = $sdk->users->update(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `$request`                                                                                 | [Operations\UpdateCurrentUserRequest](../../Models/Operations/UpdateCurrentUserRequest.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |

### Response

**[?Operations\UpdateCurrentUserResponse](../../Models/Operations/UpdateCurrentUserResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |