---
title: REST
menu:
    main:
        parent: integrate
        weight: 4
---

## JSON REST API

Besides the [gRPC]({{< relref "grpc.md" >}}) API, LoRa App Server also provides
a JSON REST API. As this is technically a "gateway" between the gRPC API,
it contains exactly the same calls (using RESTful resources) and exposes the
same fields.

### API console

LoRa App Server comes with an API console (based on Swagger UI) containing all
API endpoints and their documentation. This console is accessible at `/api`.

![Swagger API](/lora-app-server/img/swagger.png)