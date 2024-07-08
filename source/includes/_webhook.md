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

# Webhook Events

## crawling.initial

```json
{
  "event": "crawling",
  "status": "initial",
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
}
```

## crawling.completed

```json
{
  "event": "crawling",
  "status": "completed",
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
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
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
}
```

## uploading.completed

```json
{
  "event": "uploading",
  "status": "completed",
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
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
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "event_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
}
```

## training.initial

```json
{
  "event": "training",
  "status": "initial",
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
}
```

## training.completed

```json
{
  "event": "training",
  "status": "completed",
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "data": {
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
  "chatbot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "detail": ""
}
```
