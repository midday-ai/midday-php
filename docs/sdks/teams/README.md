# Teams
(*teams*)

## Overview

### Available Operations

* [list](#list) - List all teams
* [get](#get) - Retrieve a team
* [update](#update) - Update a team
* [members](#members) - List all team members

## list

Retrieve a list of teams for the authenticated user.

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



$response = $sdk->teams->list(

);

if ($response->object !== null) {
    // handle response
}
```

### Response

**[?Operations\ListTeamsResponse](../../Models/Operations/ListTeamsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a team by its ID for the authenticated team.

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



$response = $sdk->teams->get(
    id: '123e4567-e89b-12d3-a456-426614174000'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | 123e4567-e89b-12d3-a456-426614174000 |

### Response

**[?Operations\GetTeamByIdResponse](../../Models/Operations/GetTeamByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a team for the authenticated workspace. If there’s no change, returns it as it is.

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

$requestBody = new Operations\UpdateTeamByIdRequestBody(
    name: 'Acme Corporation',
    email: 'team@acme.com',
    logoUrl: 'https://cdn.midday.ai/logos/acme-corp.png',
    baseCurrency: 'USD',
);

$response = $sdk->teams->update(
    id: '123e4567-e89b-12d3-a456-426614174000',
    requestBody: $requestBody

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   | Example                                                                                       |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `id`                                                                                          | *string*                                                                                      | :heavy_check_mark:                                                                            | N/A                                                                                           | 123e4567-e89b-12d3-a456-426614174000                                                          |
| `requestBody`                                                                                 | [?Operations\UpdateTeamByIdRequestBody](../../Models/Operations/UpdateTeamByIdRequestBody.md) | :heavy_minus_sign:                                                                            | N/A                                                                                           |                                                                                               |

### Response

**[?Operations\UpdateTeamByIdResponse](../../Models/Operations/UpdateTeamByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## members

List all team members for the authenticated team.

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



$response = $sdk->teams->members(
    id: '123e4567-e89b-12d3-a456-426614174000'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | 123e4567-e89b-12d3-a456-426614174000 |

### Response

**[?Operations\ListTeamMembersResponse](../../Models/Operations/ListTeamMembersResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |