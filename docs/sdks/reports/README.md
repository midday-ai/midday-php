# Reports

## Overview

### Available Operations

* [revenue](#revenue) - Revenue reports
* [profit](#profit) - Profit reports
* [burnRate](#burnrate) - Burn rate reports
* [runway](#runway) - Runway reports
* [expenses](#expenses) - Expense reports
* [spending](#spending) - Spending reports

## revenue

Revenue reports for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getRevenueReports" method="get" path="/reports/revenue" -->
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



$response = $sdk->reports->revenue(
    from: '2023-01-01',
    to: '2023-12-31',
    currency: 'USD'

);

if ($response->getRevenueResponseSchema !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        | Example            |
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| `from`             | *string*           | :heavy_check_mark: | N/A                | 2023-01-01         |
| `to`               | *string*           | :heavy_check_mark: | N/A                | 2023-12-31         |
| `currency`         | *?string*          | :heavy_minus_sign: | N/A                | USD                |

### Response

**[?Operations\GetRevenueReportsResponse](../../Models/Operations/GetRevenueReportsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## profit

Profit reports for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getProfitReports" method="get" path="/reports/profit" -->
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



$response = $sdk->reports->profit(
    from: '2023-01-01',
    to: '2023-12-31',
    currency: 'USD'

);

if ($response->getProfitResponseSchema !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        | Example            |
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| `from`             | *string*           | :heavy_check_mark: | N/A                | 2023-01-01         |
| `to`               | *string*           | :heavy_check_mark: | N/A                | 2023-12-31         |
| `currency`         | *?string*          | :heavy_minus_sign: | N/A                | USD                |

### Response

**[?Operations\GetProfitReportsResponse](../../Models/Operations/GetProfitReportsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## burnRate

Burn rate reports for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getBurnRateReports" method="get" path="/reports/burn-rate" -->
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



$response = $sdk->reports->burnRate(
    from: '2023-01-01',
    to: '2023-12-31',
    currency: 'USD'

);

if ($response->getBurnRateResponseSchemas !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        | Example            |
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| `from`             | *string*           | :heavy_check_mark: | N/A                | 2023-01-01         |
| `to`               | *string*           | :heavy_check_mark: | N/A                | 2023-12-31         |
| `currency`         | *?string*          | :heavy_minus_sign: | N/A                | USD                |

### Response

**[?Operations\GetBurnRateReportsResponse](../../Models/Operations/GetBurnRateReportsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## runway

Runway reports for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getRunwayReports" method="get" path="/reports/runway" -->
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



$response = $sdk->reports->runway(
    from: '2023-01-01',
    to: '2023-12-31',
    currency: 'USD'

);

if ($response->getRunwayResponseSchema !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        | Example            |
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| `from`             | *string*           | :heavy_check_mark: | N/A                | 2023-01-01         |
| `to`               | *string*           | :heavy_check_mark: | N/A                | 2023-12-31         |
| `currency`         | *?string*          | :heavy_minus_sign: | N/A                | USD                |

### Response

**[?Operations\GetRunwayReportsResponse](../../Models/Operations/GetRunwayReportsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## expenses

Expense reports for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getExpensesReports" method="get" path="/reports/expenses" -->
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



$response = $sdk->reports->expenses(
    from: '2023-01-01',
    to: '2023-12-31',
    currency: 'USD'

);

if ($response->getExpensesResponseSchema !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        | Example            |
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| `from`             | *string*           | :heavy_check_mark: | N/A                | 2023-01-01         |
| `to`               | *string*           | :heavy_check_mark: | N/A                | 2023-12-31         |
| `currency`         | *?string*          | :heavy_minus_sign: | N/A                | USD                |

### Response

**[?Operations\GetExpensesReportsResponse](../../Models/Operations/GetExpensesReportsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## spending

Spending reports for the authenticated team.

### Example Usage

<!-- UsageSnippet language="php" operationID="getSpendingReports" method="get" path="/reports/spending" -->
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



$response = $sdk->reports->spending(
    from: '2023-01-01',
    to: '2023-12-31',
    currency: 'USD'

);

if ($response->spendingResultArray !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        | Example            |
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| `from`             | *string*           | :heavy_check_mark: | N/A                | 2023-01-01         |
| `to`               | *string*           | :heavy_check_mark: | N/A                | 2023-12-31         |
| `currency`         | *?string*          | :heavy_minus_sign: | N/A                | USD                |

### Response

**[?Operations\GetSpendingReportsResponse](../../Models/Operations/GetSpendingReportsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |