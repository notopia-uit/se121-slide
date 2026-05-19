---
layout: center
class: text-center
transition: slide-up
---

## Setup

---
hideInToc: true
---

### Health - Startup

```json
{
  "status": "up",
  "details": {
    "persistenceMigration": {
      "status": "up",
      "timestamp": "2026-05-19T08:06:45.31010631Z"
    }
  }
}
```

`http://api.notopia.localhost/note/health/startup`

---
hideInToc: true
layout: two-cols
---

### Health - Ready

```json
{
  "status": "down",
  "details": {
    "authentik": {
      "status": "down",
      "timestamp": "2026-05-19T08:05:14.841142259Z",
      "error": "making the request for the health check failed: Get \"http://authentik.notopia.localhost/-/health/live\": dial tcp [::1]:80: connect: connection refused"
    },
    "authorizationService": {
      "status": "down",
      "timestamp": "2026-05-19T08:05:14.840856216Z",
      "error": "making the request for the health check failed: Get \"http://localhost:28089/authorization/health/live\": dial tcp [::1]:28089: connect: connection refused"
    },
    "grpc": {
      "status": "up",
      "timestamp": "2026-05-19T08:05:14.840692045Z"
    }
  }
}
```

::right::

```json
{
  "status": "down",
  "details": {
    "http": {
      "status": "up",
      "timestamp": "2026-05-19T08:05:14.840871465Z"
    },
    "kafka": {
      "status": "up",
      "timestamp": "2026-05-19T08:05:14.84080603Z"
    },
    "persistenceConnection": {
      "status": "up",
      "timestamp": "2026-05-19T08:05:14.840665763Z"
    },
    "workspaceEventHubRedisConnection": {
      "status": "up",
      "timestamp": "2026-05-19T08:05:14.841261038Z"
    }
  }
}
```

`http://api.notopia.localhost/note/health/ready`

<!--
Sử dụng thư viện hỗ trợ async và sync health check.

Với async, đồng nghĩa với việc cache, interval check và lưu cache
-->

---
hideInToc: true
---

### Health - Live

```json
{
  "status": "up"
}
```

`http://api.notopia.localhost/note/health/live`

<!--
Live là endpoint check nhẹ, xem process còn sống không. Có thể sử dụng TCP connection response lại cũng được. Nhưng để dễ dàng dev cũng như sử dụng có sẵn của thư viện.
-->
