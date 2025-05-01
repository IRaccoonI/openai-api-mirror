# openai-api-mirror

🔁 A simple Nginx-based proxy that forwards HTTP requests from `localhost:8080` to the OpenAI API (`https://api.openai.com`).

## Features

- Transparent proxy to `https://api.openai.com`
- Local development support without CORS issues
- Minimal setup with Docker and Docker Compose

## Usage

### 1. Build and Run the Proxy

```
docker-compose up --build
```

This will start an Nginx container listening on `http://localhost:8080`.

### 2. Send Requests via Proxy

Example `curl` request to OpenAI Chat API through the proxy:

```
curl -X POST http://localhost:8080/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

> 🔐 Make sure to replace `YOUR_API_KEY` with your actual OpenAI API key.

## Files

- `nginx.conf`: Nginx config for proxying requests to api.openai.com
- `Dockerfile`: Container build config
- `docker-compose.yml`: Service definition for easy startup

## License

MIT
