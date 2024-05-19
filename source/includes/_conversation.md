## Talk With Chatbot

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/talk&nickname=NICKNAME' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'uid: CUSTUM_UID' \
    --header 'Content-Type: application/json' \
    --data '{"text": TEXT}'
```

```python
import requests
import json

url = "http://caigunn-api.ap-mic.com/api/external/chatbot/talk&nickname=NICKNAME"

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

`POST https://caigunn-api.ap-mic.com/api/external/chatbot/talk`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description                           |
| ------- | ------ | --------- | ------- | ------------------------------------- |
| api-key | string | true      |         | API Key.                              |
| uid     | string | true      |         | Custom UID for identify conversation. |

### Query Parameters

| Name     | Type   | Mandatory | Default | Description                               |
| -------- | ------ | --------- | ------- | ----------------------------------------- |
| nickname | string | false     |         | Nickname of the conversation participant. |

### Request Body Schema

| Name | Type   | Mandatory | Default | Description                                |
| ---- | ------ | --------- | ------- | ------------------------------------------ |
| text | string | true      |         | Message from the conversation participant. |

## Get Historical Messages

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/messages?offset=OFFSET&limit=LIMIT&start_at=START_AT&end_at=END_AT&nickname=NICKNAME' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'uid: CUSTUM_UID'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/messages?offset=OFFSET&limit=LIMIT&start_at=START_AT&end_at=END_AT&nickname=NICKNAME"

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

`GET https://caigunn-api.ap-mic.com/api/external/chatbot/messages`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description                           |
| ------- | ------ | --------- | ------- | ------------------------------------- |
| api-key | string | true      |         | API Key.                              |
| uid     | string | true      |         | Custom UID for identify conversation. |

### Query Parameters

| Name     | Type     | Mandatory | Default | Description                               |
| -------- | -------- | --------- | ------- | ----------------------------------------- |
| offset   | integer  | false     | 0       |                                           |
| limit    | integer  | false     | 30      |                                           |
| start_at | datetime | false     |         |                                           |
| end_at   | datetime | false     |         |                                           |
| nickname | string   | false     |         | Nickname of the conversation participant. |

## Get Conversation UIDs

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/uids?offset=OFFSET&limit=LIMIT&start_at=START_AT&end_at=END_AT' \
    --header 'api-key: CHATBOT_API_KEY'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/uids?offset=OFFSET&limit=LIMIT&start_at=START_AT&end_at=END_AT"

headers = {"api-key": CHATBOT_API_KEY, "uid": CUSTUM_UID}

response = requests.request("GET", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "uids": [
    {
      "uid": "string",
      "nickname": "string",
      "source": "string",
      "last_sent": "string",
      "last_sent_at": "string"
    }
  ]
}
```

This endpoint retrieves conversation UIDs.

### HTTP Request

`GET https://caigunn-api.ap-mic.com/api/external/chatbot/uids`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| api-key | string | true      |         | API Key.    |

### Query Parameters

| Name     | Type     | Mandatory | Default          | Description                                                    |
| -------- | -------- | --------- | ---------------- | -------------------------------------------------------------- |
| offset   | integer  | false     | 0                |                                                                |
| limit    | integer  | false     | 30               |                                                                |
| start_at | datetime | false     | 1970-1-1         | Get UIDs where last_sent_at is greater than or equal start_at. |
| end_at   | datetime | false     | current datetime | Get UIDs where last_sent_at is less than or equal end_at.      |
