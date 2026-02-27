# Get a Chat Thread

Retrieve details of an existing conversational thread with Microsoft 365 Copilot.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/chat/threads/{threadId}`
- **Operation ID**: `getChatThreadById`
- **Tag**: Chat Completions
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/chat/threads/{threadId}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.Chat.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `threadId` | path | string | Yes | Unique identifier of the chat thread |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/chat/threads/thread-abc-123" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "thread-abc-123",
  "displayName": "Travel Policy Questions",
  "createdDateTime": "2025-09-10T16:00:00Z",
  "lastUpdatedDateTime": "2025-09-10T16:45:00Z"
}
```

## Instructions

When the user wants to retrieve details about an existing chat thread, use this operation by making a GET request to `/copilot/chat/threads/{threadId}`. Provide the thread ID as a path parameter. This returns the thread metadata including display name and timestamps.
