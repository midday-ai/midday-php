<div align="center">
  <img src="https://github.com/midday-ai/midday-php/raw/main/hero.jpg" alt="Midday PHP SDK to interact with APIs.">
  <h3>Midday PHP SDK</h3>
  <a href="https://speakeasyapi.dev/"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20Speakeasy-212015?style=for-the-badge&logoColor=FBE331&logo=speakeasy&labelColor=545454" /></a>
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
  </a>
</div>

<br/>


Learn more about the Midday PHP SDK in the [official documentation](https://docs.midday.ai/sdks/php/overview).

<!-- Start Summary [summary] -->
## Summary

Midday API: Midday is a platform for Invoicing, Time tracking, File reconciliation, Storage, Financial Overview & your own Assistant.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

The SDK relies on [Composer](https://getcomposer.org/) to manage its dependencies.

To install the SDK and add it as a dependency to an existing `composer.json` file:
```bash
composer require "midday/midday-php"
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

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

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security schemes globally:

| Name     | Type   | Scheme      |
| -------- | ------ | ----------- |
| `oauth2` | apiKey | API key     |
| `token`  | http   | HTTP Bearer |

You can set the security parameters through the `setSecurity` function on the `SDKBuilder` when initializing the SDK. The selected scheme will be used by default to authenticate with the API for all operations that support it. For example:
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [bankAccounts](docs/sdks/bankaccounts/README.md)

* [list](docs/sdks/bankaccounts/README.md#list) - List all bank accounts
* [create](docs/sdks/bankaccounts/README.md#create) - Create a bank account
* [get](docs/sdks/bankaccounts/README.md#get) - Retrieve a bank account
* [delete](docs/sdks/bankaccounts/README.md#delete) - Delete a bank account
* [update](docs/sdks/bankaccounts/README.md#update) - Update a bank account

### [customers](docs/sdks/customers/README.md)

* [list](docs/sdks/customers/README.md#list) - List all customers
* [create](docs/sdks/customers/README.md#create) - Create customer
* [get](docs/sdks/customers/README.md#get) - Retrieve a customer
* [delete](docs/sdks/customers/README.md#delete) - Delete a customer
* [update](docs/sdks/customers/README.md#update) - Update a customer

### [documents](docs/sdks/documents/README.md)

* [list](docs/sdks/documents/README.md#list) - List all documents
* [get](docs/sdks/documents/README.md#get) - Retrieve a document
* [delete](docs/sdks/documents/README.md#delete) - Delete a document
* [getPreSignedUrl](docs/sdks/documents/README.md#getpresignedurl) - Generate pre-signed URL for document

### [inbox](docs/sdks/inbox/README.md)

* [list](docs/sdks/inbox/README.md#list) - List all inbox items
* [get](docs/sdks/inbox/README.md#get) - Retrieve a inbox item
* [delete](docs/sdks/inbox/README.md#delete) - Delete a inbox item
* [update](docs/sdks/inbox/README.md#update) - Update a inbox item
* [getPreSignedUrl](docs/sdks/inbox/README.md#getpresignedurl) - Generate pre-signed URL for inbox attachment

### [invoices](docs/sdks/invoices/README.md)

* [list](docs/sdks/invoices/README.md#list) - List all invoices
* [create](docs/sdks/invoices/README.md#create) - Create an invoice
* [getInvoicesPaymentStatus](docs/sdks/invoices/README.md#getinvoicespaymentstatus) - Payment status
* [summary](docs/sdks/invoices/README.md#summary) - Invoice summary
* [get](docs/sdks/invoices/README.md#get) - Retrieve a invoice
* [update](docs/sdks/invoices/README.md#update) - Update an invoice
* [delete](docs/sdks/invoices/README.md#delete) - Delete a invoice


### [notifications](docs/sdks/notifications/README.md)

* [list](docs/sdks/notifications/README.md#list) - List all notifications
* [updateStatus](docs/sdks/notifications/README.md#updatestatus) - Update notification status
* [updateAllStatus](docs/sdks/notifications/README.md#updateallstatus) - Update status of all notifications

### [oAuth](docs/sdks/oauth/README.md)

* [getOAuthAuthorization](docs/sdks/oauth/README.md#getoauthauthorization) - OAuth Authorization Endpoint
* [postOAuthAuthorization](docs/sdks/oauth/README.md#postoauthauthorization) - OAuth Authorization Decision
* [postOAuthToken](docs/sdks/oauth/README.md#postoauthtoken) - OAuth Token Exchange
* [postOAuthRevoke](docs/sdks/oauth/README.md#postoauthrevoke) - OAuth Token Revocation

### [reports](docs/sdks/reports/README.md)

* [revenue](docs/sdks/reports/README.md#revenue) - Revenue reports
* [profit](docs/sdks/reports/README.md#profit) - Profit reports
* [burnRate](docs/sdks/reports/README.md#burnrate) - Burn rate reports
* [runway](docs/sdks/reports/README.md#runway) - Runway reports
* [expenses](docs/sdks/reports/README.md#expenses) - Expense reports
* [spending](docs/sdks/reports/README.md#spending) - Spending reports

### [search](docs/sdks/search/README.md)

* [search](docs/sdks/search/README.md#search) - Search

### [tags](docs/sdks/tags/README.md)

* [list](docs/sdks/tags/README.md#list) - List all tags
* [create](docs/sdks/tags/README.md#create) - Create a new tag
* [get](docs/sdks/tags/README.md#get) - Retrieve a tag
* [delete](docs/sdks/tags/README.md#delete) - Delete a tag
* [update](docs/sdks/tags/README.md#update) - Update a tag

### [teams](docs/sdks/teams/README.md)

* [list](docs/sdks/teams/README.md#list) - List all teams
* [get](docs/sdks/teams/README.md#get) - Retrieve a team
* [update](docs/sdks/teams/README.md#update) - Update a team
* [members](docs/sdks/teams/README.md#members) - List all team members

### [trackerEntries](docs/sdks/trackerentries/README.md)

* [list](docs/sdks/trackerentries/README.md#list) - List all tracker entries
* [create](docs/sdks/trackerentries/README.md#create) - Create a tracker entry
* [createBulk](docs/sdks/trackerentries/README.md#createbulk) - Create multiple tracker entries
* [delete](docs/sdks/trackerentries/README.md#delete) - Delete a tracker entry
* [update](docs/sdks/trackerentries/README.md#update) - Update a tracker entry

### [trackerProjects](docs/sdks/trackerprojects/README.md)

* [list](docs/sdks/trackerprojects/README.md#list) - List all tracker projects
* [create](docs/sdks/trackerprojects/README.md#create) - Create a tracker project
* [get](docs/sdks/trackerprojects/README.md#get) - Retrieve a tracker project
* [delete](docs/sdks/trackerprojects/README.md#delete) - Delete a tracker project
* [update](docs/sdks/trackerprojects/README.md#update) - Update a tracker project

### [trackerTimer](docs/sdks/trackertimer/README.md)

* [startTimer](docs/sdks/trackertimer/README.md#starttimer) - Start a timer
* [stopTimer](docs/sdks/trackertimer/README.md#stoptimer) - Stop a timer
* [getCurrentTimer](docs/sdks/trackertimer/README.md#getcurrenttimer) - Get current timer
* [getTimerStatus](docs/sdks/trackertimer/README.md#gettimerstatus) - Get timer status

### [transactions](docs/sdks/transactions/README.md)

* [list](docs/sdks/transactions/README.md#list) - List all transactions
* [create](docs/sdks/transactions/README.md#create) - Create a transaction
* [get](docs/sdks/transactions/README.md#get) - Retrieve a transaction
* [delete](docs/sdks/transactions/README.md#delete) - Delete a transaction
* [update](docs/sdks/transactions/README.md#update) - Update a transaction
* [getAttachmentPreSignedUrl](docs/sdks/transactions/README.md#getattachmentpresignedurl) - Generate pre-signed URL for transaction attachment
* [createMany](docs/sdks/transactions/README.md#createmany) - Bulk create transactions
* [deleteMany](docs/sdks/transactions/README.md#deletemany) - Bulk delete transactions
* [updateMany](docs/sdks/transactions/README.md#updatemany) - Bulk update transactions

### [users](docs/sdks/users/README.md)

* [get](docs/sdks/users/README.md#get) - Retrieve the current user
* [update](docs/sdks/users/README.md#update) - Update the current user

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or throw an exception.

By default an API error will raise a `Errors\APIException` exception, which has the following properties:

| Property       | Type                                    | Description           |
|----------------|-----------------------------------------|-----------------------|
| `$message`     | *string*                                | The error message     |
| `$statusCode`  | *int*                                   | The HTTP status code  |
| `$rawResponse` | *?\Psr\Http\Message\ResponseInterface*  | The raw HTTP response |
| `$body`        | *string*                                | The response content  |

When custom error responses are specified for an operation, the SDK may also throw their associated exception. You can refer to respective *Errors* tables in SDK docs for more details on possible exception types for each operation. For example, the `getOAuthAuthorization` method throws the following exceptions:

| Error Type                                      | Status Code | Content Type     |
| ----------------------------------------------- | ----------- | ---------------- |
| Errors\GetOAuthAuthorizationBadRequestException | 400         | application/json |
| Errors\APIException                             | 4XX, 5XX    | \*/\*            |

### Example

```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Components;
use Midday\Midday\Models\Errors;
use Midday\Midday\Models\Operations;

$sdk = Midday\Midday::builder()
    ->setSecurity(
        new Components\Security(
            oauth2: '<YOUR_API_KEY_HERE>',
        )
    )
    ->build();

try {
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
} catch (Errors\GetOAuthAuthorizationBadRequestExceptionThrowable $e) {
    // handle $e->$container data
    throw $e;
} catch (Errors\APIException $e) {
    // handle default exception
    throw $e;
}
```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally using the `setServerUrl(string $serverUrl)` builder method when initializing the SDK client instance. For example:
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use Midday\Midday;
use Midday\Midday\Models\Components;
use Midday\Midday\Models\Operations;

$sdk = Midday\Midday::builder()
    ->setServerURL('https://api.midday.ai')
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
<!-- End Server Selection [server] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=midday/midday-php&utm_campaign=php)
