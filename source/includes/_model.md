# Model

## Train a Model

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/train' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'Content-Type: application/json' \
    --data '{"text": TEXT, "title": TITLE, "model_name": MODEL_NAME}'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/train"

payload = json.dumps(
    {"text": TEXT, "title": TITLE, "model_name": MODEL_NAME}
)
headers = {"api-key": CHATBOT_API_KEY, "Content-Type": "application/json"}

response = requests.request("POST", url, headers=headers, data=payload)
print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "id": "11111111-1111-1111-1111-111111111111"
}
```

Train a model by text content.

### HTTP Request

`POST https://caigunn-api.ap-mic.com/api/external/chatbot/train`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| api-key | string | true      |         | API Key.    |

### Request Body Schema

| Name       | Type   | Mandatory | Default      | Description                       |
| ---------- | ------ | --------- | ------------ | --------------------------------- |
| text       | string | true      |              | Text for model training.          |
| title      | string | true      |              | Title for the trained model.      |
| model_name | string | false     | "PaLM2"      | "PaLM2", "gpt-3.5-turbo", "gpt-4" |

## Get All Models

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/models' \
    --header 'api-key: CHATBOT_API_KEY'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/models"

headers = {"api-key": "CHATBOT_API_KEY"}

response = requests.request("GET", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "models": [
    {
      "title": "string",
      "id": "string",
      "updated_at": "2023-11-06T09:09:41.552Z",
      "created_at": "2023-11-06T09:09:41.552Z",
      "model_name": "chat-bison"
    }
  ]
}
```

This endpoint retrieves all models.

### HTTP Request

`GET http://caigunn-api.ap-mic.com/api/external/chatbot/models`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| api-key | string | true      |         | API Key.    |

## Update Chatbot Model

```shell
curl --location --request PATCH 'https://caigunn-api.ap-mic.com/api/external/chatbot/model_id' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'Content-Type: application/json' \
    --data '{"id": MODEL_ID}'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/model_id"

payload = json.dumps({"id": MODEL_ID})
headers = {"api-key": CHATBOT_API_KEY, "Content-Type": "application/json"}

response = requests.request("PATCH", url, headers=headers, data=payload)
print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "detail": "Update successfully"
}
```

This endpoint updates the model of chatbot.

### HTTP Request

`PATCH https://caigunn-api.ap-mic.com/api/external/chatbot/model_id`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| api-key | string | true      |         | API Key.    |

### Request Body Schema

| Name | Type   | Mandatory | Default | Description |
| ---- | ------ | --------- | ------- | ----------- |
| id   | string | true      |         | Model id.   |
