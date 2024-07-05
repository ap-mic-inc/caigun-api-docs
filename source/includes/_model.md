# Model

## Create Training Data

```shell
# Create by files
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/training_data?type=file' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --form 'files=@FILE'

# Create by crawler
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/training_data?type=crawler' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --form 'website="WEBSITE"' \
    --form 'is_single_page="IS_SINGLE_PAGE"'

# Create by text
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/training_data?type=text' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --form 'text=TEXT'

```

```python
# Create by files
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/training_data?type=file"

payload = {"website": WEBSITE, "is_single_page": IS_SINGLE_PAGE}
files = []
headers = {"api-key": CHATBOT_API_KEY, "caigunn-access-token": CAIGUNN_ACCESS_TOKEN}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.json())


# Create by crawler
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/training_data?type=crawler"

payload = {"website": WEBSITE, "is_single_page": IS_SINGLE_PAGE}

headers = {"api-key": CHATBOT_API_KEY, "caigunn-access-token": CAIGUNN_ACCESS_TOKEN}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.json())

# Create by text

import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/training_data?type=file"

payload = {'text': 'TEXT'}

headers = {"api-key": CHATBOT_API_KEY, "caigunn-access-token": CAIGUNN_ACCESS_TOKEN}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.json())

```

> The above command returns JSON structured like this:

```json
# Create by files
{
    "id": "123e4567-e89b-12d3-a456-426655440000"
}

# Create by crawler
{
    "event_id": "123e4567-e89b-12d3-a456-426655440000"
}

# Create by files
{
    "event_id": "123e4567-e89b-12d3-a456-426655440000"
}


```

Create training data for model training. Create training data by crawler or uploading files will be processed in background and the result will be sent to the webhook.

### HTTP Request

`POST https://caigunn-api.ap-mic.com/api/external/chatbot/training_data`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Query Parameters

| Name | Type   | Mandatory | Default | Description         |
| ---- | ------ | --------- | ------- | ------------------- |
| type | string | true      |         | file, crawler, text |

### Request Body Form data

| Name           | Type   | Mandatory | Default | Description                            |
| -------------- | ------ | --------- | ------- | -------------------------------------- |
| website        | string | false     |         | The website for crawling.              |
| is_single_page | bool   | false     |         | Crawl one webpage or the whole website |
| text           | string | false     |         |                                        |
| files          | array  | false     |         |                                        |

## Train a Model

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/model' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --header 'Content-Type: application/json' \
    --data '{"title": TITLE, "model_name": MODEL_NAME}'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/model"

payload = json.dumps({"title": TITLE, "model_name": MODEL_NAME})
headers = {
    "api-key": CHATBOT_API_KEY,
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
    "Content-Type": "application/json",
}

response = requests.request("POST", url, headers=headers, data=payload)
print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "detail": "Training in background"
}
```

Train a model. Result will be sent to the webhook.

### HTTP Request

`POST https://caigunn-api.ap-mic.com/api/external/chatbot/model`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Request Body Schema

| Name       | Type   | Mandatory | Default | Description                                                                                     |
| ---------- | ------ | --------- | ------- | ----------------------------------------------------------------------------------------------- |
| title      | string | true      |         | Title for the trained model.                                                                    |
| model_name | string | false     | "PaLM2" | "PaLM2", "gpt-3.5-turbo", "gpt-4", "Gemini", "Claude 2", "Claude 3", "CaiGunn001", "Gemini 1.5" |

## Get All Models

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/model' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/model"

headers = {"api-key": CHATBOT_API_KEY, "caigunn-access-token": CAIGUNN_ACCESS_TOKEN}

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

`GET http://caigunn-api.ap-mic.com/api/external/chatbot/model`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

## Get Model

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/chatbot/model/MODEL_ID' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/model/MODEL_ID"

headers = {
    "api-key": CHATBOT_API_KEY,
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
}

response = requests.request("GET", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "title": "string",
  "id": "string",
  "updated_at": "2024-07-05T04:19:04.436Z",
  "created_at": "2024-07-05T04:19:04.436Z",
  "model_name": "string",
  "training_data": [
    {
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "title": "string"
    }
  ]
}
```

This endpoint retrieves detail information of the chatbot.

### HTTP Request

`GET https://caigunn-api.ap-mic.com/api/external/chatbot/model/MODEL_ID`

### Path Parameters

| Name     | Type   | Mandatory | Default | Description      |
| -------- | ------ | --------- | ------- | ---------------- |
| model-id | string | true      |         | ID of the model. |

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |
