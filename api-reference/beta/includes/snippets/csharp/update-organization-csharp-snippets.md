---
description: "Automatically generated file. DO NOT MODIFY"
---

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

var graphClient = new GraphServiceClient(requestAdapter);

var requestBody = new Organization
{
	MarketingNotificationEmails = new List<string>
	{
		"marketing@contoso.com",
	},
	OnPremisesSyncEnabled = true,
	PrivacyProfile = new PrivacyProfile
	{
		ContactEmail = "alice@contoso.com",
		StatementUrl = "https://contoso.com/privacyStatement",
	},
	SecurityComplianceNotificationMails = new List<string>
	{
		"security@contoso.com",
	},
	SecurityComplianceNotificationPhones = new List<string>
	{
		"(123) 456-7890",
	},
	TechnicalNotificationMails = new List<string>
	{
		"tech@contoso.com",
	},
};
var result = await graphClient.Organization["{organization-id}"].PatchAsync(requestBody);


```