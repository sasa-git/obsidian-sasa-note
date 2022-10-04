[Docker hub](https://hub.docker.com/_/redis?tab=description)

compose example

```
  redis:
    image: "redis:6.2"
    volumes:
      - sample-redis-local-data:/data
    ports:
      - 6379:6379
    networks:
      - sample-web-network
```