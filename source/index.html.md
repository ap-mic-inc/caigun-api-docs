---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell: cURL
  - python: Python-Request

toc_footers:
  - <a href='https://caigun.ap-mic.com'>Sign Up for an API Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - model
  - message
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the CaiGun API
---

# Introduction

Welcome to the CaiGun API! You can use our API to setup and interact with chatbot.

We have language bindings in Shell and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication


CaiGun uses API keys to allow access to the API. You can register and create chatbot at [CaiGun](https://caigun.ap-mic.com).

CaiGun API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`api-key: CHATBOT_API_KEY`

<aside class="notice">
You must replace <code>CHATBOT_API_KEY</code> with your personal API key.
</aside>
