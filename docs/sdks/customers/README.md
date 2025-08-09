# Customers
(*customers*)

## Overview

### Available Operations

* [list](#list) - List all customers
* [create](#create) - Create customer
* [get](#get) - Retrieve a customer
* [delete](#delete) - Delete a customer
* [update](#update) - Update a customer

## list

Retrieve a list of customers for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listCustomers" method="get" path="/customers" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->customers->list(
    q: 'acme',
    sort: [
        'name',
        'asc',
    ],
    cursor: 'eyJpZCI6IjEyMyJ9',
    pageSize: 20

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        | Example            |
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| `q`                | *?string*          | :heavy_minus_sign: | N/A                | acme               |
| `sort`             | array<*string*>    | :heavy_minus_sign: | N/A                | [<br/>"name",<br/>"asc"<br/>] |
| `cursor`           | *?string*          | :heavy_minus_sign: | N/A                | eyJpZCI6IjEyMyJ9   |
| `pageSize`         | *?float*           | :heavy_minus_sign: | N/A                | 20                 |

### Response

**[?Operations\ListCustomersResponse](../../Models/Operations/ListCustomersResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a new customer for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="createCustomer" method="post" path="/customers" -->
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

$request = new Operations\CreateCustomerRequest(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4',
    name: 'Acme Corporation',
    email: 'contact@acme.com',
    billingEmail: 'finance@acme.com',
    country: 'United States',
    addressLine1: '123 Main Street',
    addressLine2: 'Suite 400',
    city: 'San Francisco',
    state: 'California',
    zip: '94105',
    phone: '+1-555-123-4567',
    website: 'https://acme.com',
    note: 'Preferred contact method is email. Large enterprise client.',
    vatNumber: 'US123456789',
    countryCode: 'US',
    contact: 'John Smith',
    tags: [
        new Operations\CreateCustomerTagRequest(
            id: 'e7a9c1a2-4c2a-4e7a-9c1a-2b7c1e24c2a4',
            name: 'VIP',
        ),
        new Operations\CreateCustomerTagRequest(
            id: 'f1b2c3d4-5678-4e7a-9c1a-2b7c1e24c2a4',
            name: 'Enterprise',
        ),
    ],
);

$response = $sdk->customers->create(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `$request`                                                                           | [Operations\CreateCustomerRequest](../../Models/Operations/CreateCustomerRequest.md) | :heavy_check_mark:                                                                   | The request object to use for the request.                                           |

### Response

**[?Operations\CreateCustomerResponse](../../Models/Operations/CreateCustomerResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a customer by ID for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getCustomerById" method="get" path="/customers/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->customers->get(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4 |

### Response

**[?Operations\GetCustomerByIdResponse](../../Models/Operations/GetCustomerByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a customer by ID for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="deleteCustomer" method="delete" path="/customers/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        'MIDDAY_API_KEY'
    )
    ->build();



$response = $sdk->customers->delete(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          | Example                              |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `id`                                 | *string*                             | :heavy_check_mark:                   | N/A                                  | b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4 |

### Response

**[?Operations\DeleteCustomerResponse](../../Models/Operations/DeleteCustomerResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a customer by ID for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateCustomer" method="patch" path="/customers/{id}" -->
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

$requestBody = new Operations\UpdateCustomerRequestBody(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4',
    name: 'Acme Corporation',
    email: 'contact@acme.com',
    billingEmail: 'finance@acme.com',
    country: 'United States',
    addressLine1: '123 Main Street',
    addressLine2: 'Suite 400',
    city: 'San Francisco',
    state: 'California',
    zip: '94105',
    phone: '+1-555-123-4567',
    website: 'https://acme.com',
    note: 'Preferred contact method is email. Large enterprise client.',
    vatNumber: 'US123456789',
    countryCode: 'US',
    contact: 'John Smith',
    tags: [
        new Operations\UpdateCustomerTagRequest(
            id: 'e7a9c1a2-4c2a-4e7a-9c1a-2b7c1e24c2a4',
            name: 'VIP',
        ),
        new Operations\UpdateCustomerTagRequest(
            id: 'f1b2c3d4-5678-4e7a-9c1a-2b7c1e24c2a4',
            name: 'Enterprise',
        ),
    ],
);

$response = $sdk->customers->update(
    id: 'b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4',
    requestBody: $requestBody

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   | Example                                                                                       |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `id`                                                                                          | *string*                                                                                      | :heavy_check_mark:                                                                            | N/A                                                                                           | b3b7c1e2-4c2a-4e7a-9c1a-2b7c1e24c2a4                                                          |
| `requestBody`                                                                                 | [?Operations\UpdateCustomerRequestBody](../../Models/Operations/UpdateCustomerRequestBody.md) | :heavy_minus_sign:                                                                            | N/A                                                                                           |                                                                                               |

### Response

**[?Operations\UpdateCustomerResponse](../../Models/Operations/UpdateCustomerResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |