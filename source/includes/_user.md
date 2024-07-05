# User

## Refresh Caigunn Access Token

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/user/token/refresh?expired_date=EXPIRED_DATE' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/user/token/refresh?expired_date=EXPIRED_DATE"

headers = {"caigunn-access-token": CAIGUNN_ACCESS_TOKEN}

response = requests.request("GET", url, headers=headers)

print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "token": "string"
}
```

Refresh caigunn-access-token.

### HTTP Request

`GET https://caigunn-api.ap-mic.com/api/external/user/token/refresh`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Query Parameters

| Name         | Type | Mandatory | Default | Description |
| ------------ | ---- | --------- | ------- | ----------- |
| expired_date | date | false     |         |             |

## Get Plans

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/user/plan?offset=OFFSET&limit=LIMIT' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/user/plan?offset=OFFSET&limit=LIMIT"

headers = {
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
}

response = requests.request("GET", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "plans": [
    {
      "title": "string",
      "id": "string",
      "crawler_limit": 0,
      "character_limit": 0,
      "training_limit": 0,
      "price": 0
    }
  ]
}
```

This endpoint retrieves all plans.

### HTTP Request

`GET https://caigunn-api.ap-mic.com/api/external/user/plan`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Query Parameters

| Name   | Type    | Mandatory | Default | Description |
| ------ | ------- | --------- | ------- | ----------- |
| offset | integer | false     | 0       |             |
| limit  | integer | false     | 30      |             |

## Create Chatbot

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/user/chatbot?title=TITLE&plan_id=PLAN_ID' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --header 'Content-Type: application/json'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/user/chatbot?title=TITLE&plan_id=PLAN_ID"

headers = {
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
    "Content-Type": "application/json",
}

response = requests.request("POST", url, headers=headers)
print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "api_key": "string",
  "expired_at": "2024-07-05T09:49:32.451Z"
}
```

Create Chatbot.

### HTTP Request

`POST https://caigunn-api.ap-mic.com/api/external/user/chatbot`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Query Parameters

| Name    | Type   | Mandatory | Default | Description |
| ------- | ------ | --------- | ------- | ----------- |
| title   | string | true      |         |             |
| plan_id | uuid   | true      |         |             |

## Get All Chatbots

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/user/chatbot' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/user/chatbot"

headers = {"caigunn-access-token": CAIGUNN_ACCESS_TOKEN}

response = requests.request("GET", url, headers=headers)

print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "chatbots": [
    {
      "id": "string",
      "title": "string",
      "api_key": "string"
    }
  ]
}
```

This endpoint retrieves all chatbots.

### HTTP Request

`GET https://caigunn-api.ap-mic.com/api/external/user/chatbot`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Query Parameters

| Name   | Type    | Mandatory | Default | Description |
| ------ | ------- | --------- | ------- | ----------- |
| offset | integer | false     | 0       |             |
| limit  | integer | false     | 30      |             |

## Get Chatbot Info

```shell
curl --location 'https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests

url = "https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID"

headers = {
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
}

response = requests.request("GET", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "updated_at": "2024-07-05T04:08:48.392Z",
  "created_at": "2024-07-05T04:08:48.392Z",
  "id": "string",
  "title": "string",
  "user_id": "string",
  "is_deleted": true,
  "deleted_at": "2024-07-05T04:08:48.392Z",
  "prompt": "string",
  "temperature": 0,
  "is_ready_for_train": true,
  "is_shared": true,
  "share_link": "string",
  "is_free": true,
  "training_data_type": "file",
  "file_model_id": "string",
  "crawler_model_id": "string",
  "text_model_id": "string",
  "usage_notification": 0,
  "message_limit": 0,
  "character_limit": 0,
  "crawler_limit": 0,
  "training_limit": 0,
  "plan_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "period_start_at": "2024-07-05T04:08:48.392Z",
  "period_end_at": "2024-07-05T04:08:48.392Z",
  "api_key": "string",
  "total_file_size_limit": 0,
  "is_api_accessible": true,
  "model": {
    "id": "string",
    "model_name": "string",
    "embedding_name": "string"
  },
  "opentalk_device_id": "string",
  "opentalk_device_name": "string",
  "opentalk_device_type": "string",
  "bound_at": "2024-07-05T04:08:48.392Z",
  "opentalk_api_token": "string",
  "use_opentalk_conversation": false,
  "opentalk_account": "string",
  "opentalk_user_id": "string",
  "next_plan_id": "string",
  "limits_reset_day": 0,
  "coupon": {},
  "store_source_data": true,
  "is_prompt_template_accessible": true,
  "qa_generate_limit": 0,
  "qa_generate_count": 0,
  "preview_chunks": true,
  "is_chunks_editable": true,
  "opentalk_host": "string",
  "webhook_url": "string"
}
```

This endpoint retrieves detail information of the chatbot.

### HTTP Request

`GET https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID`

### Path Parameters

| Name       | Type   | Mandatory | Default | Description        |
| ---------- | ------ | --------- | ------- | ------------------ |
| chatbot-id | string | true      |         | The ID of chatbot. |

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

## Update Chatbot

```shell
curl --location --request PUT 'https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --header 'Content-Type: application/json' \
    --data '{"webhook_url": WEBHOOK_URL}'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID"

payload = json.dumps({"webhook_url": WEBHOOK_URL})
headers = {
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
    "Content-Type": "application/json",
}

response = requests.request("PUT", url, headers=headers, data=payload)

print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "detail": "update successfully"
}
```

Update chatbot settings

### HTTP Request

`PUT https://caigunn-api.ap-mic.com/api/external/chatbot/webhook`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Request Body Form data

| Name               | Type    | Mandatory | Default | Description                        |
| ------------------ | ------- | --------- | ------- | ---------------------------------- |
| title              | string  | false     |         |                                    |
| avatar             | file    | false     |         |                                    |
| main_color         | string  | false     |         |                                    |
| is_default_visible | boolean | false     |         |                                    |
| button_style       | string  | false     |         | basic, image                       |
| button_image       | file    | false     |         |                                    |
| initial_messages   | array   | false     |         | [{"type":"text","value":"string"}] |
| is_fixed           | bool    | false     |         |                                    |
| show_history       | boolean | false     |         |                                    |
| allowed_domains    | array   | false     |         |                                    |
| model_id           | uuid    | false     |         |                                    |
| prompt             | string  | false     |         |                                    |
| is_shared          | boolean | false     |         |                                    |

## Delete Chatbot

```shell
shell curl --location --request DELETE 'https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID"

headers = {
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
}

response = requests.request("DELETE", url, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
  "detail": "Delete chatbot successfully"
}
```

Delete Chatbot.

### HTTP Request

`DELETE https://caigunn-api.ap-mic.com/api/external/user/chatbot/CHATBOT_ID`

### Path Parameters

| Name       | Type   | Mandatory | Default | Description        |
| ---------- | ------ | --------- | ------- | ------------------ |
| chatbot-id | string | true      |         | The ID of chatbot. |

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |
