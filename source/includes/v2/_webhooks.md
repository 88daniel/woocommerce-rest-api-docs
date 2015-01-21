# Webhooks #

This section lists all API that can be used to create, edit or otherwise manipulate webhooks.

## Webhooks Properties ##

|   Attribute    |   Type  |                                                                                                       Description                                                                                                       |
| -------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`           | integer | The webhook ID (post ID) <i class="label label-info">read-only</i>                                                                                                                                                      |
| `name`         | string  | A friendly name for the webhook, defaults to "Webhook created on &lt;date&gt;"                                                                                                                                          |
| `status`       | string  | Webhook status, options are `active` (delivers payload), `paused` (does not deliver), or `disabled` (does not deliver due delivery failures)                                                                            |
| `topic`        | string  | Webhook topic, e.g. `coupon.updated`. [See the complete list](#topics)                                                                                                                                                  |
| `resource`     | string  | Webhook resource, e.g. `coupon` <i class="label label-info">read-only</i>                                                                                                                                               |
| `event`        | string  | Webhook event, e.g. `updated` <i class="label label-info">read-only</i>                                                                                                                                                 |
| `hooks`        | array   | WooCommerce action names associated with the webhook <i class="label label-info">read-only</i>                                                                                                                          |
| `delivery_url` | string  | The URL where the webhook payload is delivered                                                                                                                                                                          |
| `secret`       | string  | Secret key used to generate a hash of the delivered webhook and provided in the request headers. This will default to the current API user's consumer secret if not provided <i class="label label-info">write-only</i> |
| `created_at`   | string  | UTC DateTime when the webhook was created <i class="label label-info">read-only</i>                                                                                                                                     |
| `updated_at`   | string  | UTC DateTime when the webhook was last updated <i class="label label-info">read-only</i>                                                                                                                                |


### Delivery Properties ###

|     Attribute      |   Type  |                                                                                 Description                                                                                 |
| ------------------ | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`               | integer | The delivery ID (comment ID)                                                                                                                                                |
| `duration`         | string  | The delivery duration, in seconds                                                                                                                                           |
| `summary`          | string  | A friendly summary of the response including the HTTP response code, message, and body                                                                                      |
| `request_url`      | string  | The URL where the webhook was delivered                                                                                                                                     |
| `request_headers`  | array   | Array of request headers (see [Request Headers Attributes](#request-headers-properties))                                                                                    |
| `request_body`     | string  | The request body, this matches the API response for the given resource (e.g. for the coupon.updated topic, the request body would match the response for GET /coupons/{id}) |
| `response_code`    | string  | The HTTP response code from the receiving server                                                                                                                            |
| `response_message` | string  | The HTTP response message from the receiving server                                                                                                                         |
| `response_headers` | array   | Array of the response headers from the receiving server                                                                                                                     |
| `response_body`    | string  | The response body from the receiving server                                                                                                                                 |
| `created_at`       | string  | A DateTime of when the delivery was logged                                                                                                                                  |

#### Request Headers Properties ####

|         Attribute          |   Type  |                                        Description                                         |
| -------------------------- | ------- | ------------------------------------------------------------------------------------------ |
| `User-Agent`               | string  | The request user agent, defaults to "WooCommerce/{version} Hookshot (WordPress/{version})" |
| `Content-Type`             | string  | The request content-type, defaults to "application/json"                                   |
| `X-WC-Webhook-Topic`       | string  | The webhook topic                                                                          |
| `X-WC-Webhook-Resource`    | string  | The webhook resource                                                                       |
| `X-WC-Webhook-Event`       | string  | The webhook event                                                                          |
| `X-WC-Webhook-Signature`   | string  | A base64 encoded HMAC-SHA256 hash of the payload                                           |
| `X-WC-Webhook-ID`          | integer | The webhook's ID                                                                           |
| `X-WC-Webhook-Delivery-ID` | integer | The delivery ID                                                                            |

## Create A Webhook ##

This API helps you to create a new webhook.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/wc-api/v2/webhooks</h6>
	</div>
</div>

```shell
curl -X POST https://example.com/wc-api/v2/webhooks \
	-u consumer_key:consumer_secret \
	-H "Content-Type: application/json" \
	-d '{
  "webhook": {
    "name": "An add to cart webhook",
    "secret": "my-super-secret-private-key",
    "topic": "action.woocommerce_add_to_cart",
    "delivery_url": "http://requestb.in/1exdwip1"
  }
}'
```

> Response:

```json
{
  "webhook": {
    "id": 535,
    "name": "An add to cart webhook",
    "status": "active",
    "topic": "action.woocommerce_add_to_cart",
    "resource": "action",
    "event": "woocommerce_add_to_cart",
    "hooks": [
      "woocommerce_add_to_cart"
    ],
    "delivery_url": "http://requestb.in/1exdwip1",
    "created_at": "2015-01-21T13:19:58Z",
    "updated_at": "2015-01-21T13:19:58Z"
  }
}
```

## View A Webhook ##

This API lets you retrieve and view a specific webhook.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/webhooks/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/webhooks/535 \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "webhook": {
    "id": 535,
    "name": "An add to cart webhook",
    "status": "active",
    "topic": "action.woocommerce_add_to_cart",
    "resource": "action",
    "event": "woocommerce_add_to_cart",
    "hooks": [
      "woocommerce_add_to_cart"
    ],
    "delivery_url": "http://requestb.in/1exdwip1",
    "created_at": "2015-01-21T13:19:58Z",
    "updated_at": "2015-01-21T13:19:58Z"
  }
}
```

## View List Of Webhooks ##

This API helps you to view all the webhooks.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/webhooks</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/webhooks \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "webhooks": [
    {
      "id": 535,
      "name": "An add to cart webhook",
      "status": "active",
      "topic": "action.woocommerce_add_to_cart",
      "resource": "action",
      "event": "woocommerce_add_to_cart",
      "hooks": [
        "woocommerce_add_to_cart"
      ],
      "delivery_url": "http://requestb.in/1exdwip1",
      "created_at": "2015-01-21T13:19:58Z",
      "updated_at": "2015-01-21T13:19:58Z"
    },
    {
      "id": 313,
      "name": "Webhook created on Jan 17, 2015 @ 11:45 AM",
      "status": "active",
      "topic": "order.created",
      "resource": "order",
      "event": "created",
      "hooks": [
        "woocommerce_checkout_order_processed",
        "woocommerce_process_shop_order_meta",
        "woocommerce_api_create_order"
      ],
      "delivery_url": "http://requestb.in/1exdwip1",
      "created_at": "2014-12-17T11:45:05Z",
      "updated_at": "2015-01-10T00:41:08Z"
    }
  ]
}
```

## Update A Webhook ##

This API lets you make changes to a webhook.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-put">PUT</i>
		<h6>/wc-api/v2/webhook/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X PUT https://example.com/wc-api/v2/webhook/535 \
	-u consumer_key:consumer_secret \
	-H "Content-Type: application/json" \
	-d '{
  "webhook": {
    "status": "paused"
  }
}'
```

> Response:

```json
{
  "webhook": {
    "id": 535,
    "name": "An add to cart webhook",
    "status": "paused",
    "topic": "action.woocommerce_add_to_cart",
    "resource": "action",
    "event": "woocommerce_add_to_cart",
    "hooks": [
      "woocommerce_add_to_cart"
    ],
    "delivery_url": "http://requestb.in/1exdwip1",
    "created_at": "2015-01-21T13:19:58Z",
    "updated_at": "2015-01-21T13:19:58Z"
  }
}
```

## Delete A Webhook ##

This API helps you delete a webhook.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-delete">DELETE</i>
		<h6>/wc-api/v2/webhooks/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X DELETE https://example.com/wc-api/v2/webhooks/535 \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "message": "Permanently deleted webhook"
}
```

