# Send a Message to Microsoft 365 Copilot

Enable conversational experiences powered by Microsoft 365 Copilot. Send user messages and receive AI-generated responses grounded in Microsoft 365 data and user context. Supports multi-turn conversations.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: POST
- **Path**: `/copilot/chat/completions`
- **Operation ID**: `createChatCompletion`
- **Tag**: Chat Completions
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/chat/completions`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scope

- `Copilot.Chat.ReadWrite`

## Request Body

```json
{
  "threadId": "thread-abc-123",
  "messages": [
    {
      "role": "user",
      "content": "What is our company's travel policy for international trips?"
    }
  ]
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `threadId` | string | No | Thread ID for multi-turn conversations |
| `messages` | array | Yes | Array of message objects with role and content |
| `messages[].role` | string | Yes | Role of the message sender (user) |
| `messages[].content` | string | Yes | The message content |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/chat/completions" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{"threadId": "thread-abc-123", "messages": [{"role": "user", "content": "What is our company travel policy for international trips?"}]}'
```

## Example Response

```json
{
  "id": "chatcmpl-001-xyz",
  "threadId": "thread-abc-123",
  "created": "2025-09-10T16:00:00Z",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "Based on your organization's travel policy, international travel requires VP-level approval at least two weeks in advance. The policy also requires booking through the approved travel portal. You can find the full policy in the Employee Handbook on SharePoint."
      },
      "finishReason": "stop"
    }
  ],
  "citations": [
    {
      "id": "cite-001",
      "name": "Employee-Handbook-2025.pdf",
      "webUrl": "https://contoso.sharepoint.com/sites/hr/Employee-Handbook-2025.pdf",
      "snippet": "International travel requires VP-level approval submitted at least 14 calendar days prior to departure."
    }
  ]
}
```

## Instructions

When the user wants to send a message to Microsoft 365 Copilot and get an AI-generated response grounded in organizational data, use this operation by making a POST request to `/copilot/chat/completions`. Provide the messages array with user content. Use a threadId for multi-turn conversations. Responses include citations referencing source documents.
