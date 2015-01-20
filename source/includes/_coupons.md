# Coupons #

This section lists all API that can be used to create, edit or otherwise manipulate coupons.

## Coupon Properties ##

|           Attribute            |   Type  |                                                        Description                                                         |
| ------------------------------ | ------- | -------------------------------------------------------------------------------------------------------------------------- |
| `id`                           | integer | Coupon ID (post ID) <i class="label label-info">read-only</i>                                                              |
| `code`                         | string  | Coupon code, always lowercase <i class="label label-info">mandatory</i>                                                    |
| `type`                         | string  | Coupon type, valid core types are: `fixed_cart`, `percent`, `fixed_product` and `percent_product`. Default is `fixed_cart` |
| `created_at`                   | string  | UTC DateTime when the coupon was created <i class="label label-info">read-only</i>                                         |
| `updated_at`                   | string  | UTC DateTime when the coupon was last updated <i class="label label-info">read-only</i>                                    |
| `amount`                       | float   | The amount of discount                                                                                                     |
| `individual_use`               | boolean | Whether coupon can only be used individually                                                                               |
| `product_ids`                  | array   | Array of product ID's the coupon can be used on                                                                            |
| `exclude_product_ids`          | array   | Array of product ID's the coupon cannot be used on                                                                         |
| `usage_limit`                  | integer | How many times the coupon can be used                                                                                      |
| `usage_limit_per_user`         | integer | How many times the coupon can be user per customer                                                                         |
| `limit_usage_to_x_items`       | integer | Max number of items in the cart the coupon can be applied to                                                               |
| `usage_count`                  | integer | Number of times the coupon has been used already <i class="label label-info">read-only</i>                                 |
| `expiry_date`                  | string  | UTC DateTime`when the coupon expires                                                                                       |
| `enable_free_shipping`         | boolean | Is the coupon for free shipping                                                                                            |
| `product_category_ids`         | array   | Array of category ID's the coupon applies to                                                                               |
| `exclude_product_category_ids` | array   | Array of category ID's the coupon does not apply to                                                                        |
| `exclude_sale_items`           | boolean | Exclude sale items from the coupon                                                                                         |
| `minimum_amount`               | float   | Minimum order amount that needs to be in the cart before coupon applies                                                    |
| `maximum_amount`               | float   | Maximum order amount allowed when using the coupon                                                                         |
| `customer_emails`              | array   | Array of email addresses that can use this coupon                                                                          |
| `description`                  | string  | Coupon description                                                                                                         |

## Create A Coupon ##

This API helps you to create a new coupon.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/wc-api/v2/coupons</h6>
	</div>
</div>

```shell
curl -X POST https://example.com/wc-api/v2/coupons \
	-u consumer_key:consumer_secret \
	-H "Content-Type: application/json" \
	-d '{
  "coupon": {
    "code": "new-coupon",
    "type": "percent",
    "amount": "10",
    "individual_use": true,
    "product_ids": [],
    "exclude_product_ids": [],
    "usage_limit": "",
    "usage_limit_per_user": "",
    "limit_usage_to_x_items": "",
    "expiry_date": "",
    "enable_free_shipping": false,
    "product_category_ids": [],
    "exclude_product_category_ids": [],
    "exclude_sale_items": true,
    "minimum_amount": "100.00",
    "maximum_amount": "0.00",
    "customer_emails": [],
    "description": ""
  }
}'
```

> Response:

```json
{
  "coupon": {
    "id": 529,
    "code": "new-coupon",
    "type": "percent",
    "created_at": "2015-01-20T19:05:27Z",
    "updated_at": "2015-01-20T19:05:27Z",
    "amount": "10.00",
    "individual_use": true,
    "product_ids": [],
    "exclude_product_ids": [],
    "usage_limit": null,
    "usage_limit_per_user": null,
    "limit_usage_to_x_items": 0,
    "usage_count": 0,
    "expiry_date": null,
    "enable_free_shipping": false,
    "product_category_ids": [],
    "exclude_product_category_ids": [],
    "exclude_sale_items": true,
    "minimum_amount": "100.00",
    "maximum_amount": "0.00",
    "customer_emails": [],
    "description": ""
  }
}
```

## View A Coupon ##

This API lets you retrieve and view a specific coupon.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/coupons/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/coupons/529 \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "coupon": {
    "id": 529,
    "code": "new-coupon",
    "type": "percent",
    "created_at": "2015-01-20T19:05:27Z",
    "updated_at": "2015-01-20T19:05:27Z",
    "amount": "10.00",
    "individual_use": true,
    "product_ids": [],
    "exclude_product_ids": [],
    "usage_limit": null,
    "usage_limit_per_user": null,
    "limit_usage_to_x_items": 0,
    "usage_count": 0,
    "expiry_date": null,
    "enable_free_shipping": false,
    "product_category_ids": [],
    "exclude_product_category_ids": [],
    "exclude_sale_items": true,
    "minimum_amount": "100.00",
    "maximum_amount": "0.00",
    "customer_emails": [],
    "description": ""
  }
}
```

## View List Of Coupons ##

