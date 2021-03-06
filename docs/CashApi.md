# CashApi

All URIs are relative to *https://localhost:13083*

Method | HTTP request | Description
------------- | ------------- | -------------
[**Cash**](CashApi.md#CashRequest) | **POST** /api/cash | Cash deposit/withdraw

## CashRequest
> Cash deposit/withdraw

Create cash deposit or withdraw

### Example
```bash
curl --location --request POST 'http://localhost:13083/api/cash' \
--data-raw '{
    "externalId": "uuid:bb78531a-f2f7-c27f-9523-819b1d280a4b",
    "amount": 300,
    "footer": "Morning deposit",
    "exception": false
}'
```

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

### Example Request Body

```yaml
{
    "externalId": "uuid:bb78531a-f2f7-c27f-9523-819b1d280a4b",
    "amount": 300,
    "footer": "Morning deposit",
    "exception": false
}
```

### Request Parameters

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**external_id** | **String** | External id from external software | [optional] 
**printer** | [**Printer**](Printer.md) |  | [optional] 
**amount** | **Float** | Cash in/out to/from cashier | [required] 
**footer** | **String** | Custom text to footer | [optional] 
**exception** | **Boolean** |  | [optional] 

### Example Response Body

```yaml
{
  "cash": {
    "amount": 300,
    "cashRegisterCode": "88812345678900001",
    "createDate": "05.11.2020 11:22:15",
    "electronic": false,
    "electronicReceipt": "",
    "exception": false,
    "footer": "Morning deposit",
    "issueDate": "05.11.2020 11:22:15",
    "merchant": {
      "corporateFullName": "O.C.a.F.A. STANDARD_ICDPH",
      "dic": "1234567890",
      "icDph": "SK9999999999",
      "ico": "99999999",
      "id": 9113,
      "organizationUnit": {
        "cashRegisterCode": "88812345678900001",
        "cashRegisterType": "STANDARD",
        "location": {
          "physicalAddress": {
            "buildingNumber": "21",
            "country": "Slovenská republika",
            "municipality": "Nitra",
            "postalCode": "22222",
            "propertyRegistrationNumber": "980",
            "street": "Hospodárska"
          }
        },
        "name": "nepovinný názov predajne"
      },
      "physicalAddress": {
        "buildingNumber": "4",
        "country": "Slovenská republika",
        "municipality": "Bratislava",
        "postalCode": "99999",
        "propertyRegistrationNumber": "22",
        "street": "Miletičova"
      }
    },
    "okp": "01B73BB8-DD6E831D-7694A17D-47A46D6D-980BD8D0",
    "pkp": "TSxZ4qObDikdUPENwHVxr6Fe8oNEJgYCrp2AMJTWuLtxCHSyvRGM7nEMBPNi\r\nnjE/AFgyDIdfAk7MaU20ASuUZs4MOu8rj3+VCau69yfyp2i3yAnrYfze76Re\r\nXGyqrm9HQkXlvw9ryRNg5ogEtyfglVnXmPXwLLCAc3X4dgcANyPLr7ZcMNCV\r\nfQ2AEvXwZ/6nhmBs1Bh+9O4cIeYjUuv9cSFBWNLlpJIA1XdrTJTiPiBeaVZ6\r\nE2qd1/HjWg8DhBr9sSbOXSGE24cD8TKhmtMy4goUxpc2VbNitFO7yHopt8dU\r\n1xMYSmh8BKktofoVKUnk2KfWzqXMqnvvSjyt0JCBaQ\\u003d\\u003d",
    "processDate": "05.11.2020 11:22:18",
    "qrCode": "O-7F02B42B29ED4EFE82B42B29ED8-TEST",
    "sendingCount": 1,
    "sequenceId": 2,
    "uuid": "O-7F02B42B29ED4EFE82B42B29ED8-TEST",
    "status": {}
  }
}
```

### Response Parameters

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**warning** | **String** | Filled only if any warning | [optional] 
**cash** | [**Cash**](CashApi.md#Cash) |  | [optional] 
**error_message** | **String** | Ooops! Something went wrong | [optional] 

#### Cash

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**status** | [**EkasaStatus**](EkasaStatus.md) |  | [optional] 
**printer_status** | **String** | Printer status | [optional] 
**internal_document_id** | **Integer** | internal id generated by PPEKK | [optional] 
**sequence_id** | **Integer** | Sequence id of Document. Restarted by every month starting of 1 in sequence | [optional] 
**merchant** | [**Merchant**](Merchant.md) |  | [optional] 
**cash_register_code** | **String** | Cash register code | [optional] 
**amount** | **Float** | Amount of cash withdraw or  | [optional] 
**issue_date** | **DateTime** | Date of issuing receipt. This is NOT equal with createDate only for paragon document | [optional] 
**create_date** | **DateTime** | Date of creation in ekasa | [optional] 
**process_date** | **DateTime** | Process datetime of receipt on eKasa. Not present if offline receipt | [optional] 
**uuid** | **String** | Receipt UUID generated by eKasa. Not present if offline receipt | [optional] 
**pkp** | **String** | Pkp printed on receipt | [optional] 
**okp** | **String** | OKP printed on receipt | [optional] 
**footer** | **String** | Custom footer to print at the bottom of the receipt | [optional] 
**exception** | **Boolean** | If this document has exception to send offline receipts later | [optional] 
**electronic** | **Boolean** | If receipt is going to be sent electronically | [optional] 
**electronic_receipt** | **String** | Electronic receipt as bitmap in BASE64 encoding or Esc Pos sequence receipt | [optional] 
**qr_code** | **String** | Qr code printed on receipt | [optional] 
**document_type** | **String** |  | [optional] 

