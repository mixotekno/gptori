<h1 align="center">ChatGPT Mirror</h1>

[![Docker](https://img.shields.io/docker/pulls/dairoot/chatgpt-mirror?label=ChatGPT-Mirror&logo=docker)](https://hub.docker.com/r/dairoot/chatgpt-mirror)
[![License](https://img.shields.io/github/license/dairoot/ChatGPT-Mirror)](https://github.com/dairoot/ChatGPT-Mirror/blob/main/LICENSE)

ChatGPT Mirror backend is a ChatGPT mirror station, allowing multiple accounts to share management. Enable multiple people to use ChatGPT services at the same time.

## Features

- Provides the same ultimate experience as the official website.
- Provide ChatGPT chat interface to API `/v1/chat/completions`
- Users can easily access and use all functions of ChatGPT official website without going through the firewall.
- By entering `ChatGPT Token` in the `Mirror` background, each team member can have an independent account (or share the same `ChatGPT Plus` account).
- Provide a convenient management background to help administrators manage accounts efficiently.

## Online experience

https://chatgpt.dairoot.cn

## Deployment

For the best experience, please watch the following video tutorial first

https://github.com/user-attachments/assets/7b868672-cfaf-430c-9ec4-f1617a428225

<!--
<a href="https://www.bilibili.com/video/BV1fD421M7xP/" target="_blank">
<img src="./docs/img/cover.jpeg" alt="How to use">
</a>
-->

Open the command line terminal and execute the following command

```bash
# Switch to the home directory and clone the ChatGPT-Mirror repository
cd /home/ && git clone https://github.com/dairoot/ChatGPT-Mirror.git

cd ChatGPT-Mirror/

# Modify the management backend account password
cp .env.example .env && vi .env

# Start
./deploy.sh

```
Visit http://127.0.0.1:50002 or http://external ip:50002

To configure the domain name, please click to view [Complete deployment process](./docs/deploy.md)

## Environment variables

<table>
<tr align="left">
<th>Category</th>
<th>Variable name</th>
<th>Type</th>
<th>Default value</th>
<th>Description</th>
</tr>
<tr align="left">
<td rowspan="4">Mirror background</td>
<td><code>ADMIN_USERNAME</code></td>
<td><code>String</code></td>
<td><code>None</code></td>
<td>Admin background account</td>
</tr>
<tr align="left">
<td><code>ADMIN_PASSWORD</code></td>
<td><code>String</code></td>
<td><code>None</code></td>
<td>Admin backend password</td>
</tr>
<tr align="left">
<td><code>ALLOW_REGISTER</code></td>
<td><code>Boolean</code></td>
<td><code>true</code></td>
<td>Is registration allowed</td>
</tr>
<tr align="left">
<td><code>WEB_HATD</code></td>
<td><code>Boolean</code></td>
<td><code>false</code></td>
<td>WEB opens temporary chat (chat history is not saved)</td>
</tr>
<tr align="left">
<td rowspan="3">API related</td>
<td><code>ENABLE_MIRROR_API</code></td>
<td><code>Boolean</code></td>
<td><code>true</code></td>
<td>Whether to enable API access</td>
</tr>
<tr align="left">
<td><code>MIRROR_API_PREFIX</code></td>
<td><code>String</code></td>
<td><code>None</code></td>
<td>API access prefix, recommended configuration</td>
</tr>
<tr align="left">
<td><code>API_HATD</code></td>
<td><code>Boolean</code></td>
<td><code>false</code></td>
<td>API enables temporary chat (chat history is not saved)</td>
</tr>
<tr align="left">
<td rowspan="3">System variables</td>
<td><code>PROXY_URL_POOL</code></td>
<td><code>String</code></td>
<td><code>None</code></td>
<td>Proxy pool link, multiple proxies are separated by commas<br><code>http://username:password@ip:port,</code><br/><code>socks5://username:password@ip:port,</code><br/><code>socks5h://username:password@ip:port</code></td>
</tr>
<tr align="left">
<td><code>VOICE_PROXY_URL</code></td>
<td><code>String</code></td>
<td><code>None</code></td>
<td>Voice proxy address <a href="./docs/livekit.md">Click to build it yourself</a><br>If not configured, users need to bypass the firewall to use the voice function</td>
</tr>
</table>

# Chat API interface

Can be used with [ChatGPT-Next-Web](https://app.nextchat.dev), [Lobe-Chat](https://github.com/lobehub/lobe-chat)
```
AccessToken acquisition address: https://chatgpt.com/api/auth/session

API address: https://your address
```

Chat interface request example:

```bash
export accessToken=XXXXX # Get address: https://chatgpt.com/api/auth/session
export yourUrl=http://127.0.0.1:50002

curl --location "${yourUrl}/v1/chat/completions" \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer ${accessToken}" \
--data '{
"model": "gpt-4o-mini",
"messages": [{"role": "user", "content": "Hello!"}],
"stream": true,
"conversation_id": null,
"parent_message_id": null,
"hatd": false
}'
```

For more APIs, please click: [Advanced Play](./docs/chatapi-gateway.md)

## FQA

[Simplified Chinese > Frequently Asked Questions](./docs/faq-cn.md)

## Join Group Chat

[Telegram](https://t.me/+34aYksZdq5ZhMzhl)

## Donate

[Buy Me a Coffee](./docs/donation.md) ## Star History ![Star History Chart](https://api.star-history.com/svg?repos=dairoot/ChatGPT-Mirror&type=Timeline)
