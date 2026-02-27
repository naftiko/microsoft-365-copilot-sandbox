# Create a Change Notification Subscription

Subscribe to change notifications for Copilot interactions across Microsoft 365. Enables real-time monitoring, proactive compliance checks, anomaly detection, and auditing.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: POST
- **Path**: `/copilot/subscriptions`
- **Operation ID**: `createCopilotSubscription`
- **Tag**: Change Notifications
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scope

- `Copilot.ChangeNotification.ReadWrite`

## Request Body

```json
{
  "resource": "/copilot/interactions",
  "changeType": "created",
  "notificationUrl": "https://contoso.com/webhooks/copilot-notifications",
  "expirationDateTime": "2025-10-15T00:00:00Z",
  "clientState": "contoso-secret-state-value"
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `resource` | string | Yes | The resource to monitor (e.g., /copilot/interactions) |
| `changeType` | string | Yes | Type of change to subscribe to (created, updated) |
| `notificationUrl` | string | Yes | Webhook URL for notifications |
| `expirationDateTime` | string | Yes | When the subscription expires (ISO 8601) |
| `clientState` | string | No | Secret value for validating notifications |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{"resource": "/copilot/interactions", "changeType": "created", "notificationUrl": "https://contoso.com/webhooks/copilot-notifications", "expirationDateTime": "2025-10-15T00:00:00Z", "clientState": "contoso-secret-state-value"}'
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

When the user wants to set up webhook notifications for Copilot interaction events, use this operation by making a POST request to `/copilot/subscriptions`. Provide the resource to monitor, change type, webhook URL, and expiration. This enables real-time monitoring and compliance auditing.
