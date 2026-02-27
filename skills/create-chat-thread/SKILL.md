# Create a New Chat Thread

Create a new conversational thread with Microsoft 365 Copilot for multi-turn interactions.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: POST
- **Path**: `/copilot/chat/threads`
- **Operation ID**: `createChatThread`
- **Tag**: Chat Completions
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/chat/threads`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scope

- `Copilot.Chat.ReadWrite`

## Request Body

```json
{
  "displayName": "Travel Policy Questions"
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `displayName` | string | No | A display name for the chat thread |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/chat/threads" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{"displayName": "Travel Policy Questions"}'
```

## Example Response

```json
{
  "id": "thread-abc-123",
  "displayName": "Travel Policy Questions",
  "createdDateTime": "2025-09-10T16:00:00Z",
  "lastUpdatedDateTime": "2025-09-10T16:00:00Z"
}
```

## Instructions

When the user wants to start a new multi-turn conversation with Microsoft 365 Copilot, use this operation by making a POST request to `/copilot/chat/threads`. Optionally provide a display name for the thread. Use the returned thread ID in subsequent chat completion requests for multi-turn conversations.