## View Webhooks Count ##

This API lets you retrieve a count of all webhooks.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/webhooks/count</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/webhooks/count \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "count": 4
}
```

### Parameters ###

| Parameter |  Type  |                            Description                             |
| --------- | ------ | ------------------------------------------------------------------ |
| `status`  | string | Get a total count of webhooks with the given status                |
| `filter`  | string | See [Parameters > Filter Parameter](#filter-parameter) documention |

## View A Webhooks Delivery ##

This API lets you retrieve and view a specific webhook delivery.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/webhooks/&lt;id&gt;/deliveries/&lt;delivery_id&gt;</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/webhooks/535/deliveries/378 \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "webhook_delivery": {
    "id": 378,
    "duration": "0.90226",
    "summary": "HTTP 200 OK: ok",
    "request_method": "POST",
    "request_url": "http://requestb.in/125q7ns1",
    "request_headers": {
      "User-Agent": "WooCommerce/2.3.0 Hookshot (WordPress/4.1)",
      "Content-Type": "application/json",
      "X-WC-Webhook-Topic": "action.woocommerce_add_to_cart",
      "X-WC-Webhook-Resource": "action",
      "X-WC-Webhook-Event": "woocommerce_add_to_cart",
      "X-WC-Webhook-Signature": "geC1akFhCtsO7fbXz5XiGUsMsRa4Mt0IJsZ96nTaHjI=",
      "X-WC-Webhook-ID": 535,
      "X-WC-Webhook-Delivery-ID": 378
    },
    "request_body": "{\"action\":\"woocommerce_add_to_cart\",\"arg\":\"7cbbc409ec990f19c78c75bd1e06f215\"}",
    "response_code": "200",
    "response_message": "OK",
    "response_headers": {
      "connection": "close",
      "server": "gunicorn/18.0",
      "date": "Wed, 21 Jan 2015 16:22:49 GMT",
      "content-type": "text/html; charset=utf-8",
      "content-length": "2",
      "sponsored-by": "https://www.runscope.com",
      "via": "1.1 vegur"
    },
    "response_body": "ok",
    "created_at": "2015-01-21T16:26:12Z"
  }
}
```

