# Billit-PHP-SDK
This SDK is developed for integrations with the billit api

- API version: v1

## About this fork

This repository is a fork of `zodi-innovations/billit-php-sdk`.

It contains a small compatibility fix for Billit API list endpoints that
return responses wrapped in `{ Items: [...] }`, which does not match the
published OpenAPI specification.

The fix is applied centrally in `ObjectSerializer::deserialize()`.

## Requirements

PHP 7.3 and later

## Installation & Usage

### Composer

To install the bindings via [Composer](http://getcomposer.org/), add the following to `composer.json`:

```
{
  "repositories": [
    {
      "type": "git",
      "url": "https://github.com/nero987/billit-php-sdk.git"
    }
  ],
  "require": {
      "zodi-innovations/billit-php-sdk": "^1.0"
  }
}
```

Then run `composer install`

### Manual Installation

Download the files and include `autoload.php`:

```php
    require_once('vendor/autoload.php');
```

## Tests

To run the unit tests:

```
composer install
./vendor/bin/phpunit
```

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AccountApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->accountGetAccountInformation();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AccountApi->accountGetAccountInformation: ', $e->getMessage(), PHP_EOL;
}

?>
```

## Documentation for API Endpoints

All URIs are relative to *https://api.billit.be*

 Class                     | Method                                                                                                                     | HTTP request                                                  | Description                                                                                     
---------------------------|----------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------
 *AccountApi*              | [**accountGetAccountInformation**](docs/Api/AccountApi.md#accountgetaccountinformation)                                    | **GET** /v1/account/accountInformation                        |
 *AccountApi*              | [**accountGetSSOToken**](docs/Api/AccountApi.md#accountgetssotoken)                                                        | **GET** /v1/account/ssoToken                                  |
 *AccountApi*              | [**accountPostSequences**](docs/Api/AccountApi.md#accountpostsequences)                                                    | **POST** /v1/account/sequences                                |
 *AccountApi*              | [**accountRegisterCompany**](docs/Api/AccountApi.md#accountregistercompany)                                                | **POST** /v1/account/registercompany                          |
 *AccountantApi*           | [**accountantDeleteFeeds**](docs/Api/AccountantApi.md#accountantdeletefeeds)                                               | **DELETE** /v1/accountant/feeds/{feedName}                    | Delete the feed                                                                                 
 *AccountantApi*           | [**accountantGetFeeds**](docs/Api/AccountantApi.md#accountantgetfeeds)                                                     | **GET** /v1/accountant/feeds                                  |
 *AccountantApi*           | [**accountantGetIndex**](docs/Api/AccountantApi.md#accountantgetindex)                                                     | **GET** /v1/accountant/feeds/{feedName}                       | Get A list of all feeds to download. Only query this once per minute                            
 *AccountantApi*           | [**accountantPostConfirm**](docs/Api/AccountantApi.md#accountantpostconfirm)                                               | **POST** /v1/accountant/feeds/{feedName}/{feedItemID}/confirm | Confirm each succesfully downloaded feed item to remove it from the feedlist                    
 *AccountantApi*           | [**accountantPostFeeds**](docs/Api/AccountantApi.md#accountantpostfeeds)                                                   | **POST** /v1/accountant/feeds                                 | Register a new feed. All newly exported orders or documents will be available in this new feed. 
 *DocumentApi*             | [**documentGetDocument**](docs/Api/DocumentApi.md#documentgetdocument)                                                     | **GET** /v1/documents/{documentID}                            |
 *DocumentApi*             | [**documentGetDocuments**](docs/Api/DocumentApi.md#documentgetdocuments)                                                   | **GET** /v1/documents                                         |
 *DocumentApi*             | [**documentPostDocument**](docs/Api/DocumentApi.md#documentpostdocument)                                                   | **POST** /v1/documents                                        |
 *FileApi*                 | [**fileGetOrders**](docs/Api/FileApi.md#filegetorders)                                                                     | **GET** /v1/files/{fileID}                                    |
 *FinancialTransactionApi* | [**financialTransactionGetBankTransactions**](docs/Api/FinancialTransactionApi.md#financialtransactiongetbanktransactions) | **GET** /v1/financialTransactions                             |
 *FinancialTransactionApi* | [**financialTransactionPostImport**](docs/Api/FinancialTransactionApi.md#financialtransactionpostimport)                   | **POST** /v1/financialTransactions/commands/import            |
 *FinancialTransactionApi* | [**financialTransactionPostImportFile**](docs/Api/FinancialTransactionApi.md#financialtransactionpostimportfile)           | **POST** /v1/financialTransactions/importFile                 |
 *GLAccountApi*            | [**gLAccountPostGLAccount**](docs/Api/GLAccountApi.md#glaccountpostglaccount)                                              | **POST** /v1/glaccounts                                       |
 *GLAccountApi*            | [**gLAccountPostGLAccount_0**](docs/Api/GLAccountApi.md#glaccountpostglaccount_0)                                          | **POST** /v1/glaccounts/commands/import                       |
 *JournalApi*              | [**journalPostGLAccount**](docs/Api/JournalApi.md#journalpostglaccount)                                                    | **POST** /v1/journals/commands/import                         |
 *MiscApi*                 | [**miscGetCompanySearch**](docs/Api/MiscApi.md#miscgetcompanysearch)                                                       | **GET** /v1/misc/companysearch/{Keywords}                     |
 *MiscApi*                 | [**miscGetTranslation**](docs/Api/MiscApi.md#miscgettranslation)                                                           | **GET** /v1/misc/typecodes/{TypeCodeType}/{key}               |
 *MiscApi*                 | [**miscGetTypeCodes**](docs/Api/MiscApi.md#miscgettypecodes)                                                               | **GET** /v1/misc/typecodes/{TypeCodeType}                     |
 *OAuth2Api*               | [**oAuth2PostToken**](docs/Api/OAuth2Api.md#oauth2posttoken)                                                               | **POST** /OAuth2/token                                        |
 *OAuth2Api*               | [**oAuth2PostTokenRevoke**](docs/Api/OAuth2Api.md#oauth2posttokenrevoke)                                                   | **POST** /OAuth2/revoke                                       |
 *OrderApi*                | [**orderGetDeleted**](docs/Api/OrderApi.md#ordergetdeleted)                                                                | **GET** /v1/orders/deleted                                    |
 *OrderApi*                | [**orderGetOrders**](docs/Api/OrderApi.md#ordergetorders)                                                                  | **GET** /v1/orders                                            |
 *OrderApi*                | [**orderGetOrders_0**](docs/Api/OrderApi.md#ordergetorders_0)                                                              | **GET** /v1/orders/{orderID}                                  |
 *OrderApi*                | [**orderPatchOrders**](docs/Api/OrderApi.md#orderpatchorders)                                                              | **PATCH** /v1/orders/{orderID}                                |
 *OrderApi*                | [**orderPostOrderPayment**](docs/Api/OrderApi.md#orderpostorderpayment)                                                    | **POST** /v1/orders/{orderID}/payments                        |
 *OrderApi*                | [**orderPostOrders**](docs/Api/OrderApi.md#orderpostorders)                                                                | **POST** /v1/orders                                           |
 *OrderApi*                | [**orderPostSend**](docs/Api/OrderApi.md#orderpostsend)                                                                    | **POST** /v1/orders/commands/send                             |
 *OrderApi*                | [**orderPutOrderBookings**](docs/Api/OrderApi.md#orderputorderbookings)                                                    | **PUT** /v1/orders/{orderID}/bookingEntries                   |
 *PartyApi*                | [**partyGetParties**](docs/Api/PartyApi.md#partygetparties)                                                                | **GET** /v1/parties                                           |
 *PartyApi*                | [**partyGetParty**](docs/Api/PartyApi.md#partygetparty)                                                                    | **GET** /v1/parties/{partyID}                                 |
 *PartyApi*                | [**partyPatchParties**](docs/Api/PartyApi.md#partypatchparties)                                                            | **PATCH** /v1/parties/{partyID}                               |
 *PartyApi*                | [**partyPostParty**](docs/Api/PartyApi.md#partypostparty)                                                                  | **POST** /v1/parties                                          |
 *PeppolApi*               | [**peppolDeleteParticipant**](docs/Api/PeppolApi.md#peppoldeleteparticipant)                                               | **DELETE** /v1/peppol/participants                            |
 *PeppolApi*               | [**peppolGetInbox**](docs/Api/PeppolApi.md#peppolgetinbox)                                                                 | **GET** /v1/peppol/inbox                                      |
 *PeppolApi*               | [**peppolGetParticipantInformation**](docs/Api/PeppolApi.md#peppolgetparticipantinformation)                               | **GET** /v1/peppol/participantInformation/{VATorCBE}          |
 *PeppolApi*               | [**peppolInboxItemConfirm**](docs/Api/PeppolApi.md#peppolinboxitemconfirm)                                                 | **POST** /v1/peppol/inbox/{inboxItemId}/confirm               |
 *PeppolApi*               | [**peppolPostParticipant**](docs/Api/PeppolApi.md#peppolpostparticipant)                                                   | **POST** /v1/peppol/participants                              |
 *PeppolApi*               | [**peppolPostSendOrder**](docs/Api/PeppolApi.md#peppolpostsendorder)                                                       | **POST** /v1/peppol/sendOrder                                 |
 *ProductApi*              | [**productGetProduct**](docs/Api/ProductApi.md#productgetproduct)                                                          | **GET** /v1/products/{productID}                              | Get a specific product                                                                          
 *ProductApi*              | [**productGetProducts**](docs/Api/ProductApi.md#productgetproducts)                                                        | **GET** /v1/products                                          | Get a list of products                                                                          
 *ProductApi*              | [**productPostProduct**](docs/Api/ProductApi.md#productpostproduct)                                                        | **POST** /v1/products                                         | Create a new product of update an existing product                                              
 *ToProcessApi*            | [**toProcessDeleteToProcess**](docs/Api/ToProcessApi.md#toprocessdeletetoprocess)                                          | **DELETE** /v1/toProcess/{uploadID}                           |
 *ToProcessApi*            | [**toProcessPatchToProcess**](docs/Api/ToProcessApi.md#toprocesspatchtoprocess)                                            | **PATCH** /v1/toProcess/{uploadID}                            |
 *ToProcessApi*            | [**toProcessPostToProcess**](docs/Api/ToProcessApi.md#toprocessposttoprocess)                                              | **POST** /v1/toProcess                                        |
 *ToProcessApi*            | [**toProcessPostToProcess_0**](docs/Api/ToProcessApi.md#toprocessposttoprocess_0)                                          | **POST** /v1/toProcess/{uploadID}                             |

## Documentation For Models

- [AccountInformation](docs/Model/AccountInformation.md)
- [AccountSettings](docs/Model/AccountSettings.md)
- [AssignedEntity](docs/Model/AssignedEntity.md)
- [BankAccount](docs/Model/BankAccount.md)
- [BookingEntry](docs/Model/BookingEntry.md)
- [CompanySearchResult](docs/Model/CompanySearchResult.md)
- [CompanySearchResultItem](docs/Model/CompanySearchResultItem.md)
- [ConfirmRequest](docs/Model/ConfirmRequest.md)
- [DeleteParticipantRequest](docs/Model/DeleteParticipantRequest.md)
- [Document](docs/Model/Document.md)
- [DocumentAPIView](docs/Model/DocumentAPIView.md)
- [ExternalProviderReference](docs/Model/ExternalProviderReference.md)
- [Feed](docs/Model/Feed.md)
- [FeedItem](docs/Model/FeedItem.md)
- [File](docs/Model/File.md)
- [FilterClause](docs/Model/FilterClause.md)
- [FilterQueryOption](docs/Model/FilterQueryOption.md)
- [FilterQueryValidator](docs/Model/FilterQueryValidator.md)
- [GLAccount](docs/Model/GLAccount.md)
- [IEdmDirectValueAnnotationsManager](docs/Model/IEdmDirectValueAnnotationsManager.md)
- [IEdmModel](docs/Model/IEdmModel.md)
- [IEdmSchemaElement](docs/Model/IEdmSchemaElement.md)
- [IEdmTerm](docs/Model/IEdmTerm.md)
- [IEdmType](docs/Model/IEdmType.md)
- [IEdmTypeReference](docs/Model/IEdmTypeReference.md)
- [IEdmVocabularyAnnotatable](docs/Model/IEdmVocabularyAnnotatable.md)
- [IEdmVocabularyAnnotation](docs/Model/IEdmVocabularyAnnotation.md)
- [InboxGetResult](docs/Model/InboxGetResult.md)
- [InboxGetResultItem](docs/Model/InboxGetResultItem.md)
- [InlineCountQueryOption](docs/Model/InlineCountQueryOption.md)
- [Journal](docs/Model/Journal.md)
- [MutableKeyValuePairStringString](docs/Model/MutableKeyValuePairStringString.md)
- [OAuthAccessTokenRequest](docs/Model/OAuthAccessTokenRequest.md)
- [ODataQueryContext](docs/Model/ODataQueryContext.md)
- [ODataQueryOptionsDocumentAPIView](docs/Model/ODataQueryOptionsDocumentAPIView.md)
- [ODataQueryOptionsOrder](docs/Model/ODataQueryOptionsOrder.md)
- [ODataQueryOptionsParty](docs/Model/ODataQueryOptionsParty.md)
- [ODataQueryOptionsProduct](docs/Model/ODataQueryOptionsProduct.md)
- [ODataQueryOptionsTransaction](docs/Model/ODataQueryOptionsTransaction.md)
- [ODataQueryValidator](docs/Model/ODataQueryValidator.md)
- [ODataRawQueryOptions](docs/Model/ODataRawQueryOptions.md)
- [Order](docs/Model/Order.md)
- [OrderByClause](docs/Model/OrderByClause.md)
- [OrderByNode](docs/Model/OrderByNode.md)
- [OrderByQueryOption](docs/Model/OrderByQueryOption.md)
- [OrderByQueryValidator](docs/Model/OrderByQueryValidator.md)
- [OrderLine](docs/Model/OrderLine.md)
- [PageResultDocumentAPIView](docs/Model/PageResultDocumentAPIView.md)
- [PageResultOrder](docs/Model/PageResultOrder.md)
- [PageResultParty](docs/Model/PageResultParty.md)
- [PageResultProduct](docs/Model/PageResultProduct.md)
- [PageResultTransaction](docs/Model/PageResultTransaction.md)
- [ParticipantInformationResponse](docs/Model/ParticipantInformationResponse.md)
- [Party](docs/Model/Party.md)
- [PaymentLink](docs/Model/PaymentLink.md)
- [PostPaymentRequest](docs/Model/PostPaymentRequest.md)
- [ProcessInfo](docs/Model/ProcessInfo.md)
- [Product](docs/Model/Product.md)
- [RangeVariable](docs/Model/RangeVariable.md)
- [RegisterAccountRequest](docs/Model/RegisterAccountRequest.md)
- [RegisterParticipantRequest](docs/Model/RegisterParticipantRequest.md)
- [SelectExpandClause](docs/Model/SelectExpandClause.md)
- [SelectExpandQueryOption](docs/Model/SelectExpandQueryOption.md)
- [SelectExpandQueryValidator](docs/Model/SelectExpandQueryValidator.md)
- [SelectItem](docs/Model/SelectItem.md)
- [SendRequest](docs/Model/SendRequest.md)
- [SequenceRequest](docs/Model/SequenceRequest.md)
- [ServiceDetail](docs/Model/ServiceDetail.md)
- [SingleValueNode](docs/Model/SingleValueNode.md)
- [SkipQueryOption](docs/Model/SkipQueryOption.md)
- [SkipQueryValidator](docs/Model/SkipQueryValidator.md)
- [ToProcessSaveRequest](docs/Model/ToProcessSaveRequest.md)
- [TopQueryOption](docs/Model/TopQueryOption.md)
- [TopQueryValidator](docs/Model/TopQueryValidator.md)
- [Transaction](docs/Model/Transaction.md)
- [TypeCodeResult](docs/Model/TypeCodeResult.md)
- [TypeCodeResultItem](docs/Model/TypeCodeResultItem.md)
- [UploadMetadata](docs/Model/UploadMetadata.md)
- [UserCompanyRole](docs/Model/UserCompanyRole.md)
- [VatGroup](docs/Model/VatGroup.md)

## Documentation For Authorization

All endpoints do not require authorization.

## Author
