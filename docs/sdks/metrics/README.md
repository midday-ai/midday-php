# Metrics
(*metrics*)

## Overview

### Available Operations

* [revenue](#revenue) - Revenue metrics
* [profit](#profit) - Profit metrics
* [burnRate](#burnrate) - Burn rate metrics
* [runway](#runway) - Runway metrics
* [expenses](#expenses) - Expense metrics
* [spending](#spending) - Spending metrics

## revenue

Revenue metrics for the authenticated team.

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



$response = $sdk->metrics->revenue(
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

**[?Operations\GetRevenueMetricsResponse](../../Models/Operations/GetRevenueMetricsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## profit

Profit metrics for the authenticated team.

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



$response = $sdk->metrics->profit(
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

**[?Operations\GetProfitMetricsResponse](../../Models/Operations/GetProfitMetricsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## burnRate

Burn rate metrics for the authenticated team.

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



$response = $sdk->metrics->burnRate(
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

**[?Operations\GetBurnRateMetricsResponse](../../Models/Operations/GetBurnRateMetricsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## runway

Runway metrics for the authenticated team.

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



$response = $sdk->metrics->runway(
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

**[?Operations\GetRunwayMetricsResponse](../../Models/Operations/GetRunwayMetricsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## expenses

Expense metrics for the authenticated team.

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



$response = $sdk->metrics->expenses(
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

**[?Operations\GetExpensesMetricsResponse](../../Models/Operations/GetExpensesMetricsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## spending

Spending metrics for the authenticated team.

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



$response = $sdk->metrics->spending(
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

**[?Operations\GetSpendingMetricsResponse](../../Models/Operations/GetSpendingMetricsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |