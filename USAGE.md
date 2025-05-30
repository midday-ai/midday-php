<!-- Start SDK Example Usage [usage] -->
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

$request = new Operations\ListTransactionsRequest(
    cursor: 'eyJpZCI6IjEyMyJ9',
    sort: [
        'date',
        'desc',
    ],
    pageSize: 50,
    q: 'office supplies',
    categories: [
        'office-supplies',
        'travel',
    ],
    tags: [
        'tag-1',
        'tag-2',
    ],
    start: '2024-04-01T00:00:00.000Z',
    end: '2024-04-30T23:59:59.999Z',
    accounts: [
        'account-1',
        'account-2',
    ],
    assignees: [
        'user-1',
        'user-2',
    ],
    statuses: [
        'pending',
        'completed',
    ],
    recurring: [
        'monthly',
        'annually',
    ],
    attachments: Operations\Attachments::Include,
    amountRange: [
        100,
        1000,
    ],
    amount: [
        '150.75',
        '299.99',
    ],
    type: Operations\ListTransactionsType::Expense,
);

$response = $sdk->transactions->list(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```
<!-- End SDK Example Usage [usage] -->