# Delete a Subscription

Remove an existing Copilot change notification subscription.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: DELETE
- **Path**: `/copilot/subscriptions/{subscriptionId}`
- **Operation ID**: `deleteCopilotSubscription`
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
| `subscriptionId` | path | string | Yes | Unique identifier of the subscription to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/subscriptions/sub-001-abc" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

HTTP 204 No Content (empty response body on success).

## Instructions

When the user wants to remove or cancel a change notification subscription, use this operation by making a DELETE request to `/copilot/subscriptions/{subscriptionId}`. Provide the subscription ID as a path parameter. A successful deletion returns a 204 status with no response body.
