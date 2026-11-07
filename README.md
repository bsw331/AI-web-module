# Zhiwen AI Chat

A lightweight, single-file AI chat interface. Configure an API key, model, and endpoint to chat with any provider that supports the OpenAI-compatible Chat Completions API and server-sent event (SSE) streaming.

The interface is available in English and Simplified Chinese.

## Features

- Single HTML file; no build step, dependencies, or backend required.
- OpenAI-compatible API endpoint, model, and API key configuration.
- Streaming assistant responses, conversation context, and quick-start prompts.
- English and Simplified Chinese interface; language preference is remembered.
- API keys stay in page memory and are cleared when the page is refreshed or closed.

## Getting started

1. Download or clone this project.
2. Open `index.html` in a modern browser. If your provider does not allow requests from a `file://` page, serve the file from a local web server instead.
3. Select **API settings** and enter your API key, model name, and chat completions endpoint.
4. Save the settings and start chatting.

The default model is `gpt-4o-mini`, and the default endpoint is `https://api.openai.com/v1/chat/completions`. Change these to match your provider.

## API compatibility

The configured endpoint should accept a `POST` request with a JSON body containing `model`, `messages`, and `stream: true`, and return an OpenAI-compatible streaming response. The page sends the key as a Bearer token in the `Authorization` header.

Because requests are made directly from the browser, the provider must allow the page's origin through its CORS policy. A network or CORS error may prevent the browser from reaching an otherwise valid endpoint.

## Security notes

- This is a browser-only client, not a secure proxy. Your API key is sent to the configured endpoint and can be accessed by scripts running in the page. Use it only in a page and device you trust.
- The API key is not written to browser storage; it remains in memory until the page is refreshed or closed.
- The model name and API endpoint are saved in `localStorage` on the current browser.
- Do not publish a copy of this page with a personal API key embedded in it. For a public or multi-user deployment, use a backend to protect credentials and enforce access controls.

## License

This project is distributed under the MIT License. See [LICENSE](./LICENSE).
