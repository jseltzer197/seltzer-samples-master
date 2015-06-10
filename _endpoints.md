<!--
eBay Enterprise Webstore API Documentation
Author: Jeff Seltzer
email: jseltzer@wardenclyffe.com
phone: 610.356.0905
-->

# Categories
The Categories API is used to retrieve categories for the client application. The request can specify returned categories by store_id to return a list of top-level and sub-level category navigation paths.  Responses, or Payloads, are returned in JSON format.



## Get Top Level Category

This request returns a list of top-level navigation categories.

> Sample response payload:

```JSON
{
  "subcategories":  [
     {
      "displayName": "Category 1",
      "id": 3036498,
      "images":  [],
      "productCount": 189,
      "seoAttributes":  {
        "description": "Buy Category 1 products at ",
        "keywords": "Category 1 , ",
        "title": "Category 1 - - "
      },
      "subcategoriesCount": 5,
      "uri": "categories/3036498",
      "displaySequence": 1
    },
    .
    .
    .
```

### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/categories`

### Request Details


Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Code | 403 Forbidden - invalid version or store code
Success HTTP Code | 200 OK
Error Payload | None
Request Payload | None
Response Payload | See [Response Payload](payloads/index.htm#<id=37>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes | None
Optional Query Parameters | depth=&#60;N&#62; : the number of levels to be returned.  For example, `/v<M.m>/stores/<store_id>/categories?depth=3` will return subcategories 3 levels deep, for the navigation GUI, top-level category plus 2 sub-level categories. 
Additional Information | None









## Get Specific Category

This request returns details on a specific category. The resource uses the categoryId to search the specific category within the store, and return the details on the category.

> Sample response payload:

```JSON
{
  "subcategories":  [
     {
      "ancestors":  [
         {
          "displayName": "Category 1",
          "rank": 1,
          "uri": "categories/3036498"
        }
      ],
      "displayName": "SubCategory 1.1",
      "id": 3036509,
      "images":  [
         {
          "name": "p4649411dt.jpg",
          "effectiveUrl": "http://ess-uat02.uat.gsipartners.com/graphics/product_images/p4649411dt.jpg",
          "imageActualHeight": 500,
          "imageActualWidth": 500,
          "typeID": "ENH",
          "viewID": "main"
        },
        .
        .
        .
```





### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/categories/<categoryId>`

<aside class="notice">
Using the Specific Category URI, only 1 category can be requested at a time.
</aside>

### Request Details


Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
Success HTTP Code | 200 OK
Error Payload | None
Request Payload | None
Response Payload | See [Response Payload](payloads/index.htm#<id=34>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes | None
Optional Query Parameters | **depth=&#60;N&#62;** : the number of levels to be returned.  For example, `/v<M.m>/stores/<store_id>/categories?depth=3` will return subcategories 3 levels deep, for the navigation GUI, the specified category plus 2 sub-level categories.
Additional Information | None









# Products
The Products API is used to retrieve products for the client application.


## Get List of Products within a Category

This request returns a list of products within a category.

> Sample response payload:

```JSON
{
  "offset": 0,
  "pageCount": 19,
  "pageIndex": 0,
  "pageSize": 10,
  "products":  [
     {
      "availability": true,
      "averageRating": 0,
      "customizable": false,
      "displayName": "T-Shirt White Large Alpha - long title",
      "inStock": false,
      "isCartable": false,
      "isShipToStoreEligible": null,
      "isStorePickupEligible": false,
      "itemId": 3073498,
      "itemType": "barebones",
      "listPrice": 44.23,
      "reviews": 0,
      "salePrice": 44.23,
      "shortDesc": "T-Shirt White Large Alpha - short desc",
      "thumbnailUri": "http://ess-uat02.uat.gsipartners.com/graphics/product_images/p4649411th.jpg",
      "uri": "products/3073498",
      "wasPrice": null
    },
    .
    .
    .
```


### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/categories/<cat_ID>/products`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|403 Forbidden - invalid version or store code 
 | 404 Not Found - when requested resource is not found
Success HTTP Code|200 OK
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=30>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Optional Query Parameters|pageSize=&#60;number of products per response&#62; (maximum value = 100)
 | pageNumber=&#60;page number&#62;
 | q=&#60;search term&#62;
 | associations=&#60;promotions, facets, variations, attributes&#62;
 | associations = promotions - displays the promotion list for the product
 | associations = facets - displays the sort and filter attributes
 | associations = variations - displays variation details for the product
 | associations = attributes - displays product attribute data in the response
 | Comma separated query parameters can be provided that display various attributes for the product (for example, associations=promotions, facets, variations, attributes).
Additional Information|None






## Get List of Products
This request uses the products?q=&#60;keyword&#62; to search for products within the store.
<aside class="notice">
The application will return search results in the same order provided by the search engine used by the Webstore. 

The same query run repeatedly will return the same search results. 
</aside>
> Sample response payload:

```JSON
{
  "offset": 0,
  "pageCount": 10,
  "pageIndex": 0,
  "pageSize": 10,
  "products":  [
     {
      "availability": false,
      "averageRating": 0,
      "customizable": false,
      "displayName": "Widget Charlie - long title",
      "inStock": false,
      "isCartable": false,
      "isShipToStoreEligible": null,
      "isStorePickupEligible": false,
      "itemId": 12544401,
      "itemType": "essSimple",
      "listPrice": 99.99,
      "reviews": 0,
      "salePrice": 99.99,
      "shortDesc": "Widget Charlie - short desc",
      "thumbnailUri": "http://ess-uat02.uat.gsipartners.com/graphics/product_images/pTRU1-5385755th.jpg",
      "uri": "products/12544401",
      "wasPrice": null
    },
    .
    .
    .
```

### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/products?q=<keyword>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|400 Bad Request - no query parameters supplied
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found 
Success HTTP Code|200 OK 
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=29>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|q=&#60;keyword&#62;
Optional Query Parameters|pageSize=&#60;number of products per response&#62; (maximum value = 100)
 | pageNumber=&#60;page number&#62; 
 | q=&#60;search term&#62;
 | associations=&#60;promotions, facets, variations, attributes&#62;
 | associations = promotions - displays the promotion list for the product
 | associations = facets - displays the sort and filter attributes
 | associations = variations - displays variation details for the product
 | associations = attributes - displays product attribute data in the response
 | Comma separated query parameters can be provided that display various attributes for the product (for example, associations=promotions, facets, variations, attributes).
Additional Information|None




## Get Product Detail by Item ID
This request returns product details on a specific product by item id.  The resource uses &#60;itemid&#62; to search for the specific product within the store.
> Sample response payload:

```JSON
{
  "ancestors":  [
     {
      "displayName": "ESS Collections",
      "rank": 1,
      "uri": "categories/3562866"
    },
     {
      "displayName": "ESS Global Category 3",
      "rank": 2,
      "uri": "categories/3036542"
    }
  ],
  "attributes":  {
    "Bullet Point 1": "Bullet 1",
    "Bullet Point 2": "Bullet 2",
    "Bullet Point 3": "Bullet 3",
    "Bullet Point 4": "Bullet 4",
    "Bullet Point 5": "Bullet 5",
    "Bullet Point 6": "Bullet 6",
    "Country of Origin": "United States",
    "Express Store Color Code": "008",
    "Fabric Content": "100% Cotton",
    "Search 1": "GSI",
    "Search 2": "Express",
    "Search 3": "Store",
    "Fulfillment Option": "STH"
  },
  .
  .
  .

```


### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/products/<itemId>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found 
Success HTTP Code|200 OK
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=31>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Optional Query Parameters| associations=&#60;promotions, facets, variations, attributes&#62;
 | associations = promotions - displays the promotion list for the product
 | associations = facets - displays the sort and filter attributes
 | associations = variations - displays variation details for the product
 | associations = attributes - displays product attribute data in the response
 | Comma separated query parameters can be provided that display various attributes for the product (for example, associations=promotions, facets, variations, attributes).
 | imageType=&#60;type1,type2,type3..&#62;
Additional Information|None





## Get List of Cross-Sells Associated with Product
This request returns the list of cross sell products associated with a specific product by &#60;itemId&#62;. The resource uses itemId and cross-sells to search for the specific cross sell products within the store.

> Sample response payload:

```JSON
{
  "ancestors":  [],
  "offset": 0,
  "pageCount": 10,
  "pageNumber": 1,
  "pageSize": 10,
  "products":  [
     {
      "availability": true,
      "averageRating": 0,
      "customizable": false,
      "displayName": "Product Title",
      "inStock": false,
      "isCartable": false,
      "isShipToStoreEligible": null,
      "isStorePickupEligible": false,
      "itemId": 3039766,
      "itemType": "barebones",
      "listPrice": 57.11,
      "reviews": 0,
      "salePrice": 57.11,
      "shortDesc": "This is the short description",
      "thumbnailUri": "http://ess-uat02.uat.gsipartners.com/graphics/product_images/p4552115th.jpg",
      "uri": "products/3039766",
      "wasPrice": null
    },
    .
    .
    .
```



### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/products/<itemId>/crosssells`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found 
Success HTTP Code|200 OK
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=28>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Optional Query Parameters|pageSize=&#60;number of products per response&#62; (maximum value = 100)
 | pageNumber=&#60;page number&#62;
 | associations=&#60;promotions, facets, variations, attributes&#62;
 | associations = promotions - displays the promotion list for the product
 | associations = facets - displays the sort and filter attributes
 | associations = variations - displays variation details for the product
 | associations = attributes - displays product attribute data in the response
 | Comma separated query parameters can be provided that display various attributes for the product (for example, associations=promotions, facets, variations, attributes).
Additional Information|None





## Get Variation (SKU) Detail
This request returns details of a specific variation (SKU).  The resource will use &#60;product_id&#62;-&#60;sku_id&#62; to search for the specific variation (SKU) within the store.

> Sample response payload:

```JSON
{
  "attributes":  {
    "ESSCOLORCODE": "008",
    "ShipWtAir": "1",
    "ShipWtGround": "1",
    "SkuLargePkg": "0",
    "_color_code": "1058515",
    "_color_description": "YELLOW",
    "_size_code": "139340",
    "_size_description": "M"
  },
  "availability": true,
  "availabilityStatus": "IN_STOCK",
  "customizable": false,
  "dimensions":  {
    "length": 1,
    "width": 1,
    "height": 1,
    "measurementUnit": "Inches"
  },
  "weight": 1,
  "salesClass": "stock",
  "averageRating": null,
  "crosssells": null,
  "currencyCode": "USD",
  "displayName": null,
  "images":  [],
  "inStock": true,
  "isCartable": true,
  "isShipToStoreEligible": false,
  "isStorePickupEligible": false,
  "itemId": 4552121,
  "listPrice": 96.27,
  "manufacturer": "Style0098",
  "mastered": true,
  "minOrderQuantity": 1,
  "productBundle": false,
  "productMaster": false,
  "retailSet": false,
  "reviews": 0,
  "salePrice": 96.27,
  "thumbnailUri": "http://ess-uat02.uat.gsipartners.com/graphics/product_images/p4552121th.jpg",
  "warranties": null,
  "wasPrice": null
}


```






### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/products/<product_id>-<sku_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found 
Success HTTP Code|200 OK
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=38>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None







# Promotions
The Promotions resource is used to retrieve promotions associated with a product, category or store for the client application. 




## Get the Applicable Promotions for a Product
This request returns a list of promotions associated with a product. The resource uses the &#60;itemId&#62; and promotions to search for promotions associated with the &#60;itemId&#62; within a store.

> Sample response payload:

```JSON
{
  "total": 1,
  "promotions":  [
     {
      "name": "Buy One Get One 50% Off!! ",
      "rank": 100,
      "uri": "promotions/35068036",
      "id": 35068036,
      "promotionType": "BASIC"
    }
  ]
}
```

### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/products/<itemId>/promotions`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found 
Success HTTP Code|200 OK
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=36>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None





## Get a List of Promotions Available for the Store
This request returns a list of all promotions within a store. 

> Sample response payload:

```JSON
{
  "total": 178,
  "promotions":  [
     {
      "name": "A Dick's Sporting Goods' Exclusive!",
      "rank": 100,
      "uri": "promotions/2552903",
      "id": 2552903,
      "promotionType": "TAG"
    },
     {
      "name": "Free Shipping Eligible!",
      "rank": 9999,
      "uri": "promotions/21427816",
      "id": 21427816,
      "promotionType": "TAG"
    },
     {
      "name": "Free Shipping Plus Free Returns on Apparel!",
      "rank": 103,
      "uri": "promotions/21938266",
      "id": 21938266,
      "promotionType": "SHIPPING"
    },
    .
    .
    .
```


### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/promotions`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
Success HTTP Code|200 Success
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=26>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None





## Get Promotion Detail
This request returns details on a specific promotion specified by &#60;promotion_id&#62;.


> Sample response payload:

```JSON
{
  "name": "Buy One Get One 50% Off!! ",
  "couponCode": null,
  "couponCodeRequired": false,
  "description": null,
  "displayName": null,
  "id": 35068036,
  "title": "Buy One Get One 50% Off!! ",
  "promotionType": "BASIC",
  "legalContentMessage": null,
  "longTitle": "Buy One, Get One 50% Off Polar Water Bottles!! Must Add Both to Cart.",
  "ruleDescription": "<ul>\r\n<li> Discount only applied to qualifying product and will be automatically calculated at the time of checkout. </li>\r\n<li> 2nd Item must be of equal or lesser value. </li>\r\n<li> Offer valid only while supplies last and excludes out of stock & clearance merchandise and is not applicable to canceled orders due to out-of-stock merchandise. </li>\r\n<li> Order must be confirmed by 11:59 PM (ET) on August 1, 2015 to receive discount. </li>\r\n<li> Gift certificates, gift cards, taxes, shipping and handling charges, payment of DSG credit card charges or similar charges are excluded from any discount or free shipping offer. </li>\r\n<li> Discount not applicable with returned merchandise; total discount will be deducted from the value of any returned item to which the discount applied. </li>\r\n<li> Cannot be combined with any other promotional offer nor is this offer valid on previous purchases. </li>\r\n<li> Entire order must be shipped to a single address and customer is responsible for all shipping costs for returned merchandise. </li>\r\n<li> Event prices of select merchandise may differ from in-store prices. </li>\r\n<li> Shipping offers apply only to standard ground delivery. </li>\r\nCertain merchandise and brands excluded. \r\n<a href="http://www.dickssportinggoods.com/shop/index.jsp?categoryId=12312192&sr=1&origkw=12312192/new-window.php" target="_blank"><b>Click for details</b></a>\r\n\r\nThis promotional offer may be modified or terminated at any time without notice. <b>Additional exclusions may apply</b>.\r\n</ul>\r\n"
}
```


### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/promotions/<promotion_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found 
Success HTTP Code|200 OK
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=32>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None










# Carts
The carts endpoints are used to enact the cart management and checkout processes for the client application.





## Add Item to Cart


> Sample request payload:

```JSON
{
  "itemId":"12544485-12097248",
  "quantity":"1"
}
```


This request is used to request that specific items be added to the cart for the checkout process.
### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/items`



### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request
 | 403 Forbidden - invalid version or store code
 | 422 InvalidAttributeValue
 | 422 RequiredAttribute
 | 422 Unprocessable Entity
Success HTTP Code|204 No Content
Error Payload|See [Error Payload](payloads/index.htm#<id=6>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=6>>wnd=HelpPopup>>newwnd=false).
Response Payload|None
Mandatory Attributes|None
Additional Information|None





## Remove Item from Cart
This request is used to remove an item from the cart for the checkout process.
### HTTP Request

`DELETE https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/items/<line_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
HTTP Error Codes|401 Unauthorized - when authentication failed
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
 | 422 Unprocessable Entity - When LineItem not Found 
Success HTTP Code|HTTP Status Code 204
Error Payload|None
Request Payload|None
Response Payload|None
Mandatory Attributes|None
Additional Information|None





## View Cart
This request is used to request a view of the items in the cart for the checkout process.


> Sample response payload:

```JSON
{
  "cartId": 75919668163,
  "status": "OPEN",
  "lineItems":  [
     {
      "lineId": 1487513194,
      "itemPromotionDiscount":  {
        "currency": "USD",
        "amount": 0
      },
      "itemPromotions": null,
      "pliPoints": "pliPoints",
      "price":  {
        "currency": "USD",
        "amount": 96.27
      },
      "itemShippingMethod": "ShippingMethod",
      "shipmentTrackingURL": "TrackingUrl",
      "product":  {
        "ancestors":  [
           {
            "displayName": "ESS Collections",
            "rank": 1,
            "uri": "categories/3562866"
          },
           {
            "displayName": "ESS Global Category 3",
            "rank": 2,
            "uri": "categories/3036542"
          }
        ],
        .
        .
        .
```


### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|401 Unauthorized - when authentication failed
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
Success HTTP Code|200 Success
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=69>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None





## Update Quantity Request
This request is used to update the quantity of a specific item in the cart.

> Sample request payload:

```JSON
{
    "quantity" : "4",
}
```

### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/items/<line_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 NotFound - cart id is not valid or doesn't match auth token value
 | 404 NotFound - cart line item not found
 | 422 InvalidAttributeValue - if quantity is not valid for a line item
 | 422 RequiredAttribute - if quantity is not supplied
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=66>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=66>>wnd=HelpPopup>>newwnd=false).
Response Payload|None
Mandatory Attributes|None
Additional Information|None





## Add Promotion Request
This request is used to apply a promotion to the cart for the checkout process.

> Sample request payload:

```JSON
{
  "couponCode": "35068036"
}
```


### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/promotions`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 NotFound - cart id is not valid or does not match auth token
 | 422 InvalidAttributeValue - couponCode is not valid
 | 422 RequiredAttribute - couponCode is not provided
 | 422 AlreadyAdded
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=8>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=8>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Code 204 or 422 with error response
Mandatory Attributes|None
Additional Information|None





## Remove Promotion from Cart
This request is used to remove a promotion from the cart for the checkout process.
### HTTP Request

`DELETE https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/promotions/<code>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 422 InvalidAttributeValue - couponCode not valid
 | 422 RequiredAttribute - couponCode not provided
Success HTTP Code|204 Success
Error Payload|None
Request Payload|None
Response Payload|None
Mandatory Attributes|None
Additional Information|None





## Add Address Request
This request is used to add an address for the checkout process.

> Sample request payload:

```JSON
{
  "addressType": "billing",
  "firstName": "Joseph",
  "lastName": "Customer",
  "line1": "123 Main Street",
  "line2": "Apt 123",
  "line3": "",
  "city": "King of Prussia",
  "mainDivision": "PA",
  "countryCode": "US",
  "postalCode": "19406",
  "homePhone": "610-555-1212",
  "mobilePhone": "610-555-1213",
  "email": "joseph.customer@isp.net"
  "country": "USA"
}
```


### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/addresses`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 422 AddressValidationFailed
 | 422 InvalidAttributeValue
 | 422 AlreadyAdded
 | 422 RequiredAttribute - addressType not valid
Success HTTP Code|204 Success
Error Payload|See [Error Payload and/or Address Validation Error Payload](payloads/index.htm#<id=5>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=5>>wnd=HelpPopup>>newwnd=false).
Response Payload|None
Mandatory Attributes|"line2", "mobilePhone" and "title" are optional. 
 | "email" is mandatory if addressType is "billing". 
  | All other parameters are mandatory. 
Additional Information|None





## Update Address
This request is used to update an address for the checkout process.


> Sample request payload:

```JSON
{
  "addressType": "billing",
  "firstName": "Joseph",
  "lastName": "Customer",
  "line1": "123 Main Street",
  "line2": "Apt 123",
  "line3": "",
  "city": "King of Prussia",
  "mainDivision": "PA",
  "countryCode": "US",
  "postalCode": "19406",
  "homePhone": "610-555-1212",
  "country": "USA",
  "preferredBillingAddress": "true",
  "preferredShippingAddress": "false"
}
```


### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/addresses/<address_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 422 AddressValidationFailed
 | 422 RequiredAttribute
 | 422 InvalidAttributeValue
 | 422 AlreadyAdded
Success HTTP Code|204 Success
Error Payload|See [Error Payload and/or Address Validation Error Payload](payloads/index.htm#<id=63>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=63>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Code 204 or 422 with error response
Mandatory Attributes|Note that "line2" "mobilePhone" "email" and "title" are optional. 
 | All other parameters are mandatory.
Additional Information|None





## View Valid Shipping Methods for Cart
This is used to retrieve the valid shipping options for a consumer to view and select.  This is a GET request with no payload.

> Sample response payload:

```JSON
{
  "options":  [
     {
      "name": "Economy Ground, (6-10 business days)",
      "description": "?? restapi.shipOpDesc.Economy_Ground ??",
      "estimatedCharge": 15.99,
      "id": "Economy_Ground",
      "maxDays": null,
      "minDays": null
    },
     {
      "name": "Standard Ground, (3-5 business days)",
      "description": "Standard, (3-6 business days)",
      "estimatedCharge": 15.99,
      "id": "Standard_Ground",
      "maxDays": null,
      "minDays": null
    },
     {
      "name": "Second Day, (2-3 business days)",
      "description": "2 to 3 Day, (2-3 business days)",
      "estimatedCharge": 19.99,
      "id": "Second_Day",
      "maxDays": null,
      "minDays": null
    },
     {
      "name": "Overnight, (1-2 business days)",
      "description": "Overnight, (1-2 business days)",
      "estimatedCharge": 25.99,
      "id": "1DAY",
      "maxDays": null,
      "minDays": null
    }
  ]
}
```


### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/shipping_options`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|401 Unauthorized - when authentication failed
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found or no shipping address exists
Success HTTP Code|200 Success
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=70>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None





## Apply Selected Shipping Method to Cart
This method is used to apply the selected shipping method to the order at checkout.

> Sample request payload:

```JSON
{
    "id": "Economy_Ground"
}
```


### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/shipping_methods`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 422 RequiredAttribute
 | 422 InvalidAttributeValue
 | 422 AlreadyAdded
 | 422 Shipping_Address_Not_Defined
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=13>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=13>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Code 204 or 422 with error response
Mandatory Attributes|None
Additional Information|None





## Update Shipping Method to Cart
This is used to update a previously selected shipping method for the order, at checkout.

> Sample request payload:

```JSON
{
    "id": "Standard_Ground"
}
```


### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/shipping_methods`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 422 RequiredAttribute
 | 422 InvalidAttributeValue
 | 422 AlreadyAdded
 | 422 Shipping_Address_Not_Defined
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=67>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=67>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Code 204 or 422 with error response
Mandatory Attributes|None
Additional Information|None





## Checkout - Add Payment Information to Cart
This request is used to apply a payment method and payment to the cart for the checkout process.

The cart allows zero or one credit card payment. If you add credit card payment information to the cart, set the credit card security code in the [Checkout - Submit Order](#checkout---submit-order) API call. 

Gift card(s) are added in the [Checkout - Submit Order](#checkout---submit-order) API call. The order submit process will charge/deplete the gift card(s), then charge the remaining balance to the credit card. 


> Sample request payload:

```JSON
{
  "serviceId": "GSI_CREDITCARD",
  "saveToWallet": "true",
  "attributes": {
    "CreditCardNumber": "4123456789123456",
    "CreditCardExpiryYear": "2020",
    "CreditCardExpiryMonth": "11",
    "CreditCardTenderType": "VC",
    "CreditCardSecurityCode": "123"
  }
}
```



### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/payment`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 422 CreditCardValidationFailed
 | 422 DebitValidationFailed
 | 422 PaypalValidationFailed
 | 422 StoredValueValidationFailed
 | 422 RequiredAttribute
 | 422 InvalidAttributeValue
 | 422 AlreadyAdded
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=16>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=16>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Code 204 or 422 with [Error Response](payloads/index.htm#<id=16>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None





## Checkout - Update Payment Information to Cart
This request is used to update a specific payment method and payment to the cart for the checkout process.  Note that only the credit card expiration month and year can be updated via this method.

> Sample request payload:

```JSON
{
  "serviceId": "GSI_CREDITCARD",
  "saveToWallet": "true",
  "attributes": {
    "CreditCardExpiryYear": "2020",
    "CreditCardExpiryMonth": "11",
    "CreditCardTenderType": "VC",
    "EncrytedCardSwipe": ""
  }
}
```


### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/payment/<payment_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 422 CreditCardValidationFailed
 | 422 DebitValidationFailed
 | 422 PaypalValidationFailed
 | 422 StoredValueValidationFailed
 | 422 RequiredAttribute
 | 422 InvalidAttributeValue
 | 422 AlreadyAdded
Success HTTP Code|204 Success
Error Payload|None
Request Payload|See [Request Payload](payloads/index.htm#<id=18>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Code 204 or 422 with error response.
Mandatory Attributes|None
Additional Information|None





## Delete Payment Information from Cart
This request is used to delete a payment method and payment from the cart for the checkout process.
### HTTP Request

`DELETE https://<Public API Domain Name>/v<M.m>/stores/<store_id>/carts/<cart_id>/payment/<payment_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|403 Forbidden - invalid version or store code
 | 404 InvalidAttributeValue
 | 404 RequiredAttribute
Success HTTP Code|204 Success
Error Payload|None
Request Payload|None
Response Payload|None
Mandatory Attributes|None
Additional Information|None





# Orders
The orders requests are used to initiate the processing of an order. 



## Return Details and Status of User Entered Order Number
This request is used to retrieve order history for a specific order.
### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/orders/<order_id>?postal_code=<postal_code>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|400 Bad Request - when query parameter is invalid
 | 401 Unauthorized - invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
Success HTTP Code|200 Success
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=58>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|Postal code required if no authentication token
Additional Information|None





## Checkout - Submit Order
This request is used to post an order transaction in the checkout process.

Gift card(s) are added in this API call. The order submit process will charge/deplete the gift card(s), then charge the remaining balance to the credit card (if any). Credit cards are added via the [Checkout - Add Payment Information to Cart](#checkout---add-payment-information-to-cart) API call.

If you add credit card payment information to the cart via the [Checkout - Add Payment Information to Cart](#checkout---add-payment-information-to-cart) API call, set the credit card security code using this API call. 

> Sample request payload:

```JSON
{
  "cartId": "75919668163",
  "creditCardSecurityCode": "123",
}
```

> Sample response payload:

```JSON
{
  "orderId": 4537044963,
  "errors": null
}
```




### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/orders`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - when query parameter is invalid
 | 401 Unauthorized - when authentication failed
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
 | 422 Validation Error
Success HTTP Code|200 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=17>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=17>>wnd=HelpPopup>>newwnd=false).
Response Payload|See [Response Payload](payloads/index.htm#<id=17>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None





## Retrieve List of Orders for Account
This request is used to retrieve a list of orders for an account.
### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/orders`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|400 Bad Request - when query parameter is invalid
 | 401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 404 Found - when requested resource is not found 
Success HTTP Code|200 Success
Error Payload|None
Request Payload|See Optional Query Parameters below.
Response Payload|See [Response Payload](payloads/index.htm#<id=57>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Optional Query Parameters|days=&#60;orders placed in the last x days&#62;
 | status=&#60;valid status&#62;
 | pageable=&#60;pageableID&#62;
 | amount=&#60;number of orders&#62;
 | offset=&#60;order offset&#62;
 | pageSize=&#60;number of orders&#62; (default: 5; maximum value: 100)
 | startIndex=&#60;order offset&#62; (default: 5)
Additional Information|None





## Delete/Cancel Orders for Registered User
This request is used to delete or cancel an order for a registered user.
### HTTP Request

`DELETE https://<Public API Domain Name>/v<M.m>/stores/<store_id>/orders/<order_id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 422 Unprocessable Entity - invalid attribute value: OrderID; Invalidstate
 | 500 Internal Server Error - OtherError
Success HTTP Code|200 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=72>>wnd=HelpPopup>>newwnd=false).
Request Payload|None
Response Payload|None
Mandatory Attributes|None
Additional Information|None





## Delete/Cancel Orders for Guest User
This request is used to delete or cancel an order for a guest user.
### HTTP Request

`DELETE https://<Public API Domain Name>/v<M.m>/stores/<store_id>/orders/<order_id>?postal_code=<postal_code>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 422 Unprocessable Entity - invalid attribute value: OrderID; Invalidstate
 | 500 Internal Server Error - OtherError 
Success HTTP Code|200 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=71>>wnd=HelpPopup>>newwnd=false).
Request Payload|None
Response Payload|None
Mandatory Attributes|Postal code required if no authentication token. 
Additional Information|None






# Tokens
The token requests are used to create a new token or extend the validity of an existing token for the payment processing during checkout. The Method is POST.


## Create New Token

> Sample response payload:

```json
[
  {
    "expires": 1399062078880,
    "value": "016acbe0b1379a4c9676c9f32eb44a7adac0c1819ebafdf1b304
  4d0fffd59358d00f14e1bc53786e26274375b5f8ac0c",
    "cartId": 74885362737
  }
]
```


This method is used to create a new authentication-token and corresponding cart ID.

### Scenario 1:
Performing a POST to /tokens without an authentication-token value in the header returns a guest token (authentication-token).  This token is valid for 24 hours.  (The authentication-token is required when working with Carts, Orders and Accounts.)

### Scenario 2:
Performing a POST to /tokens with Basic Authorization will return a Registered user token. This authentication-token remains active and valid for a configurable amount of time.  Registered users will need a registered user token when working with Orders and Accounts endpoints.
<aside class="notice">
Token validity time is the same for both Registered and Guest Users. However, the difference between the two is that, whenever a guest user token is expired, the guest user loses any cart items that were added to cart Id where as a Registered user retrieves cart items once he logs back in even though the registered user token has expired.
</aside>

### Scenario 3:
Performing a POST to /tokens with Basic Authorization credentials (base64 encrypted user ID and password) and an authentication-token logs in the user and returns a token response message that may also include the cart id of the known user, if they have a cart. Logging in merges any cart items from the guest user (items added to the cart via an authentication-token only) to the persistent cart, if one exists for the user. 
The authorization header is the user's username and password in base64 encoding. The username and password are concatenated together with ":" separating them. The authorization header includes the word "Basic" plus a space character, then the encoded data. 
Per [http://www.ietf.org/rfc/rfc2617.txt](http://www.ietf.org/rfc/rfc2617.txt),
If the user agent wishes to send the userid "Aladdin" and password "open sesame", it would use the following header field:

`Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`

Decoding this string results in: 

`Aladdin:open sesame`


### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/tokens`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
 | Optional Create New Token Request Header:
 | Examples:
 | authorization : basic cC5zY2huZWlkZXJAaW50ZXJzaG9wLmRlOnNjaG5laWRlcg==\n
 | authentication-token: 0NRIUOpR+rK/CYYzbyocdOcTeC/oAp7CaA5xNYqMQ2tzCs43yFcMGw==
 | If the request header contains the optional tags 'authorization' and 'authentication-token' a switch user is enforced.  The resulting 'authentication-token' in the response is the one for the new user. Possible basket content is kept in the way that the content of the old user's cart is copied into the new users cart. If so, the response contains the new cart's id.
HTTP Error Codes|401 Unauthorized - incorrect Authorization header, invalid authentication-token
 | 403 Forbidden - Invalid version or store code 
Success HTTP Code|200 OK
Error Payload|None
Request Payload|See Create New Token Request Header above and in Additional Information below.
Response Payload|See [Response Payload](payloads/index.htm#<id=20>>wnd=HelpPopup>>newwnd=false).
 | The field ‘cartId’ is present when the create token call is for both a registered user and a guest user. (This field exists if the request header contains or does not contain a valid authorization field in the header).
Mandatory Attributes|None
Additional Information|Optional Create New Token Request Header:
 | Performing a POST to /tokens without basic authentication returns a guest token.
 | Add basic authentication to return a registered user token.
 | Add basic authentication and a guest authentication-token to return a registered user token and have items in the guest’s cart get merged to the registered cart.





## Extend Existing Token
Before the authentication-token generated using POST method expires (see [Create New Token](#create-new-token) ), the validity of the token can be extended to provide uninterrupted service by extending the authentication-token. This method is used to extend the validity of an existing token for a configurable amount of time.

### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/tokens`

> Sample response payload:

```JSON

{
  "expires": 1426007117448,
  "value": "4195a6787810f033926023587166b89730bd383d5460d534f62fad1e7b8c6327451f02a7c67d087cb503ff292f991285",
  "cartId": 75919785063
}
```

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|401 Unauthorized - incorrect Authorization header, invalid authentication-token
 | 403 Forbidden - Invalid version or store code 
Success HTTP Code|200 OK
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=25>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None








# Accounts
The accounts endpoints are used for maintenance or updates to consumer accounts.


## Get Account Details
This request retrieves current account details including payment, shopping cart and user group information.
> Sample response payload:

```JSON

```

### HTTP Request

`GET https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-`


### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Codes|401 Unauthorized - when authentication failed
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
 | 422 UserNotFound
 | 500 Internal Server Error - OtherError
Success HTTP Code|200 Success
Error Payload|None
Request Payload|None
Response Payload|See [Response Payload](payloads/index.htm#<id=27>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes|None
Additional Information|None




## Update Account Details
This request updates account details that have been entered (revised) by the consumer in the client application.

> Sample request payload:

```JSON

```
### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - The request is syntactically incorrect, ParameterMissing (Mandatory parameter missing), Email is invalid, WrongGenderFormat, WrongDate
 | 401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
 | 422 Unprocessable Entity - WrongLoginData (Incorrect login or password in request)
 | 500 Internal Server Error - OtherError 
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=62>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=62>>wnd=HelpPopup>>newwnd=false).
Response Payload|None
Mandatory Attributes|email
 | password
 | Authentication
Additional Information|"gender" - may have following value {"male", "female", "decline"}
 | birthday - has following format: yyyy-MM-dd
 | locale - is an existing locale in the Shop system (like 'de-DE', or 'en-US')
 | email - changing email will change 3 values: order confirmation email, password reminder email and login.
 | password - used only to modify the login (email) information.  Another service needs to be used to change user password.




## Register Account
This request posts information to register an account (create new registered user in the store).


> Sample request payload:

```JSON

{
  "login": "jcustomer",
  "email": "jcustomer@isp.net",
  "firstName": "John"
  "lastName": "Customer"
  "optIn" : "true"
  "password": "password123",
  "confirmPassword": "password123"
}
```



### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/registration`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - The request is syntactically incorrect, login - Mandatory Parameter Missing, password - Mandatory Parameter Missing, confirmPassword - Mandatory Parameter Missing, WrongDate, Wrong locale, Wrong OptIn value. Only (True/False), Login and Email don't match, Login ID is invalid, Email ID is invalid
 | 400 Bad Request - When registering a new account for already existing account API throws 400 Error with Transformer Messaging Exception
 | 401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
 | 422 Unprocessable Entity - Login already in use, Password Confirmation Does Not Match With Password
 | 500 Internal Server Error - OtherError 
Success HTTP Code|204 Success
Error Payload|None
Request Payload|See [Request Payload](payloads/index.htm#<id=52>>wnd=HelpPopup>>newwnd=false).
Response Payload|None
Mandatory Attributes|login, firstName, lastName, optIn, password, confirmPassword
Additional Information|None




## Reset Password
This request resets the user password and sends the new password via email.  SecurityAnswer is used instead of login/password authentication.

> Sample request payload:

```JSON

```

### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/password`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - The request is syntactically incorrect, ParameterMissing (login is mandatory)
 | 401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
 | 422 Unprocessable Entity - AccountNotFound, WrongSecurityAnswer, SecurityAnswerMissing (new password format is wrong: is too short or has no numbers, etc.), Security Error (user not logged in or not registered), WrongSecurityAnswer 
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=55>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=55>>wnd=HelpPopup>>newwnd=false).
Response Payload|Processing Result
Mandatory Attributes|Login
 | Answer
Additional Information|The service sends the new generated password via email. The password will be valid just for the first login. After that the user has to choose a new password.




## Update Password
This request updates the password of the current user.
> Sample request payload:

```JSON

```

### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-/password`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - The request is syntactically incorrect, ParameterMissing (currentPassword and newPassword are mandatory)
 | 401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 404 Not Found - when requested resource is not found
 | 422 Unprocessable Entity - SecurityError (User not logged in or not registered), WrongPasswordError, NewPasswordFormatError (New password is too short or has no numbers, etc.)
 | 500 Internal Server Error - OtherError 
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=64>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=64>>wnd=HelpPopup>>newwnd=false).
Response Payload|Processing result
Mandatory Attributes|newPassword
 | currentPassword
Additional Information|new password must correspond to the password rules of the Webstore











## Add Account Address
This request adds a new address to the current user account.
> Sample request payload:

```JSON

```

### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-/addresses`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad request - when request payload is malformed
 | 401 Unauthorized - when authentication failed
 | 403 Forbidden - invalid version or store code
 | 422 ParameterMissing
 | 422 UserNotFound
 | 422 CountryNotFound
 | 500 Internal Server Error - OtherError
Success HTTP Code|204 Success
Error Payload|See [Error Payload or Address Validation Error Payload](payloads/index.htm#<id=4>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=4>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Status Code 204 or error code with processing result payload.
Mandatory Attributes|firstName, lastName, line1, City, mainDivision, countryCode, postalCode
Additional Information|countryCode - is an existing country in the Webstore (ISO 3166-2)
 | preferredBillingAddress - possible values: true, false. Missing or different value will default to false.
 | preferredShippingAddress - possible values: true, false. Missing or different value will default to false.









## Update Account Address
This request updates an address for the current user account.
> Sample request payload:

```JSON

```


### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-/addresses/<address id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
Header|AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - The request is syntactically incorrect, ParameterMissing, CountryNotFound
 | 401 Unauthorized - incorrect Authorization header, invalid authentication-token (when authentication failed)
 | 403 Forbidden - invalid version or store code
 | 404 Found - when requested resource is not found
 | 422 Unprocessable Entity - UserNotFound, AddressNotFound
 | 500 Internal Server Error - OtherError 
Success HTTP Code|204 Success
Error Payload|See [Error Payload or Address Validation Error Payload](payloads/index.htm#<id=61>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=61>>wnd=HelpPopup>>newwnd=false).
Response Payload|HTTP Status Code 204 or error code with processing result payload
Mandatory Attributes|None. Only in the request existing attributes will be updated
Additional Information|countryCode - is an existing country in the Shop system (ISO 3166-2).
 | preferredBillingAddress - possible values: true, false. Missing or different value will default to false.
 | preferredShippingAddress - possible values: true, false. Missing or different value will default to false.










## Delete Address
This request deletes a specified address from the current user account.


### HTTP Request

`DELETE https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-/addresses/<address id>`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad request - when request payload is malformed
 | 401 Unauthorized - when authentication failed
 | 403 Forbidden - invalid version or store code
 | 422 ParameterMissing
 | 422 UserNotFound
 | 422 AddressNotFound
 | 500 Internal Server Error - OtherError
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=21>>wnd=HelpPopup>>newwnd=false).
Request Payload|None
Response Payload|HTTP Status Code 204 or error code with processing result payload.
Mandatory Attributes|None
Additional Information|None



## Add Payment
This request creates a new payment instrument info object for an account. (As of this writing, only credit card service is applicable.)
> Sample request payload:

```JSON

```


### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-/payments/`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - when syntax is invalid
 | 403 Forbidden - invalid version or store code
 | 422 PaymentNotAvailable
 | 422 UserNotFound (user not logged in or not registered)
 | 422 AlreadyExists
 | 500 Internal Server Error - OtherError
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=7>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=7>>wnd=HelpPopup>>newwnd=false).
Response Payload|None
Mandatory Attributes|The mandatory attributes are specific to the payment method.
Additional Information|None











## Update Payment
This request updates an existing payment Instrument Info object for an account. (Only expiry date updates should be used for credit cards.)
> Sample request payload:

```JSON

```

### HTTP Request

`PUT https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-/payments/`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - when syntax is invalid
 | 403 Forbidden - invalid version or store code
 | 422 PaymentInstrumentInfoNotFound
 | 422 UserNotFound (user not logged in or not registered)
 | 422 WrongAttributes (Attribute values not valid for given payment method)
 | 422 UpdateFailed
 | 500 Internal Server Error - OtherError
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=65>>wnd=HelpPopup>>newwnd=false).
Request Payload|See [Request Payload](payloads/index.htm#<id=65>>wnd=HelpPopup>>newwnd=false).
Response Payload|None
Mandatory Attributes|The mandatory attributes are specific to the payment method
Additional Information|Not all payment method attributes can be updated. Creditcard allows updating:
 | CreditCardExpiryYear
 | CreditCardExpiryMonth






## Delete Payment
This request removes the payment instrument info object from a user account.

### HTTP Request

`DELETE https://<Public API Domain Name>/v<M.m>/stores/<store_id>/accounts/-/payments/`

### Request Details

Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
HTTP Error Codes|400 Bad Request - when syntax is invalid
 | 403 Forbidden - invalid version or store code
 | 422 PaymentInstrumentInfoNotFound
 | 422 UserNotFound (user not logged in or not registered)
 | 500 Internal Server Error - OtherError
Success HTTP Code|204 Success
Error Payload|See [Error Payload](payloads/index.htm#<id=22>>wnd=HelpPopup>>newwnd=false).
Request Payload|None
Response Payload|None
Mandatory Attributes|None
Additional Information|None


# Gift Cards
The Gift Cards API is used to retrieve a balance for the supplied gift card number.  Responses are returned in JSON format.



## Get Gift Card Balance

This request returns a balance for the supplied gift card.

> Sample request payload:

```JSON

{
  "cardNumber": "7008013283433989",
  "pin": "04595363"
}

```

> Sample response payload:

```JSON

{
  "balance": "$289.00"
}


```

### HTTP Request

`POST https://<Public API Domain Name>/v<M.m>/stores/<store_id>/balance_inquiries`

### Request Details


Item                 | Description
---------------------------------- | -----------------------------------
Header | apikey: &#60;apikey&#62;
 | AUTHENTICATION-TOKEN (Use the POST /tokens endpoint to receive both an AUTHENTICATION-TOKEN and a corresponding cart ID.)
 | Accept: application/json
 | Content-Type: application/json 
 | Accept-Language: &#60;locale&#62; : specifies the locale for the returned response.  Required for all store locales except en-US.  When not used, defaults to en-US.  Values are store dependent. Examples include en-CA, fr-FR, en-GB, de-DE.
Optional Header Parameters | Accept-Encoding: gzip (when using data compression for the response payload). [Click here](overview/index.htm#<id=10>>wnd=HelpPopup>>newwnd=false) for details.
HTTP Error Code | 403 Forbidden - invalid version or store code
Success HTTP Code | 200 OK
Error Payload | See [Error Payload](payloads/index.htm#<id=12>>wnd=HelpPopup>>newwnd=false).
Request Payload | See [Request Payload](payloads/index.htm#<id=12>>wnd=HelpPopup>>newwnd=false).
Response Payload | See [Response Payload](payloads/index.htm#<id=12>>wnd=HelpPopup>>newwnd=false).
Mandatory Attributes | Request payload.
Additional Information | None



