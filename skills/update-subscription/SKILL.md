# Renew or Update a Subscription

Renew or update the configuration of an existing Copilot change notification subscription.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: PATCH
- **Path**: `/copilot/subscriptions/{subscriptionId}`
- **Operation ID**: `updateCopilotSubscription`
- **Tag**: Change Notifications
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions/{subscriptionId}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scope

- `Copilot.ChangeNotification.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `subscriptionId` | path | string | Yes | Unique identifier of the subscription |

## Request Body

```json
{
  "expirationDateTime": "2025-11-15T00:00:00Z"
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `expirationDateTime` | string | No | New expiration date/time (ISO 8601) |
| `notificationUrl` | string | No | Updated webhook URL |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions/sub-001-abc" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{"expirationDateTime": "2025-11-15T00:00:00Z"}'
```

## Example Response

```json
{
  "id": "sub-001-abc",
  "resource": "/copilot/interactions",
  "changeType": "created",
  "notificationUrl": "https://contoso.com/webhooks/copilot-notifications",
  "expirationDateTime": "2025-11-15T00:00:00Z",
  "clientState": "contoso-secret-state-value",
  "createdDateTime": "2025-09-10T12:00:00Z"
}
```

## Instructions

When the user wants to renew or update an existing change notification subscription (e.g., extend expiration or change webhook URL), use this operation by making a PATCH request to `/copilot/subscriptions/{subscriptionId}`. Provide the subscription ID and the fields to update.
