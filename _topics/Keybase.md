---
layout: default
title: "Keybase"
---

## Send to chat

You can send to this chat with

```echo '{"method": "send", "params": {"options": {"channel": {"name": "CHAT_GROUP_NAME", "members_type": "team", "topic_name": "CHAT_TOPIC_NAME"}, "message": {"body": "MESSAGE"}}}}' | keybase chat api```

If you have keybase installed on the command line..

## Read from chat

This gets the recent messages:
```echo '{"method": "read", "params": {"options": {"channel": {"name": "CHAT_GROUP_NAME", "members_type": "team", "topic_name": "CHAT_TOPIC_NAME"}}}}' | keybase chat api | jq . > CHAT_TOPIC_NAME.json```