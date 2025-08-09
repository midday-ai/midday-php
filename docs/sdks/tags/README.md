# Tags
(*tags*)

## Overview

### Available Operations

* [list](#list) - List all tags
* [create](#create) - Create a new tag
* [get](#get) - Retrieve a tag
* [delete](#delete) - Delete a tag
* [update](#update) - Update a tag

## list

Retrieve a list of tags for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listTags" method="get" path="/tags" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->tags->list(

);

if ($response->tagsResponse !== null) {
    // handle response
}
```

### Response

**[?Operations\ListTagsResponse](../../Models/Operations/ListTagsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a new tag for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="createTag" method="post" path="/tags" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Components;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();

$request = new Components\CreateTag(
    name: 'Important',
);

$response = $sdk->tags->create(
    request: $request
);

if ($response->tagsResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                    | Type                                                         | Required                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `$request`                                                   | [Components\CreateTag](../../Models/Components/CreateTag.md) | :heavy_check_mark:                                           | The request object to use for the request.                   |

### Response

**[?Operations\CreateTagResponse](../../Models/Operations/CreateTagResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a tag by ID for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getTagById" method="get" path="/tags/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->tags->get(
    id: 'b3b7c8e2-1f2a-4c3d-9e4f-5a6b7c8d9e0f'
);

if ($response->tagResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b7c8e2-1f2a-4c3d-9e4f-5a6b7c8d9e0f |

### Response

**[?Operations\GetTagByIdResponse](../../Models/Operations/GetTagByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a tag by ID for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="deleteTag" method="delete" path="/tags/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->tags->delete(
    id: 'b3b7c8e2-1f2a-4c3d-9e4f-5a6b7c8d9e0f'
);

if ($response->statusCode === 200) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b7c8e2-1f2a-4c3d-9e4f-5a6b7c8d9e0f |

### Response

**[?Operations\DeleteTagResponse](../../Models/Operations/DeleteTagResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a tag by ID for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateTag" method="patch" path="/tags/{id}" -->
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

$requestBody = new Operations\UpdateTagRequestBody(
    name: 'Urgent',
);

$response = $sdk->tags->update(
    id: 'b3b7c8e2-1f2a-4c3d-9e4f-5a6b7c8d9e0f',
    requestBody: $requestBody

);

if ($response->tagResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         | Example                                                                             |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `id`                                                                                | *string*                                                                            | :heavy_check_mark:                                                                  | N/A                                                                                 | b3b7c8e2-1f2a-4c3d-9e4f-5a6b7c8d9e0f                                                |
| `requestBody`                                                                       | [?Operations\UpdateTagRequestBody](../../Models/Operations/UpdateTagRequestBody.md) | :heavy_minus_sign:                                                                  | N/A                                                                                 |                                                                                     |

### Response

**[?Operations\UpdateTagResponse](../../Models/Operations/UpdateTagResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |