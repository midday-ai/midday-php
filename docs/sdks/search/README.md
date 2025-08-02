# Search
(*search*)

## Overview

### Available Operations

* [search](#search) - Search

## search

Search across all data, invoices, documents, customers, transactions, and more.

### Example Usage

<!-- UsageSnippet language="php" operationID="search" method="get" path="/search" -->
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

$request = new Operations\SearchRequest(
    searchTerm: 'Acme',
    language: 'en',
);

$response = $sdk->search->search(
    request: $request
);

if ($response->responseBodies !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `$request`                                                           | [Operations\SearchRequest](../../Models/Operations/SearchRequest.md) | :heavy_check_mark:                                                   | The request object to use for the request.                           |

### Response

**[?Operations\SearchResponse](../../Models/Operations/SearchResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |