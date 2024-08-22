# Change Log

## 2024-08-22

- Update endpoints
  - POST /api/external/user/chatbot: Setup the chatbot with FormData on create
- Fix
  - PUT /api/external/user/chatbot/{chatbot_id}: Fix the url for HTTP Request

## 2024-07-30

- New endpoints
  - DELETE /api/external/chatbot/webhook
  - DELETE /api/external/chatbot/training_data/{training_data_id}
  - GET /api/external/chatbot/training_data
  - GET /api/external/chatbot/event/{event_id}
- Update endpoints
  - POST /api/external/chatbot/training_data: response `id` and `event_id`
  - POST /api/external/chatbot/model: response `event_id`
- Update webhook messages

## 2024-07-05

- New endpoints
  - GET /api/external/chatbot/model/{model_id}
  - GET /api/external/user/token/refresh
  - GET /api/external/user/chatbot/{chatbot_id}
  - PUT /api/external/user/chatbot/{chatbot_id}
  - DELETE /api/external/user/chatbot/{chatbot_id}
  - GET /api/external/user/plan
- Update endpoints
  - POST /api/external/chatbot/training_data: response `id` (for text) or `event_id` (crawler, upload file)
  - PUT /api/external/chatbot/opentalk: remove parameter `email`
- Remove endpoints
  - PUT /api/external/chatbot: Use PUT /api/external/user/chatbot/{chatbot_id} instead

## 2024-06-28

- New endpoints
  - GET /api/external/user/chatbot
  - POST /api/external/user/chatbot

## 2024-05-09

- Authentication
  - add `caigunn-access-token` for management
- Move endpoints
  - POST /api/external/chatbot/train --> /api/external/chatbot/models
  - PATCH /api/external/chatbot/model_id --> /api/external/chatbot
  - POST /api/external/chatbot/conversation --> /api/external/chatbot/talk
  - GET /api/external/chatbot/conversation_uids --> /api/external/chatbot/uids
- New endpoints
  - PUT /api/external/chatbot/opentalk
  - DELETE /api/external/chatbot/opentalk
  - POST /api/external/chatbot/training_data
  - PUT /api/external/chatbot/webhook

## 2024-01-31

- New endpoint
  - GET /api/external/chatbot/conversation_uids
- Update endpoints
  - POST /api/external/chatbot/conversation: add parameter `nickname`
  - GET /api/external/chatbot/messages: add parameter `nickname`

## 2023-11-10

- New endpoints
  - POST /api/external/chatbot/train
  - GET /api/external/chatbot/models
  - PATCH /api/external/chatbot/model_id
  - POST /api/external/chatbot/conversation
  - GET /api/external/chatbot/messages
