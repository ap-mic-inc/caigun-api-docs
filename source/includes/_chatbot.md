# Chatbot

## Create/Update webhook

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

