# Get AI-Generated Meeting Insights

Extract AI-generated meeting notes, action items, decisions, and discussion topics for a specific Teams meeting. Useful for integrating with project management tools, CRM systems, or custom workflows.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/meetings/{meetingId}/insights`
- **Operation ID**: `getMeetingInsightsById`
- **Tag**: Meeting Insights
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/meetings/{meetingId}/insights`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.MeetingInsights.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `meetingId` | path | string | Yes | The unique identifier of the Teams meeting |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/meetings/meeting-xyz-789/insights" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "meetingId": "meeting-xyz-789",
  "subject": "Q3 Product Roadmap Review",
  "startDateTime": "2025-09-10T14:00:00Z",
  "endDateTime": "2025-09-10T15:00:00Z",
  "summary": "The team reviewed the Q3 product roadmap, confirmed the launch date for the new dashboard feature, and discussed resource allocation for the mobile app initiative.",
  "topics": [
    {
      "id": "topic-001",
      "title": "Dashboard Feature Launch",
      "description": "Discussion of the new analytics dashboard feature timeline and QA readiness.",
      "timestamp": "00:05:30"
    },
    {
      "id": "topic-002",
      "title": "Mobile App Resource Allocation",
      "description": "Review of staffing needs for the mobile app initiative in Q4.",
      "timestamp": "00:25:00"
    }
  ],
  "actionItems": [
    {
      "id": "action-001",
      "description": "Finalize QA test plan for the dashboard feature by end of week.",
      "assignedTo": {
        "userId": "user-abc-123",
        "displayName": "Jane Doe"
      },
      "dueDate": "2025-09-14",
      "status": "pending"
    },
    {
      "id": "action-002",
      "description": "Draft resource request for two additional mobile developers.",
      "assignedTo": {
        "userId": "user-def-456",
        "displayName": "John Smith"
      },
      "dueDate": "2025-09-17",
      "status": "pending"
    }
  ],
  "decisions": [
    {
      "id": "decision-001",
      "description": "Dashboard feature launch confirmed for October 1, 2025.",
      "madeBy": {
        "userId": "user-ghi-789",
        "displayName": "Maria Garcia"
      }
    }
  ],
  "participants": [
    {
      "userId": "user-ghi-789",
      "displayName": "Maria Garcia",
      "role": "organizer"
    },
    {
      "userId": "user-abc-123",
      "displayName": "Jane Doe",
      "role": "presenter"
    },
    {
      "userId": "user-def-456",
      "displayName": "John Smith",
      "role": "attendee"
    }
  ]
}
```

## Instructions

When the user wants to get AI-generated insights from a Teams meeting including summaries, topics, action items, decisions, and participants, use this operation by making a GET request to `/copilot/meetings/{meetingId}/insights`. Provide the meeting ID as a path parameter.
