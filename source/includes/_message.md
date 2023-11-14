# Message

## Conversation With Chatbot

```shell
curl --location 'https://caigun-api.ap-mic.com/api/external/chatbot/conversation' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'uid: CUSTUM_UID' \
    --header 'Content-Type: application/json' \
    --data '{"text": TEXT}'
```

```python
import requests
import json

url = "http://caigun-api.ap-mic.com/api/external/chatbot/conversation"

payload = json.dumps({"text": TEXT})
headers = {"api-key": CHATBOT_API_KEY, "uid": CUSTUM_UID, "Content-Type": "application/json"}

response = requests.request("POST", url, headers=headers, data=payload)
print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "text": "string"
}
```

Send message to chatbot and get response.

### HTTP Request

`POST https://caigun-api.ap-mic.com/api/external/chatbot/conversation`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description                           |
| ------- | ------ | --------- | ------- | ------------------------------------- |
| api-key | string | true      |         | API Key.                              |
| uid     | string | true      |         | Custom UID for identify conversation. |

## Get Historical Messages

```shell
curl --location 'https://caigun-api.ap-mic.com/api/external/chatbot/messages?offset=OFFSET&limit=LIMIT&start_at=START_AT&end_at=END_AT' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'uid: CUSTUM_UID'
```

```python
import requests

url = "https://caigun-api.ap-mic.com/api/external/chatbot/messages?offset=OFFSET&limit=LIMIT&start_at=START_AT&end_at=END_AT"

headers = {"api-key": CHATBOT_API_KEY, "uid": CUSTUM_UID}

response = requests.request("GET", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "messages": [
    {
      "created_at": "2019-08-24T14:15:22Z",
      "receive": "string",
      "send": "string",
      "type": "text",
      "id": "string",
      "log_type": "string",
      "kwargs": {}
    }
  ]
}
```

This endpoint retrieves historical messages from a conversation.

### HTTP Request

`GET https://caigun-api.ap-mic.com/api/external/chatbot/messages`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description                           |
| ------- | ------ | --------- | ------- | ------------------------------------- |
| api-key | string | true      |         | API Key.                              |
| uid     | string | true      |         | Custom UID for identify conversation. |

### Query Parameters

| Name     | Type     | Mandatory | Default | Description |
| -------- | -------- | --------- | ------- | ----------- |
| offset   | integer  | false     | 0       |             |
| limit    | integer  | false     | 30      |             |
| start_at | datetime | false     |         |             |
| end_at   | datetime | false     |         |             |
