---
title: Get customer's direct signing status for Microsoft Customer Agreement.
description: You can use the DirectSignedCustomerAgreementStatus resource to get the status of a customer's direct signing (direct acceptance) of the Microsoft Customer Agreement. 
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice:  partnercenter-csp
ms.localizationpriority: medium
---

# Get the status of a customer's direct signing (direct acceptance) of Microsoft Customer Agreement

Applies to:

- Partner Center

The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.

This resource is *not applicable* to:

- Partner Center operated by 21Vianet
- Partner Center for Microsoft Cloud Germany
- Partner Center for Microsoft Cloud for US Government

This article explains how you can retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement.

## REST request

To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement,
create a REST request to retrieve the [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) for the customer. 

### Request syntax

Use the following request syntax:

| Method | Request URI                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1 |

### URI parameters

You can use the following URI parameters with your request:

| Name             | Type | Required | Description                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| customer-tenant-id | GUID | Yes | The value is a GUID-formatted **CustomerTenantId** that allows you to specify the tenant ID of a customer. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token> 
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## REST response

If successful, this method returns a [**DirectSignedCustomerAgreementStatus** resource](./customer-agreement-direct-sign-status-resource.md) in the response body.

The resource has an **isSigned** property that indicates the customer's direct signing (direct acceptance) status. 

- A value of **true** indicates that the agreement has been signed (accepted) directly by the customer.
- A value of **false** indicates that the agreement has *not* been signed (accepted) directly by the customer.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. 

Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```