# Model

## Train a Model

```shell
curl --location 'https://caigun-api.ap-mic.com/api/chatbot/train' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'Content-Type: application/json' \
    --data '{"text": TEXT, "title": TITLE, "model_name": MODEL_NAME}'
```

```python
import requests

url = "https://caigun-api.ap-mic.com/api/chatbot/train"

payload = "{\"text\": TEXT, \"title\": TITLE, \"model_name\": MODEL_NAME}"
headers = {
  'api-key': 'CHATBOT_API_KEY',
  'Content-Type': 'application/json'
}

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

`POST https://caigun-api.ap-mic.com/api/external/chatbot/train`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| api-key | string | true      |         | API Key.    |

### Request Body Schema

| Name       | Type   | Mandatory | Default      | Description                                                  |
| ---------- | ------ | --------- | ------------ | ------------------------------------------------------------ |
| text       | string | true      |              | Text for model training.                                     |
| title      | string | true      |              | Title for the trained model.                                 |
| model_name | string | false     | "chat-bison" | "chat-bison", "azure-gpt-3.5-turbo-0613", "azure-gpt-4-0613" |

## Get All Models

```shell
curl --location 'https://caigun-api.ap-mic.com/api/external/chatbot/models' \
    --header 'api-key: CHATBOT_API_KEY'
```

```python
import requests

url = "https://caigun-api.ap-mic.com/api/external/chatbot/models"

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

`GET http://caigun-api.ap-mic.com/api/external/chatbot/models`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| api-key | string | true      |         | API Key.    |

## Update Chatbot Model

```shell
curl --location --request PATCH 'https://caigun-api.ap-mic.com/api/external/chatbot/model_id' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'Content-Type: application/json' \
    --data '{"id": MODEL_ID}'
```

```python
import requests

url = "https://caigun-api.ap-mic.com/api/external/chatbot/model_id"

payload = '{"id": MODEL_ID}'
headers = {"api-key": "CHATBOT_API_KEY", "Content-Type": "application/json"}

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

`PATCH https://caigun-api.ap-mic.com/api/external/chatbot/model_id`

### Header Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| api-key | string | true      |         | API Key.    |

### Request Body Schema

| Name | Type   | Mandatory | Default | Description |
| ---- | ------ | --------- | ------- | ----------- |
| id   | string | true      |         | Model id.   |
