# Product - Attribute Terms #

This section lists all API endpoints that can be used to create, edit or otherwise manipulate product attribute terms.

## Product Attribute Properties ##

|  Attribute   |   Type  |                                       Description                                        |
|--------------|---------|------------------------------------------------------------------------------------------|
| `id`         | integer | Unique identifier for the resource. <i class="label label-info">read-only</i>            |
| `name`       | string  | Term name. <i class="label label-info">required</i>                                      |
| `slug`       | string  | An alphanumeric identifier for the resource unique to its type.                          |
| `menu_order` | integer | Menu order, used to custom sort the resource.                                            |
| `count`      | integer | Number of published products for the resource. <i class="label label-info">read-only</i> |

## Create a Product Attribute Term ##

This API helps you to create a new product attribute term.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;attribute_id&gt;/terms</h6>
	</div>
</div>

```shell
curl -X POST https://example.com/wp-json/wc/v1/products/attributes/2/terms \
    -u consumer_key:consumer_secret \
    -H "Content-Type: application/json" \
    -d '{
  "name": "XXS"
}'
```

```javascript
var data = {
  name: 'XXS'
};

WooCommerce.post('products/attributes/2/terms', data, function(err, data, res) {
  console.log(res);
});
```

```php
<?php
$data = [
    'name' => 'XXS'
];

print_r($woocommerce->post('products/attributes/2/terms', $data));
?>
```

```python
data = {
    "name": "XXS"
}

print(wcapi.post("products/attributes/2/terms", data).json())
```

```ruby
data = {
  name: "XXS"
}

woocommerce.post("products/attributes/2/terms", data).parsed_response
```

> JSON response example:

```json
{
  "id": 23,
  "name": "XXS",
  "slug": "xxs",
  "menu_order": 1,
  "count": 1,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/23"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
      }
    ]
  }
}
```

## View a Product Attribute Term ##

This API lets you retrieve a product attribute term by ID.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;attribute_id&gt;/terms/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl https://example.com/wp-json/wc/v1/products/attributes/2/terms/23 \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.get('products/attributes/2/terms/23', function(err, data, res) {
  console.log(res);
});
```

```php
<?php print_r($woocommerce->get('products/attributes/2/terms/23')); ?>
```

```python
print(wcapi.get("products/attributes/2/terms/23").json())
```

```ruby
woocommerce.get("products/attributes/2/terms/23").parsed_response
```

> JSON response example:

```json
{
  "id": 23,
  "name": "XXS",
  "slug": "xxs",
  "menu_order": 1,
  "count": 1,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/23"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
      }
    ]
  }
}
```

## View List of Product Attribute Terms ##

This API lets you retrieve all terms from a product attribute.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;attribute_id&gt;/terms</h6>
	</div>
</div>

```shell
curl https://example.com/wp-json/wc/v1/products/attributes/2/terms \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.get('products/attributes/2/terms', function(err, data, res) {
  console.log(res);
});
```

```php
<?php print_r($woocommerce->get('products/attributes/2/terms')); ?>
```

```python
print(wcapi.get("products/attributes/2/terms").json())
```

```ruby
woocommerce.get("products/attributes/2/terms").parsed_response
```

> JSON response example:

```json
[
  {
    "id": 23,
    "name": "XXS",
    "slug": "xxs",
    "menu_order": 1,
    "count": 1,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/23"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
        }
      ]
    }
  },
  {
    "id": 22,
    "name": "XS",
    "slug": "xs",
    "menu_order": 2,
    "count": 1,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/22"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
        }
      ]
    }
  },
  {
    "id": 17,
    "name": "S",
    "slug": "s",
    "menu_order": 3,
    "count": 1,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/17"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
        }
      ]
    }
  },
  {
    "id": 18,
    "name": "M",
    "slug": "m",
    "menu_order": 4,
    "count": 1,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/18"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
        }
      ]
    }
  },
  {
    "id": 19,
    "name": "L",
    "slug": "l",
    "menu_order": 5,
    "count": 1,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/19"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
        }
      ]
    }
  },
  {
    "id": 20,
    "name": "XL",
    "slug": "xl",
    "menu_order": 6,
    "count": 1,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/20"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
        }
      ]
    }
  },
  {
    "id": 21,
    "name": "XXL",
    "slug": "xxl",
    "menu_order": 7,
    "count": 1,
    "_links": {
      "self": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/21"
        }
      ],
      "collection": [
        {
          "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
        }
      ]
    }
  }
]
```

#### Available Parameters ####

|  Parameter   |   Type  |                                                                Description                                                                 |
|--------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `context`    | string  | Scope under which the request is made; determines fields present in response. Options: `view` and `edit`.                                  |
| `page`       | integer | Current page of the collection.                                                                                                            |
| `per_page`   | integer | Maximum number of items to be returned in result set.                                                                                      |
| `search`     | string  | Limit results to those matching a string.                                                                                                  |
| `exclude`    | string  | Ensure result set excludes specific ids.                                                                                                   |
| `include`    | string  | Limit result set to specific ids.                                                                                                          |
| `order`      | string  | Order sort attribute ascending or descending. Default is `asc`. Options: `asc` and `desc`.                                                 |
| `orderby`    | string  | Sort collection by object attribute. Default is `name`. Options: `id`, `include`, `name`, `slug`, `term_group`, `description` and `count`. |
| `hide_empty` | bool    | Whether to hide resources not assigned to any products. Default is `false`.                                                                |
| `parent`     | integer | Limit result set to resources assigned to a specific parent.                                                                               |
| `product`    | integer | Limit result set to resources assigned to a specific product.                                                                              |
| `slug`       | string  | Limit result set to resources with a specific slug.                                                                                        |

## Update a Product Attribute Term ##

This API lets you make changes to a product attribute term.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-put">PUT</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;attribute_id&gt;/terms/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X PUT https://example.com/wp-json/wc/v1/products/attributes/2/terms/23 \
	-u consumer_key:consumer_secret \
	-H "Content-Type: application/json" \
	-d '{
  "name": "XXS"
}'
```

