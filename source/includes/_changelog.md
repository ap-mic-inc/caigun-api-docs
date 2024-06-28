# Change Log

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
