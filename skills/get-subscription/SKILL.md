# Get a Specific Subscription

Retrieve details of a specific Copilot change notification subscription by its ID.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/subscriptions/{subscriptionId}`
- **Operation ID**: `getCopilotSubscription`
- **Tag**: Change Notifications
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions/{subscriptionId}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.ChangeNotification.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `subscriptionId` | path | string | Yes | Unique identifier of the subscription |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions/sub-001-abc" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "sub-001-abc",
  "resource": "/copilot/interactions",
  "changeType": "created",
  "notificationUrl": "https://contoso.com/webhooks/copilot-notifications",
  "expirationDateTime": "2025-10-15T00:00:00Z",
  "clientState": "contoso-secret-state-value",
  "createdDateTime": "2025-09-10T12:00:00Z"
}
```

## Instructions

When the user wants to check the details of a specific change notification subscription, use this operation by making a GET request to `/copilot/subscriptions/{subscriptionId}`. Provide the subscription ID as a path parameter.
