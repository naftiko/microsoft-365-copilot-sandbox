# List Active Change Notification Subscriptions

Retrieve all active Copilot change notification subscriptions.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/subscriptions`
- **Operation ID**: `listCopilotSubscriptions`
- **Tag**: Change Notifications
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.ChangeNotification.ReadWrite`

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "sub-001-abc",
      "resource": "/copilot/interactions",
      "changeType": "created",
      "notificationUrl": "https://contoso.com/webhooks/copilot-notifications",
      "expirationDateTime": "2025-10-15T00:00:00Z",
      "clientState": "contoso-secret-state-value",
      "createdDateTime": "2025-09-10T12:00:00Z"
    },
    {
      "id": "sub-002-def",
      "resource": "/copilot/interactions",
      "changeType": "updated",
      "notificationUrl": "https://contoso.com/webhooks/copilot-updates",
      "expirationDateTime": "2025-10-20T00:00:00Z",
      "clientState": "contoso-update-state",
      "createdDateTime": "2025-09-11T08:30:00Z"
    }
  ]
}
```

## Instructions

When the user wants to view all active webhook subscriptions for Copilot change notifications, use this operation by making a GET request to `/copilot/subscriptions`. This returns all active subscriptions with their configuration details including resource, change type, notification URL, and expiration.
