# VectorizerAI\AccountApi

All URIs are relative to https://api.vectorizer.ai/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getAccountStatus()**](AccountApi.md#getAccountStatus) | **GET** /account | Get account status |


## `getAccountStatus()`

```php
getAccountStatus(): \VectorizerAI\Model\AccountStatusResponse
```

Get account status

Fetch the subscription state and remaining API credits for the authenticated account.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = VectorizerAI\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new VectorizerAI\Api\AccountApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

$associative_array = [
];

try {
    $result = $apiInstance->getAccountStatus($associate_array);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AccountApi->getAccountStatus: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

Note: the input parameter is an associative array with the keys listed as the parameter names below.

This endpoint does not need any parameter.

### Return type

[**\VectorizerAI\Model\AccountStatusResponse**](../Model/AccountStatusResponse.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
