---
title: "serviceActivity: getMetricsForConditionalAccessManagedDevicesSignInSuccess"
description: "Get the number of user authentication requests, during a specific time period, that satisfy a Conditional Access policy requiring devices to be managed. Managed devices are computers joined to and managed by your on-premises directory and hybrid devices joined to Microsoft Entra."
author: "Zacharypeng"
ms.localizationpriority: medium
ms.prod: "identity-and-access-reports"
doc_type: apiPageType
---

# serviceActivity: getMetricsForConditionalAccessManagedDevicesSignInSuccess
Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get the number of user authentication requests, during a specific time period, that satisfy a Conditional Access policy requiring devices to be managed. Managed devices are computers joined to and managed by your on-premises directory and hybrid devices joined to Microsoft Entra.

## Permissions
Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "serviceactivity_getmetricsforconditionalaccessmanageddevicessigninsuccess" } -->
[!INCLUDE [permissions-table](../includes/permissions/serviceactivity-getmetricsforconditionalaccessmanageddevicessigninsuccess-permissions.md)]

In addition to the delegated permissions, the signed-in user who is accessing the data needs to belong to one of the following directory roles, which allow them to read sign-in reports:

+ Global Administrator
+ Global Reader
+ Reports Reader
+ Security Administrator
+ Security Operator
+ Security Reader

To learn more about directory roles, see [Microsoft Entra built-in roles](/azure/active-directory/roles/permissions-reference).
## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /reports/serviceActivity/getMetricsForConditionalAccessManagedDevicesSignInSuccess
```

## Function parameters
In the request URL, provide the following query parameters with values.

|Parameter|Type|Description|
|:---|:---|:---|
|inclusiveIntervalStartDateTime|DateTimeOffset|Sets the starting date and time in UTC. The earliest start time allowed is 30 days in the past. Required.|
|exclusiveIntervalEndDateTime|DateTimeOffset|Sets the ending date and time in UTC. Required.|
|aggregationIntervalInMinutes|Int32|Aggregation interval in minutes. The default value is 15, which sets the data to be aggregated into 15-minute sets. Allowed values are 5, 10, 15 and 30. Optional.|

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [serviceActivityValueMetric](../resources/serviceactivityvaluemetric.md) collection in the response body.

## Examples

### Request
The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "serviceactivitythis.getmetricsforconditionalaccessmanageddevicessigninsuccess"
}
-->
``` http
GET https://graph.microsoft.com/beta/reports/serviceActivity/getMetricsForConditionalAccessManagedDevicesSignInSuccess(inclusiveIntervalStartDateTime=2023-01-01T00:00:00Z,exclusiveIntervalEndDateTime=2023-01-01T00:20:00Z,aggregationIntervalInMinutes=10)
```

### Response
The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.serviceActivityValueMetric)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/networkAccess/reports/$metadata#Collection(serviceActivityValueMetric)",
  "value": [
   {
      "intervalStartDateTime": "2023-01-10T00:00:00Z",
      "value": 4
    },
    {
      "intervalStartDateTime": "2023-01-10T00:10:00Z",
      "value": 5
    },
    {
      "intervalStartDateTime": "2023-01-10T00:20:00Z",
      "value": 4
    }
  ]
}
```
