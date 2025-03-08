## Getting Started
- run Docker container

```docker
docker run -d --name mockserver -p 1080:1080 mockserver/mockserver:latest
```

- run Docker container with Expectation Initializers
```
docker run -v $(pwd):/config -p 1080:1080 mockserver/mockserver -serverPort 1080

docker run -d --rm \
  -p 1080:1080 \
  -v $(pwd):/config \
  -e MOCKSERVER_INITIALIZATION_JSON_PATH="/config/initializer.json" \
  mockserver/mockserver
```

- using OpenAPI

```bash
curl -v -X PUT "http://localhost:1080/mockserver/openapi" --data '{"specUrlOrPayload": "https://raw.githubusercontent.com/hylin0524/PocMockServer/refs/heads/main/order.yaml", "operationsAndResponses": {"getOrderStatusById": "200"}}'
```

- Create Expectations: [link](https://www.mock-server.com/mock_server/creating_expectations.html)


- check mockserver status & expectation list
  - `http://localhost:1080/mockserver/dashboard`
