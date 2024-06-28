# User

## Get All Chatbots

```shell
curl --location --request GET 'https://caigunn-api.ap-mic.com/api/external/user/chatbot?offset=OFFSET&limit=LIMIT' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --header 'Content-Type: application/json'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/user/chatbot?offset=OFFSET&limit=LIMIT"

headers = {
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
    "Content-Type": "application/json",
}

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

Get all chatbots.

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

## Create Chatbot

```shell
curl --location --request POST 'https://caigunn-api.ap-mic.com/api/external/user/chatbot?title=TITLE&plan_id=PLAN_ID' \
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
  "expired_at": "2024-06-28T09:58:01.364Z"
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

| Name    | Type   | Mandatory | Default | Description           |
| ------- | ------ | --------- | ------- | --------------------- |
| title   | string | true      |         | Name of the chatbot.  |
| plan_id | uuid   | true      |         | Plan for the chatbot. |