This API helps you to view all the coupons.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/coupons</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/coupons \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "coupons": [
    {
      "id": 529,
      "code": "new-coupon",
      "type": "percent",
      "created_at": "2015-01-20T19:05:27Z",
      "updated_at": "2015-01-20T19:05:27Z",
      "amount": "10.00",
      "individual_use": true,
      "product_ids": [],
      "exclude_product_ids": [],
      "usage_limit": null,
      "usage_limit_per_user": null,
      "limit_usage_to_x_items": 0,
      "usage_count": 0,
      "expiry_date": null,
      "enable_free_shipping": false,
      "product_category_ids": [],
      "exclude_product_category_ids": [],
      "exclude_sale_items": true,
      "minimum_amount": "100.00",
      "maximum_amount": "0.00",
      "customer_emails": [],
      "description": ""
    },
    {
      "id": 527,
      "code": "free-shipping",
      "type": "fixed_cart",
      "created_at": "2015-01-20T18:35:59Z",
      "updated_at": "2015-01-20T18:35:59Z",
      "amount": "0.00",
      "individual_use": true,
      "product_ids": [],
      "exclude_product_ids": [],
      "usage_limit": null,
      "usage_limit_per_user": null,
      "limit_usage_to_x_items": 0,
      "usage_count": 0,
      "expiry_date": null,
      "enable_free_shipping": true,
      "product_category_ids": [],
      "exclude_product_category_ids": [],
      "exclude_sale_items": true,
      "minimum_amount": "50.00",
      "maximum_amount": "0.00",
      "customer_emails": [],
      "description": ""
    },
    {
      "id": 526,
      "code": "christmas-promo",
      "type": "percent",
      "created_at": "2015-01-20T18:10:58Z",
      "updated_at": "2015-01-20T18:10:58Z",
      "amount": "10.00",
      "individual_use": true,
      "product_ids": [],
      "exclude_product_ids": [],
      "usage_limit": null,
      "usage_limit_per_user": 1,
      "limit_usage_to_x_items": 0,
      "usage_count": 0,
      "expiry_date": "2014-12-25T00:00:00Z",
      "enable_free_shipping": false,
      "product_category_ids": [],
      "exclude_product_category_ids": [],
      "exclude_sale_items": true,
      "minimum_amount": "200.00",
      "maximum_amount": "0.00",
      "customer_emails": [],
      "description": "Discount for Christmas for orders over $ 200"
    }
  ]
}
```

## Update A Coupon ##

This API lets you make changes to a coupon.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-put">PUT</i>
		<h6>/wc-api/v2/coupons/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X PUT https://example.com/wc-api/v2/coupons/529 \
	-u consumer_key:consumer_secret \
	-H "Content-Type: application/json" \
	-d '{
  "coupon": {
    "amount": "5"
  }
}'
```

> Response:

```json
{
  "coupon": {
    "id": 529,
    "code": "new-coupon",
    "type": "percent",
    "created_at": "2015-01-20T19:05:27Z",
    "updated_at": "2015-01-20T19:05:27Z",
    "amount": "5.00",
    "individual_use": true,
    "product_ids": [],
    "exclude_product_ids": [],
    "usage_limit": null,
    "usage_limit_per_user": null,
    "limit_usage_to_x_items": 0,
    "usage_count": 0,
    "expiry_date": null,
    "enable_free_shipping": false,
    "product_category_ids": [],
    "exclude_product_category_ids": [],
    "exclude_sale_items": true,
    "minimum_amount": "100.00",
    "maximum_amount": "0.00",
    "customer_emails": [],
    "description": ""
  }
}
```

## Delete A Coupon ##

This API helps you delete a ticket.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-delete">DELETE</i>
		<h6>/wc-api/v2/coupons/&lt;id&gt;</h6>
	</div>
</div>

```shell
curl -X DELETE https://example.com/wc-api/v2/coupons/529/?force=true \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "message": "Permanently deleted coupon"
}
```

### Parameters ###

| Parameter |  Type  |                                                                          Description                                                                           |
| --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `force`   | string | Use `true` whether to permanently delete the coupon, defaults to `false`. Note that permanently deleting the coupon will return HTTP 200 rather than HTTP 202. |

## View A Coupon By Code ##

This API lets you use a coupon code to retrieve and view a specific coupon.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/coupons/code/&lt;code&gt;</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/coupons/code/new-coupon \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "coupon": {
    "id": 529,
    "code": "new-coupon",
    "type": "percent",
    "created_at": "2015-01-20T19:05:27Z",
    "updated_at": "2015-01-20T19:05:27Z",
    "amount": "10.00",
    "individual_use": true,
    "product_ids": [],
    "exclude_product_ids": [],
    "usage_limit": null,
    "usage_limit_per_user": null,
    "limit_usage_to_x_items": 0,
    "usage_count": 0,
    "expiry_date": null,
    "enable_free_shipping": false,
    "product_category_ids": [],
    "exclude_product_category_ids": [],
    "exclude_sale_items": true,
    "minimum_amount": "100.00",
    "maximum_amount": "0.00",
    "customer_emails": [],
    "description": ""
  }
}
```

## View Coupon Count ##

This API lets you retrieve a count of all coupons.

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wc-api/v2/coupons/count</h6>
	</div>
</div>

```shell
curl https://example.com/wc-api/v2/coupons/count \
	-u consumer_key:consumer_secret
```

> Response:

```json
{
  "count": 3
}
```
