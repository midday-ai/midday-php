# Invoices
(*invoices*)

## Overview

### Available Operations

* [list](#list) - List all invoices
* [create](#create) - Create an invoice
* [getInvoicesPaymentStatus](#getinvoicespaymentstatus) - Payment status
* [summary](#summary) - Invoice summary
* [get](#get) - Retrieve a invoice
* [update](#update) - Update an invoice
* [delete](#delete) - Delete a invoice

## list

Retrieve a list of invoices for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="listInvoices" method="get" path="/invoices" -->
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

$request = new Operations\ListInvoicesRequest(
    cursor: '25',
    sort: [
        'createdAt',
        'desc',
    ],
    pageSize: 25,
    q: 'Acme',
    start: '2024-01-01',
    end: '2024-01-31',
    statuses: [
        'paid',
        'unpaid',
    ],
    customers: [
        'customer-uuid-1',
        'customer-uuid-2',
    ],
);

$response = $sdk->invoices->list(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `$request`                                                                       | [Operations\ListInvoicesRequest](../../Models/Operations/ListInvoicesRequest.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |

### Response

**[?Operations\ListInvoicesResponse](../../Models/Operations/ListInvoicesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create an invoice for the authenticated team. The behavior depends on deliveryType: 'create' generates and finalizes the invoice immediately, 'create_and_send' also sends it to the customer, 'scheduled' schedules the invoice for automatic processing at the specified date.

### Example Usage

<!-- UsageSnippet language="php" operationID="createInvoice" method="post" path="/invoices" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Components;
use Midday\Midday\Models\Operations;
use Midday\Midday\Utils;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
    )
    ->build();

$request = new Operations\CreateInvoiceRequest(
    template: new Operations\Template(
        customerLabel: 'Bill To',
        title: 'Invoice',
        fromLabel: 'From',
        invoiceNoLabel: 'Invoice #',
        issueDateLabel: 'Issue Date',
        dueDateLabel: 'Due Date',
        descriptionLabel: 'Description',
        priceLabel: 'Rate',
        quantityLabel: 'Qty',
        totalLabel: 'Amount',
        totalSummaryLabel: 'Total',
        vatLabel: 'VAT',
        taxLabel: 'Sales Tax',
        discountLabel: 'Discount',
        timezone: 'America/Los_Angeles',
        paymentLabel: 'Payment Information',
        noteLabel: 'Notes',
        logoUrl: 'https://example.com/logo.png',
        currency: 'USD',
        dateFormat: 'MM/dd/yyyy',
        includeVat: false,
        includeTax: true,
        includeDiscount: false,
        includeDecimals: true,
        includePdf: true,
        sendCopy: true,
        includeUnits: true,
        includeQr: false,
        taxRate: 8.5,
        vatRate: 0,
        size: Operations\Size::Letter,
        deliveryType: Operations\TemplateDeliveryType::Create,
        locale: 'en-US',
        paymentDetails: new Operations\TemplatePaymentDetails(),
        fromDetails: new Operations\TemplateFromDetails(),
    ),
    fromDetails: new Operations\FromDetails(),
    customerId: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
    paymentDetails: new Operations\PaymentDetails(),
    noteDetails: new Operations\NoteDetails(),
    dueDate: '2024-07-15T23:59:59.000Z',
    issueDate: '2024-06-15T00:00:00.000Z',
    invoiceNumber: 'INV-2024-001',
    logoUrl: 'https://example.com/logo.png',
    tax: 85,
    topBlock: new Operations\TopBlock(),
    bottomBlock: new Operations\BottomBlock(),
    amount: 1085,
    lineItems: [
        new Operations\LineItem(
            quantity: 40,
            price: 75,
            tax: 8.5,
            name: new Operations\Name(),
        ),
        new Operations\LineItem(
            quantity: 20,
            price: 50,
            tax: 8.5,
            name: new Operations\Name(),
        ),
    ],
    deliveryType: Operations\DeliveryType::Create,
    scheduledAt: Utils\Utils::parseDateTime('2024-07-01T09:00:00.000Z'),
);

$response = $sdk->invoices->create(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `$request`                                                                         | [Operations\CreateInvoiceRequest](../../Models/Operations/CreateInvoiceRequest.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |

### Response

**[?Operations\CreateInvoiceResponse](../../Models/Operations/CreateInvoiceResponse.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| Errors\CreateInvoiceBadRequestException | 400                                     | application/json                        |
| Errors\CreateInvoiceNotFoundException   | 404                                     | application/json                        |
| Errors\ConflictException                | 409                                     | application/json                        |
| Errors\CreateInvoiceInternalServerError | 500                                     | application/json                        |
| Errors\APIException                     | 4XX, 5XX                                | \*/\*                                   |

## getInvoicesPaymentStatus

Get payment status for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/invoices/payment-status" method="get" path="/invoices/payment-status" -->
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



$response = $sdk->invoices->getInvoicesPaymentStatus(

);

if ($response->object !== null) {
    // handle response
}
```

### Response

**[?Operations\GetInvoicesPaymentStatusResponse](../../Models/Operations/GetInvoicesPaymentStatusResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## summary

Get summary of invoices for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getInvoiceSummary" method="get" path="/invoices/summary" -->
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



$response = $sdk->invoices->summary(
    status: Operations\GetInvoiceSummaryStatus::Paid
);

if ($response->responseBodies !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               | Example                                                                                   |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `status`                                                                                  | [?Operations\GetInvoiceSummaryStatus](../../Models/Operations/GetInvoiceSummaryStatus.md) | :heavy_minus_sign:                                                                        | Filter summary by invoice status                                                          | paid                                                                                      |

### Response

**[?Operations\GetInvoiceSummaryResponse](../../Models/Operations/GetInvoiceSummaryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a invoice by its unique identifier for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getInvoiceById" method="get" path="/invoices/{id}" -->
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



$response = $sdk->invoices->get(
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

**[?Operations\GetInvoiceByIdResponse](../../Models/Operations/GetInvoiceByIdResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update an invoice by its unique identifier for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="updateInvoice" method="put" path="/invoices/{id}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Components;
use Midday\Midday\Models\Operations;
use Midday\Midday\Utils;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
    )
    ->build();

$requestBody = new Operations\UpdateInvoiceRequestBody(
    status: Operations\UpdateInvoiceStatusRequest::Paid,
    paidAt: Utils\Utils::parseDateTime('2024-06-15T12:00:00.000Z'),
    internalNote: 'Payment received via bank transfer',
);

$response = $sdk->invoices->update(
    id: '<id>',
    requestBody: $requestBody

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `id`                                                                                        | *string*                                                                                    | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `requestBody`                                                                               | [?Operations\UpdateInvoiceRequestBody](../../Models/Operations/UpdateInvoiceRequestBody.md) | :heavy_minus_sign:                                                                          | N/A                                                                                         |

### Response

**[?Operations\UpdateInvoiceResponse](../../Models/Operations/UpdateInvoiceResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete an invoice by its unique identifier for the authenticated team. Only invoices with status 'draft' or 'canceled' can be deleted directly. If the invoice is not in one of these statuses, update its status to 'canceled' before attempting deletion.

### Example Usage

<!-- UsageSnippet language="php" operationID="deleteInvoice" method="delete" path="/invoices/{id}" -->
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



$response = $sdk->invoices->delete(
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

**[?Operations\DeleteInvoiceResponse](../../Models/Operations/DeleteInvoiceResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |