# Webhook

## Subscribe Webhook

```shell
curl --location --request PUT 'https://caigunn-api.ap-mic.com/api/external/chatbot/webhook' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --header 'Content-Type: application/json' \
    --data '{"webhook_url": WEBHOOK_URL}'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/webhook"

payload = json.dumps({"webhook_url": WEBHOOK_URL})
headers = {
    "api-key": CHATBOT_API_KEY,
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
    "Content-Type": "application/json",
}

response = requests.request("PUT", url, headers=headers, data=payload)

print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "detail": "Webhook url update successfully"
}
```

Set webhook url to subscribe chatbot events.

### HTTP Request

`PUT https://caigunn-api.ap-mic.com/api/external/chatbot/webhook`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Request Body Schema

| Name        | Type   | Mandatory | Default | Description                                 |
| ----------- | ------ | --------- | ------- | ------------------------------------------- |
| webhook_url | string | true      |         | Webhook url for chatbot event subscripiton. |

## Unsubscribe Webhook

```shell
curl --location --request DELETE 'https://caigunn-api.ap-mic.com/api/external/chatbot/webhook' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/webhook"

headers = {
    "api-key": CHATBOT_API_KEY,
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN
}

response = requests.request("DELETE", url, headers=headers)

print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "detail": "Unsubscribe webhook successfully"
}
```

Unsubscribe webhook.

### HTTP Request

`DELETE https://caigunn-api.ap-mic.com/api/external/chatbot/webhook`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

## Get Events by Event ID

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/event/{EVENT_ID}' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'

```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/event/{EVENT_ID}"

headers = {"api-key": CHATBOT_API_KEY, "caigunn-access-token": CAIGUNN_ACCESS_TOKEN}

response = requests.request("GET", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "webhook_logs": [
    {
      "created_at": "2024-07-30T07:48:56.065248Z",
      "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "event": "crawling",
      "status": "initial",
      "data": {
        "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
      },
      "broadcast_status": "completed"
    },
    {
      "created_at": "2024-07-30T07:50:03.500039Z",
      "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "event": "crawling",
      "status": "completed",
      "data": {
        "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "training_data_ids": ["3fa85f64-5717-4562-b3fc-2c963f66afa6"]
      },
      "broadcast_status": "completed"
    }
  ]
}
```

List all training data which will be used in next training.

### HTTP Request

`GET https://caigunn-api.ap-mic.com/api/external/chatbot/event/{EVENT_ID}`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Path Parameters

| Name     | Type | Mandatory | Default | Description |
| -------- | ---- | --------- | ------- | ----------- |
| event_id | uuid | true      |         | Event ID.   |

# Webhook Events

## crawling.initial

```json
{
  "event": "crawling",
  "status": "initial",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
  }
}
```

## crawling.completed

```json
{
  "event": "crawling",
  "status": "completed",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "training_data_ids": [
      "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "3fa85f64-5717-4562-b3fc-2c963f66afa6"
    ]
  }
}
```

## uploading.initial

```json
{
  "event": "uploading",
  "status": "initial",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
  }
}
```

## uploading.completed

```json
{
  "event": "uploading",
  "status": "completed",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "training_data_ids": [
      {
        "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "filename": "filename"
      },
      {
        "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "filename": "filename",
        "status": "failed",
        "detail": "Unsupport file format"
      }
    ]
  }
}
```

## uploading.failed

```json
{
  "event": "uploading",
  "status": "failed",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
  }
}
```

## training.initial

```json
{
  "event": "training",
  "status": "initial",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
  }
}
```

## training.completed

```json
{
  "event": "training",
  "status": "completed",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "model_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "training_data_ids": [
      "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "3fa85f64-5717-4562-b3fc-2c963f66afa6"
    ]
  }
}
```

## training.failed

| Detail                   |
| ------------------------ |
| Training data not found  |
| Character limit exceeded |

```json
{
  "event": "training",
  "status": "failed",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
    "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "detail": ""
  }
}
```