```javascript
var data = {
  name: 'XXS'
};

WooCommerce.put('products/attributes/2/terms/23', data, function(err, data, res) {
  console.log(res);
});
```

```php
<?php
$data = [
    'name' => 'XXS'
];

print_r($woocommerce->put('products/attributes/2/terms/23', $data));
?>
```

```python
data = {
    "name": "XXS"
}

print(wcapi.put("products/attributes/2/terms/23", data).json())
```

```ruby
data = {
  name: "XXS"
}

woocommerce.put("products/attributes/2/terms/23", data).parsed_response
```

> JSON response example:

```json
{
  "id": 23,
  "name": "XXS",
  "slug": "xxs",
  "menu_order": 1,
  "count": 1,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/23"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
      }
    ]
  }
}
```

## Delete a Product Attribute Term ##

This API helps you delete a product attribute term.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-delete">DELETE</i>
		<h6>/wp-json/wc/v1/products/attributes/&lt;attribute_id&gt;/terms/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X DELETE https://example.com/wp-json/wc/v1/products/attributes/2/terms/23?force=true \
	-u consumer_key:consumer_secret
```

```javascript
WooCommerce.delete('products/attributes/2/terms/23?force=true', function(err, data, res) {
  console.log(res);
});
```

```php
<?php print_r($woocommerce->delete('products/attributes/2/terms/23', ['force' => true])); ?>
```

```python
print(wcapi.delete("products/attributes/2/terms/23?force=true").json())
```

```ruby
woocommerce.delete("products/attributes/2/terms/23", force: true).parsed_response
```

> JSON response example:

```json
{
  "id": 23,
  "name": "XXS",
  "slug": "xxs",
  "menu_order": 1,
  "count": 1,
  "_links": {
    "self": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms/23"
      }
    ],
    "collection": [
      {
        "href": "https://example.com/wp-json/wc/v1/products/attributes/2/terms"
      }
    ]
  }
}
```

#### Available Parameters ####

| Parameter |  Type  |                          Description                          |
|-----------|--------|---------------------------------------------------------------|
| `force`   | string | Required to be `true`, as resource does not support trashing. |