<aside class="notice">
View the [Delivery Properties](#delivery-properties) for more details on this response.
</aside>

## View List Of Webhooks Deliveries ##

This API helps you to view all deliveries from a specific webhooks.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/webhooks/&lt;id&gt;/deliveries</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/webhooks/535/deliveries \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "webhook_deliveries": [
    {
      "id": 380,
      "duration": "0.58635",
      "summary": "HTTP 200 OK: ok",
      "request_method": "POST",
      "request_url": "http://requestb.in/125q7ns1",
      "request_headers": {
        "User-Agent": "WooCommerce/2.3.0 Hookshot (WordPress/4.1)",
        "Content-Type": "application/json",
        "X-WC-Webhook-Topic": "action.woocommerce_add_to_cart",
        "X-WC-Webhook-Resource": "action",
        "X-WC-Webhook-Event": "woocommerce_add_to_cart",
        "X-WC-Webhook-Signature": "st4egVCTwG1JMfxmxe7MZYEuj9Y6Euge4SOTNfCUCWY=",
        "X-WC-Webhook-ID": 535,
        "X-WC-Webhook-Delivery-ID": 380
      },
      "request_body": "{\"action\":\"woocommerce_add_to_cart\",\"arg\":\"c16a5320fa475530d9583c34fd356ef5\"}",
      "response_code": "200",
      "response_message": "OK",
      "response_headers": {
        "connection": "close",
        "server": "gunicorn/18.0",
        "date": "Wed, 21 Jan 2015 16:23:05 GMT",
        "content-type": "text/html; charset=utf-8",
        "content-length": "2",
        "sponsored-by": "https://www.runscope.com",
        "via": "1.1 vegur"
      },
      "response_body": "ok",
      "created_at": "2015-01-21T16:26:28Z"
    },
    {
      "id": 378,
      "duration": "0.90226",
      "summary": "HTTP 200 OK: ok",
      "request_method": "POST",
      "request_url": "http://requestb.in/125q7ns1",
      "request_headers": {
        "User-Agent": "WooCommerce/2.3.0 Hookshot (WordPress/4.1)",
        "Content-Type": "application/json",
        "X-WC-Webhook-Topic": "action.woocommerce_add_to_cart",
        "X-WC-Webhook-Resource": "action",
        "X-WC-Webhook-Event": "woocommerce_add_to_cart",
        "X-WC-Webhook-Signature": "geC1akFhCtsO7fbXz5XiGUsMsRa4Mt0IJsZ96nTaHjI=",
        "X-WC-Webhook-ID": 535,
        "X-WC-Webhook-Delivery-ID": 378
      },
      "request_body": "{\"action\":\"woocommerce_add_to_cart\",\"arg\":\"7cbbc409ec990f19c78c75bd1e06f215\"}",
      "response_code": "200",
      "response_message": "OK",
      "response_headers": {
        "connection": "close",
        "server": "gunicorn/18.0",
        "date": "Wed, 21 Jan 2015 16:22:49 GMT",
        "content-type": "text/html; charset=utf-8",
        "content-length": "2",
        "sponsored-by": "https://www.runscope.com",
        "via": "1.1 vegur"
      },
      "response_body": "ok",
      "created_at": "2015-01-21T16:26:12Z"
    }
  ]
}
```
