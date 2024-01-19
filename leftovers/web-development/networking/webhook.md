# 🪝 Webhook

links - [https://webhook.site/](https://webhook.site/)

A webhook is an HTTP-based callback function that allows lightweight, event-driven communication between 2 application programming interfaces (APIs).

To set up a webhook, the client gives a unique URL to the server API and specifies which event it wants to know about. Once the webhook is set up, the client no longer needs to poll the server; the server will automatically send the relevant payload to the client’s webhook URL when the specified event occurs.&#x20;

Webhooks are often protected with Mutual Transport Layer Security (mTLS) authentication, which verifies both client and server before the payload is sent. It is also common for client apps to use SSL encryption for the webhook URL, to ensure the transferred data remains private.\
