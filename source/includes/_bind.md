## Bind Opentalk Device

```shell
curl --location --request PUT 'https://caigunn-api.ap-mic.com/api/external/chatbot/opentalk' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --header 'Content-Type: application/json' \
    --data '{"email": OPENTALK_USER_EMAIL, "device_id": OPENTALK_DEVICE_ID}'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/opentalk"

payload = json.dumps({"email": OPENTALK_USER_EMAIL, "device_id": OPENTALK_DEVICE_ID})
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
  "detail": "Bind Opentalk successfully"
}
```

Bind with Opentalk to access device's conversation script, live chat support, and analytics features.

### HTTP Request

`PUT https://caigunn-api.ap-mic.com/api/external/chatbot/opentalk`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |

### Request Body Schema

| Name      | Type   | Mandatory | Default | Description                 |
| --------- | ------ | --------- | ------- | --------------------------- |
| email     | string | true      |         | Email of the Opentalk user. |
| device_id | string | true      |         | ID of the Opentalk device.  |


## Unbind Opentalk Device

```shell
curl --location --request DELETE 'https://caigunn-api.ap-mic.com/api/external/chatbot/opentalk' \
    --header 'api-key: CHATBOT_API_KEY' \
    --header 'caigunn-access-token: CAIGUNN_ACCESS_TOKEN' \
    --header 'Content-Type: application/json'
```

```python
import requests
import json

url = "https://caigunn-api.ap-mic.com/api/external/chatbot/opentalk"

headers = {
    "api-key": CHATBOT_API_KEY,
    "caigunn-access-token": CAIGUNN_ACCESS_TOKEN,
    "Content-Type": "application/json"
}

response = requests.request("DELETE", url, headers=headers)

print(response.json())

```

> The above command returns JSON structured like this:

```json
{
  "detail": "Unbind Opentalk successfully"
}
```

Unbind Opentalk device.

### HTTP Request

`DELETE https://caigunn-api.ap-mic.com/api/external/chatbot/opentalk`

### Header Parameters

| Name                 | Type   | Mandatory | Default | Description           |
| -------------------- | ------ | --------- | ------- | --------------------- |
| api-key              | string | true      |         | API Key.              |
| caigunn-access-token | string | true      |         | Caigunn Access Token. |
