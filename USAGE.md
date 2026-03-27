<!-- Start SDK Example Usage [usage] -->
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

$request = new Operations\GetOAuthAuthorizationRequest(
    responseType: Operations\ResponseType::Code,
    clientId: 'mid_client_abcdef123456789',
    redirectUri: 'https://myapp.com/callback',
    scope: 'transactions.read invoices.read',
    state: 'abc123xyz789_secure-random-state-value-with-sufficient-entropy',
    codeChallenge: 'E9Melhoa2OwvFrEMTJguCHaoeK1t8URWbuGJSstw-cM',
);

$response = $sdk->oAuth->getOAuthAuthorization(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```
<!-- End SDK Example Usage [usage] -->