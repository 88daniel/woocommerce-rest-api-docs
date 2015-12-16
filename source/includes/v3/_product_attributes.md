# Product - Attributes #

This section lists all API that can be used to create, edit or otherwise manipulate product attributes.

## Product Attribute Properties ##

|   Attribute    |   Type  |                                                     Description                                                      |
| -------------- | ------- | -------------------------------------------------------------------------------------------------------------------- |
| `id`           | integer | Attribute ID <i class="label label-info">read-only</i>                                                               |
| `name`         | string  | Attribute name                                                                                                       |
| `slug`         | string  | Attribute slug                                                                                                       |
| `type`         | string  | Attribute type, the types available include by default are: `select` and `text` (some plugins can include new types) |
| `order_by`     | string  | Default sort order. Available: `menu_order`, `name`, `name_num` and `id`                                             |
| `has_archives` | boolean | Enable/Disable attribute archives                                                                                    |

## Create A Product Attribute ##

This API helps you to create a new product attribute.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/wc-api/v3/products/attributes</h6>
	</div>
</div>

```shell
curl -X POST https://example.com/wc-api/v3/products/attributes \
    -u consumer_key:consumer_secret \
    -H "Content-Type: application/json" \
    -d '{
  "product_attribute": {
    "name": "Color",
    "slug": "pa_color",
    "type": "select",
    "order_by": "menu_order",
    "has_archives": true
  }
}'
```

```javascript
var data = {
  product_attribute: {
    name: "Color",
    slug: "pa_color",
    type: "select",
    order_by: "menu_order",
    has_archives: true
  }
};

WooCommerce.post('products/attributes', data, function(err, data, res) {
  console.log(res);
});
```

```python
data = {
    "product_attribute": {
        "name": "Color",
        "slug": "pa_color",
        "type": "select",
        "order_by": "menu_order",
        "has_archives": True
    }
}

print(wcapi.post("products/attributes", data).json())
```

```ruby
data = {
  product_attribute: {
    name: "Color",
    slug: "pa_color",
    type: "select",
    order_by: "menu_order",
    has_archives: true
  }
}

woocommerce.post("products/attributes", data).parsed_response
```

> JSON response example:

```json
{
  "product_attribute": {
    "id": 1,
    "name": "Color",
    "slug": "pa_color",
    "type": "select",
    "order_by": "menu_order",
    "has_archives": true
  }
}
```

## View A Product Attribute ##

This API lets you retrieve and view a specific product attribute by ID.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v3/products/attributes/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v3/products/attributes/1 \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.get('products/attributes/1', function(err, data, res) {
  console.log(res);
});
```

```python
print(wcapi.get("products/attributes/1").json())
```

```ruby
woocommerce.get("products/attributes/1").parsed_response
```

> JSON response example:

```json
{
  "product_attribute": {
    "id": 1,
    "name": "Color",
    "slug": "pa_color",
    "type": "select",
    "order_by": "menu_order",
    "has_archives": true
  }
}
```

<aside class="notice">
	View the <a href="#product-attribute-properties">Product Attribute Properties</a> for more details on this response.
</aside>

## View List Of Product Attributes ##

This API helps you to view all the product attributes.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v3/products/attributes</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v3/products/attributes \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.get('products/attributes', function(err, data, res) {
  console.log(res);
});
```

```python
print(wcapi.get("products/attributes").json())
```

```ruby
woocommerce.get("products/attributes").parsed_response
```

> JSON response example:

```json
{
  "product_attributes": [
    {
      "id": 1,
      "name": "Color",
      "slug": "pa_color",
      "type": "select",
      "order_by": "menu_order",
      "has_archives": true
    },
    {
      "id": 2,
      "name": "Size",
      "slug": "pa_size",
      "type": "select",
      "order_by": "menu_order",
      "has_archives": false
    }
  ]
}
```

<aside class="notice">
	View the <a href="#product-attribute-properties">Product Attribute Properties</a> for more details on this response.
</aside>

## Update A Product Attribute ##

This API lets you make changes to a product attribute.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-put">PUT</i>
		<h6>/wc-api/v3/products/attributes/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X PUT https://example.com/wc-api/v3/products/attributes/1 \
	-u consumer_key:consumer_secret \
	-H "Content-Type: application/json" \
	-d '{
  "product_attribute": {
    "order_by": "name"
  }
}'
```

```javascript
var data = {
  product_attribute: {
    order_by: 'name'
  }
};

WooCommerce.put('products/attributes/1', data, function(err, data, res) {
  console.log(res);
});
```

```python
data = {
    "product_attribute": {
        "order_by": "name"
    }
}

print(wcapi.put("products/attributes/1", data).json())
```

```ruby
data = {
  product_attribute: {
    order_by: "name"
  }
}

woocommerce.put("products/attributes/1", data).parsed_response
```

> JSON response example:

```json
{
  "product_attribute": {
    "id": 1,
    "name": "Color",
    "slug": "pa_color",
    "type": "select",
    "order_by": "name",
    "has_archives": true
  }
}
```

<aside class="notice">
	View the <a href="#product-attribute-properties">Product Attribute Properties</a> for more details on this response.
</aside>

## Delete A Product Attribute ##

This API helps you delete a product attribute.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-delete">DELETE</i>
		<h6>/wc-api/v3/products/attributes/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X DELETE https://example.com/wc-api/v3/products/attributes/1 \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.delete('products/attributes/1', function(err, data, res) {
  console.log(res);
});
```

```python
print(wcapi.delete("products/attributes/1").json())
```

```ruby
woocommerce.delete("products/attributes/1").parsed_response
```

> JSON response example:

```json
{
  "message": "Deleted product_attribute"
}
```
