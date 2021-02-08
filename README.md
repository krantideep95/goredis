# goredis
a middleware for goredis to use opentracing

```go
import (
	"net/http"

	"github.com/go-redis/redis/v8"

	otredis "github.com/krantideep95/goredis"
)

var redisClient *redis.Client // initialized at program startup

func handleRequest(w http.ResponseWriter, req *http.Request) {
	// Wrap and bind redisClient to the request context. If the HTTP
	// server is instrumented with Elastic APM (e.g. with apmhttp),
	// Redis commands will be reported as spans within the request's
	// transaction.
	client := otredis.Wrap(redisClient, nil).WithContext(req.Context())
	...
}
```

Example: [goredis-example](./examples)

![](./examples/imgs/img1.jpg)

![](./examples/imgs/img2.jpg)
