# OAuth

## Overview

### Available Operations

* [getOAuthAuthorization](#getoauthauthorization) - OAuth Authorization Endpoint
* [postOAuthAuthorization](#postoauthauthorization) - OAuth Authorization Decision
* [postOAuthToken](#postoauthtoken) - OAuth Token Exchange
* [postOAuthRevoke](#postoauthrevoke) - OAuth Token Revocation

## getOAuthAuthorization

Initiate OAuth authorization flow and get consent screen information

### Example Usage

<!-- UsageSnippet language="php" operationID="getOAuthAuthorization" method="get" path="/oauth/authorize" -->
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

### Parameters

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `$request`                                                                                         | [Operations\GetOAuthAuthorizationRequest](../../Models/Operations/GetOAuthAuthorizationRequest.md) | :heavy_check_mark:                                                                                 | The request object to use for the request.                                                         |

### Response

**[?Operations\GetOAuthAuthorizationResponse](../../Models/Operations/GetOAuthAuthorizationResponse.md)**

### Errors

| Error Type                                      | Status Code                                     | Content Type                                    |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| Errors\GetOAuthAuthorizationBadRequestException | 400                                             | application/json                                |
| Errors\APIException                             | 4XX, 5XX                                        | \*/\*                                           |

## postOAuthAuthorization

Process user's authorization decision (allow/deny)

### Example Usage

<!-- UsageSnippet language="php" operationID="postOAuthAuthorization" method="post" path="/oauth/authorize" -->
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

$request = new Operations\PostOAuthAuthorizationRequest(
    clientId: 'mid_client_abcdef123456789',
    decision: Operations\Decision::Allow,
    scopes: [
        Operations\Scope::TransactionsRead,
        Operations\Scope::InvoicesRead,
    ],
    redirectUri: 'https://myapp.com/callback',
    state: 'abc123xyz789_secure-random-state-value-with-sufficient-entropy',
    codeChallenge: 'E9Melhoa2OwvFrEMTJguCHaoeK1t8URWbuGJSstw-cM',
    teamId: '123e4567-e89b-12d3-a456-426614174000',
);

$response = $sdk->oAuth->postOAuthAuthorization(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `$request`                                                                                           | [Operations\PostOAuthAuthorizationRequest](../../Models/Operations/PostOAuthAuthorizationRequest.md) | :heavy_check_mark:                                                                                   | The request object to use for the request.                                                           |

### Response

**[?Operations\PostOAuthAuthorizationResponse](../../Models/Operations/PostOAuthAuthorizationResponse.md)**

### Errors

| Error Type                                       | Status Code                                      | Content Type                                     |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| Errors\PostOAuthAuthorizationBadRequestException | 400                                              | application/json                                 |
| Errors\UnauthorizedException                     | 401                                              | application/json                                 |
| Errors\APIException                              | 4XX, 5XX                                         | \*/\*                                            |

## postOAuthToken

Exchange authorization code for access token or refresh an access token

### Example Usage

<!-- UsageSnippet language="php" operationID="postOAuthToken" method="post" path="/oauth/token" -->
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

$request = new Operations\RefreshToken(
    grantType: Operations\GrantTypeRefreshToken::RefreshToken,
    refreshToken: 'mid_rt_abcdef123456789',
    clientId: 'mid_client_abcdef123456789',
    clientSecret: 'mid_secret_abcdef123456789',
    scope: 'transactions.read invoices.read',
);

$response = $sdk->oAuth->postOAuthToken(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                               | [Operations\AuthorizationCode\|Operations\RefreshToken](../../Models/Operations/PostOAuthTokenRequest.md) | :heavy_check_mark:                                                                                       | The request object to use for the request.                                                               |

### Response

**[?Operations\PostOAuthTokenResponse](../../Models/Operations/PostOAuthTokenResponse.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| Errors\PostOAuthTokenBadRequestException | 400                                      | application/json                         |
| Errors\APIException                      | 4XX, 5XX                                 | \*/\*                                    |

## postOAuthRevoke

Revoke an access token or refresh token

### Example Usage

<!-- UsageSnippet language="php" operationID="postOAuthRevoke" method="post" path="/oauth/revoke" -->
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

$request = new Operations\PostOAuthRevokeRequest(
    token: 'mid_access_token_abcdef123456789',
    tokenTypeHint: Operations\TokenTypeHint::AccessToken,
    clientId: 'mid_client_abcdef123456789',
    clientSecret: 'mid_secret_abcdef123456789',
);

$response = $sdk->oAuth->postOAuthRevoke(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `$request`                                                                             | [Operations\PostOAuthRevokeRequest](../../Models/Operations/PostOAuthRevokeRequest.md) | :heavy_check_mark:                                                                     | The request object to use for the request.                                             |

### Response

**[?Operations\PostOAuthRevokeResponse](../../Models/Operations/PostOAuthRevokeResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |