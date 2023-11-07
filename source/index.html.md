---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell: cURL
  - python: Python-Request

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the CaiGun API
---

# Introduction

Welcome to the CaiGun API! You can use our API to access CaiGun API endpoints.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:


```shell
curl "api_endpoint_here" \
  -H "api-key: CHATBOT_API_KEY"
```

```python
import requests

url = "api_endpoint_here"
headers = {
    "api-key": "CHATBOT_API_KEY"
}

response = requests.get(url, headers=headers)
```



> Make sure to replace `CHATBOT_API_KEY` with your API key.

CaiGun uses API keys to allow access to the API. You can register a new API key at our [developer portal](https://caigun.ap-mic.com).

CaiGun API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`api-key: CHATBOT_API_KEY`

<aside class="notice">
You must replace <code>CHATBOT_API_KEY</code> with your personal API key.
</aside>

# Chatbot

## Train a Model

```shell
curl -X 'POST' \
  'https://caigun-api.ap-mic.com/api/external/chatbot/train' \
  -H 'accept: application/json' \
  -H 'api-key: CHATBOT_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{
  "text": TEXT,
  "title": TITLE,
  "model_name": MODEL_NAME
}'
```

```python
import requests
import json

url = "https://caigun-api.ap-mic.com/api/chatbot/train"

payload = "{\n  \"text\": TEXT,\n  \"title\": TITLE,\n  \"model_name\": MODEL_NAME\n}"
headers = {
  'api-key': 'CHATBOT_API_KEY',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

> The above command returns JSON structured like this:

```json
{
  "id": "11111111-1111-1111-1111-111111111111"
}
```

### HTTP Request

`POST https://caigun-api.ap-mic.com/api/external/chatbot/train`

### Request Body

Name | Type | Mandatory | Default | Description
--------- | ------- | ------- | ------- | -----------
text | string | true || Text for model training.
title | string | true || Title for the trained model.
model_name | string | false | "PaLM2" | "PaLM2", "gpt2"

## Get All Models

```shell
curl "http://caigun-api.ap-mic.com/api/external/chatbot/models" \
  -H "api-key: CHATBOT_API_KEY"
```

```python
import requests

url = "http://caigun-api.ap-mic.com/api/external/chatbot/models"
headers = {
    "api-key": "CHATBOT_API_KEY"
}

response = requests.get(url, headers=headers)
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
      "model_name": "PaLM2",
      "training_data_type": "file"
    }
  ]
}
```

This endpoint retrieves all models.

### HTTP Request

`GET http://caigun-api.ap-mic.com/api/external/chatbot/models`

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>