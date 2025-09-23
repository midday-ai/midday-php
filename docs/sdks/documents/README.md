# Documents
(*documents*)

## Overview

### Available Operations

* [list](#list) - List all documents
* [get](#get) - Retrieve a document
* [delete](#delete) - Delete a document
* [getPreSignedUrl](#getpresignedurl) - Generate pre-signed URL for document

## list

Retrieve a list of documents for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listDocuments" method="get" path="/documents" -->
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

$request = new Operations\ListDocumentsRequest(
    cursor: '20',
    pageSize: 20,
    q: 'invoice',
    tags: [
        'tag1',
        'tag2',
    ],
);

$response = $sdk->documents->list(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `$request`                                                                         | [Operations\ListDocumentsRequest](../../Models/Operations/ListDocumentsRequest.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |

### Response

**[?Operations\ListDocumentsResponse](../../Models/Operations/ListDocumentsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a document by its unique identifier for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getDocumentById" method="get" path="/documents/{id}" -->
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



$response = $sdk->documents->get(
    id: '<id>'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `id`               | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetDocumentByIdResponse](../../Models/Operations/GetDocumentByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a document by its unique identifier for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="deleteDocument" method="delete" path="/documents/{id}" -->
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



$response = $sdk->documents->delete(
    id: '<id>'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `id`               | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\DeleteDocumentResponse](../../Models/Operations/DeleteDocumentResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getPreSignedUrl

Generate a pre-signed URL for accessing a document. The URL is valid for 60 seconds and allows secure temporary access to the document file.

### Example Usage

<!-- UsageSnippet language="php" operationID="getDocumentPreSignedUrl" method="post" path="/documents/{id}/presigned-url" -->
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



$response = $sdk->documents->getPreSignedUrl(
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

**[?Operations\GetDocumentPreSignedUrlResponse](../../Models/Operations/GetDocumentPreSignedUrlResponse.md)**

### Errors

| Error Type                                        | Status Code                                       | Content Type                                      |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| Errors\GetDocumentPreSignedUrlBadRequestException | 400                                               | application/json                                  |
| Errors\GetDocumentPreSignedUrlNotFoundException   | 404                                               | application/json                                  |
| Errors\GetDocumentPreSignedUrlInternalServerError | 500                                               | application/json                                  |
| Errors\APIException                               | 4XX, 5XX                                          | \*/\*                                             |