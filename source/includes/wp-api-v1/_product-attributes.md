# Product - Attributes #

This section lists all API endpoints that can be used to create, edit or otherwise manipulate product attributes.

## Product Attribute Properties ##

|   Attribute    |   Type  |                                                Description                                                |
|----------------|---------|-----------------------------------------------------------------------------------------------------------|
| `id`           | integer | Unique identifier for the resource. <i class="label label-info">read-only</i>                             |
| `name`         | string  | Attribute name. <i class="label label-info">required</i>                                                  |
| `slug`         | string  | An alphanumeric identifier for the resource unique to its type.                                           |
| `type`         | string  | Type of attribute. Default is `select`. Options: `select` and `text` (some plugins can include new types) |
| `order_by`     | string  | Default sort order. Default is `menu_order`. Options: `menu_order`, `name`, `name_num` and `id`.          |
| `has_archives` | boolean | Enable/Disable attribute archives. Default is `false`.                                                    |

## Create a Product Attribute ##

This API helps you to create a new product attribute.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/wp-json/wc/v1/products/attributes</h6>
	</div>
</div>

```shell
curl -X POST https://example.com/wp-json/wc/v1/products/attributes \
    -u consumer_key:consumer_secret \
    -H "Content-Type: application/json" \
    -d '{
  "name": "Color",
  "slug": "pa_color",
  "type": "select",
  "order_by": "menu_order",
  "has_archives": true
}'
```

```javascript
var data = {
  name: 'Color',
  slug: 'pa_color',
  type: 'select',
  order_by: 'menu_order',
  has_archives: true
};

WooCommerce.post('products/attributes', data, function(err, data, res) {
  console.log(res);
});
```

```php
<?php
$data = [
    'name' => 'Color',
    'slug' => 'pa_color',
    'type' => 'select',
    'order_by' => 'menu_order',
    'has_archives' => true
];

print_r($woocommerce->post('products/attributes', $data));
?>
```

```python
data = {
    "name": "Color",
    "slug": "pa_color",
    "type": "select",
    "order_by": "menu_order",
    "has_archives": True
}

print(wcapi.post("products/attributes", data).json())
```

```ruby
data = {
  name: "Color",
  slug: "pa_color",
  type: "select",
  order_by: "menu_order",
  has_archives: true
}

woocommerce.post("products/attributes", data).parsed_response
```

> JSON response example:

```json
{
  "id": 1,
  "name": "Color",
  "slug": "pa_color",
  "type": "select",
  "order_by": "menu_order",
  "has_archives": true,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/6"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes"
      }
    ]
  }
}
```

## View a Product Attribute ##

This API lets you retrieve and view a specific product attribute by ID.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl https://example.com/wp-json/wc/v1/products/attributes/1 \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.get('products/attributes/1', function(err, data, res) {
  console.log(res);
});
```

```php
<?php print_r($woocommerce->get('products/attributes/1')); ?>
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
  "id": 1,
  "name": "Color",
  "slug": "pa_color",
  "type": "select",
  "order_by": "menu_order",
  "has_archives": true,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/6"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes"
      }
    ]
  }
}
```

## View List of Product Attributes ##

This API helps you to view all the product attributes.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wp-json/wc/v1/products/attributes</h6>
	</div>
</div>

```shell
curl https://example.com/wp-json/wc/v1/products/attributes \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.get('products/attributes', function(err, data, res) {
  console.log(res);
});
```

```php
<?php print_r($woocommerce->get('products/attributes')); ?>
```

```python
print(wcapi.get("products/attributes").json())
```

```ruby
woocommerce.get("products/attributes").parsed_response
```

> JSON response example:

```json
[
  {
    "id": 1,
    "name": "Color",
    "slug": "pa_color",
    "type": "select",
    "order_by": "menu_order",
    "has_archives": true,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/6"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes"
        }
      ]
    }
  },
  {
    "id": 2,
    "name": "Size",
    "slug": "pa_size",
    "type": "select",
    "order_by": "menu_order",
    "has_archives": false,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes"
        }
      ]
    }
  }
]
```

## Update a Product Attribute ##

This API lets you make changes to a product attribute.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-put">PUT</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X PUT https://example.com/wp-json/wc/v1/products/attributes/1 \
	-u consumer_key:consumer_secret \
	-H "Content-Type: application/json" \
	-d '{
  "order_by": "name"
}'
```

```javascript
var data = {
  order_by: 'name'
};

WooCommerce.put('products/attributes/1', data, function(err, data, res) {
  console.log(res);
});
```

```php
<?php
$data = [
    'order_by' => 'name'
];

print_r($woocommerce->put('products/attributes/1', $data));
?>
```

```python
data = {
    "order_by": "name"
}

print(wcapi.put("products/attributes/1", data).json())
```

```ruby
data = {
  order_by: "name"
}

woocommerce.put("products/attributes/1", data).parsed_response
```

> JSON response example:

```json
{
  "id": 1,
  "name": "Color",
  "slug": "pa_color",
  "type": "select",
  "order_by": "name",
  "has_archives": true,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/6"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes"
      }
    ]
  }
}
```

## Delete a Product Attribute ##

This API helps you delete a product attribute.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-delete">DELETE</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X DELETE https://example.com/wp-json/wc/v1/products/attributes/1?force=true \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.delete('products/attributes/1?force=true', function(err, data, res) {
  console.log(res);
});
```

```php
<?php print_r($woocommerce->delete('products/attributes/1', ['force' => true])); ?>
```

```python
print(wcapi.delete("products/attributes/1?force=true").json())
```

```ruby
woocommerce.delete("products/attributes/1", force: true).parsed_response
```

> JSON response example:

```json
{
  "id": 1,
  "name": "Color",
  "slug": "pa_color",
  "type": "select",
  "order_by": "menu_order",
  "has_archives": true,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/6"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes"
      }
    ]
  }
}
```

#### Available Parameters ####

| Parameter |  Type  |                          Description                          |
|-----------|--------|---------------------------------------------------------------|
| `force`   | string | Required to be `true`, as resource does not support trashing. |
