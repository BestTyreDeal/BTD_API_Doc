---
title: API Reference for BestTyreDeal.com

language_tabs:
  - shell: cURL

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Developers can reference this documentation to integrate their apps with our BestTyreDeal.com API. The API is still in beta.

# Authentication

Currently the API is not available for public access. Only specific organizations have been granted access.

# Products

## Get all products

```shell
 curl -i "http://api.besttyredeal.com/api/v1/products?apikey=apikey&pincode=122001&limit=2&cursor=30"
```

> The above command returns JSON structured like this:

```json
{
    "status": 200,
    "content": [
        {
            "product_id": "397",
            "product_name": "Tubeless",
            "product_size": "P 265/65R 17 112T TL",
            "product_image": "://besttyredeal.com/images/someimage.png",
            "product_mrp": "11000.0000",
            "product_currency": "INR",
            "product_description": "Fuel efficient. Superior tyre life.",
            "product_url": "http://besttyredeal.com/originalproductinfopage",
            "product_btd_offer": "",
            "product_discount": "6",
            "product_brand_offer": "",
            "suppliers": {
                "sup_id": "8",
                "sup_price": "11000",
                "sup_qty": "50",
                "sup_location": "Subhash Chowk",
                "sup_offers": " BEST EQUIPPED SHOP",
                "sup_tyre_exchange": "100",
                "sup_free_nitrogen": "Yes",
                "sup_free_alignment": "Yes",
                "sup_info_updatedat": "2015-09-17 08:46:23"
            }
        },
        {
            "product_id": "363",
            "product_name": "Tubeless",
            "product_size": "P 225/55R 16 95V TL",
            "product_image": "://besttyredeal.com/images/someimage.jpg",
            "product_mrp": "11000.0000",
            "product_currency": "INR",
            "product_description": "Fuel efficient. Superior tyre life.",
            "product_url": "http://besttyredeal.com/originalproductinfopage",
            "product_btd_offer": "",
            "product_discount": "6",
            "product_brand_offer": "",
            "suppliers": {
                "sup_id": "5",
                "sup_price": "11000",
                "sup_qty": "50",
                "sup_location": "Subhash Chowk",
                "sup_offers": " BEST EQUIPPED SHOP",
                "sup_tyre_exchange": "100",
                "sup_free_nitrogen": "Yes",
                "sup_free_alignment": "Yes",
                "sup_info_updatedat": "2015-09-17 08:46:23"
            }
        }
    ]
}
```

This endpoint retrieves all products. 

`Required paramters : pincode, apikey | Optional parameters : limit [Default = 30], cursor [Default = 0]`

### HTTP Request

`GET "http://api.besttyredeal.com/api/v1/products`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
api_key | - | The api key provided by BTD.
pincode | none | The pincode entered by user looking for sellers nearby.
limit (optional)   | 30   | Limit the number of results.
cursor (optional)  | 0    | Offset for results.

## Get single product information

```shell
 curl -i "http://api.besttyredeal.com/api/v1/product/lookup?apikey=apikey&productid=69&supplierid=1"
```

> The above command returns JSON structured like this:

```json
{
    "status": 200,
    "content": {
        "product": {
            "product_id": "69",
            "product_name": "S322 Tyre Tube",
            "product_size": "P 145/70R 12 69S TT",
            "product_image": "://besttyredeal.com/images/someimage.jpg",
            "product_mrp": "2907.0000",
            "product_currency": "INR",
            "product_description": "<p><strong>FUEL EFFICIENCY:</strong>Reduce rolling resistance.Improved fuel efficiency.</p>\r\n\r\n<p><strong>LOW NOISE:</strong>Designed to reduce noise.</p>\r\n\r\n<p><strong>BRAKING:</strong>Excellent braking capability.Increased safety.</p>",
            "product_url": "http://besttyredeal.com/originalproductinfopage",
            "product_btd_offer": "",
            "product_discount": "6",
            "product_brand_offer": ""
        },
        "supplier": {
            "sup_id": "1",
            "sup_price": "2430",
            "sup_qty": "50",
            "sup_location": "MG Road Sikanderpur",
            "sup_offers": " PICKUP & DELIVERY",
            "sup_tyre_exchange": "100",
            "sup_free_nitrogen": "Yes",
            "sup_free_alignment": "Yes",
            "sup_info_updatedat": "2015-09-17 08:46:23"
        },
        "manufacturer": {
            "manu_name": "Bridgestone",
            "manu_image": "://besttyredeal.com/images/someimage.jpg",
        }
    }
}
```

This endpoint retrieves information of single product. Lookup is done using **productid** & **supplierid** provided by BTD API via **products** endpoint.

`Required paramters : supplierid, productid, apikey`

### HTTP Request

`GET "http://api.besttyredeal.com/api/v1/product/lookup`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
api_key    | none | The api key provided by BTD.
productid  | none | The productid of user selected product. ("product_id")
supplierid | none | The supplierid of user selected product. ("sup_id")

#Orders

## Submit order details to BTD

```shell
 curl -i 
 --data "productid=9&paidamount=2000&supplierid=8&productqty=3&apikey=apikey" 
 "http://api.besttyredeal.com/api/v1/submitorder"
```

> The above command returns JSON structured like this:

```json
{
    "status": 200,
    "content": "Success"
}
```

This endpoint sends order details from third parties to BTD.

### HTTP Request

`POST http://api.besttyredeal.com/api/v1/submitorder`

### URL Parameters

Parameter | Description
--------- | -----------
apikey | The api key provided by BTD.
productid | The ID of the product user orders
supplierid | The ID of supplier who offers the product
productqty | The quantity of product ordered
paidamount | The final amount paid by customer
orderid | The order ID generated by third party