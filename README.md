# openai-api-mirror

A simple Nginx-based proxy that forwards HTTP requests from `localhost:8080` to the OpenAI API (`https://api.openai.com`).

## Docker Image

Pull the image from Docker Hub:

```
docker pull iraccooni/openai-api-mirror
```

Run the container:

```
docker run -p 8080:8080 iraccooni/openai-api-mirror
```

## Example docker-compose

```yaml
services:
  openai-proxy:
    image: iraccooni/openai-api-mirror
    ports:
      - "8080:8080"
```

## Example Request

```
curl -X POST http://localhost:8080/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

Replace `YOUR_API_KEY` with your actual OpenAI API key.
