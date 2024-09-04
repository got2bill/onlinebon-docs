# Products

## Product Configuration
- **SERIAL:** You have to provide a serial number when adding a product with this option to a receipt
- **ACQUISITION_VALUE:** You have to provie an acquisiton value whe adding a product with this option to a receipt. This has to be used for differential tax usage.
- **COPYRIGHT:** There will be a copyright notice on the receipt if you add an product with this option to the receipt
- **ADDITIONAL_INFORMATION:** You can provide additional information to the receipt item of you add a product with this option to the receipt

## List productgroups

**API-ENDPOINT:** [GET /productgroups](https://onlinebon.docs.apiary.io/#reference/v1/productgroups/list-productgroups)

Productgroups can be be structured within multiple layers. Initially only productgroups of the root layer will be displayed.

If you click on a productgroup: 
 - all products of this productgroup will be listed in the product-section. 
 - all sub-productgroup of this productgroup will be displayed in the productgroup navigation.

## List products

**API-ENDPOINT:** [GET /products](https://onlinebon.docs.apiary.io/#reference/v1/products/list-products)

A product must be attached to a productgroup. Initially all products will be displayed. 

### Filter & pagination
- The **product-pagination** can be used to paginate through the product. 
- The products are **ordererd by the past sell count**.
- The **product-search-field** can be used to search for a specific product.

When you click on a product, a new invoice item with this product will be created.

## Create new productgroup

**API-ENDPOINT:** [POST /productgroups](https://onlinebon.docs.apiary.io/#reference/v1/products/create-a-productgroup)

You can create a productgroup in the main level or as a subproductgroup of an already exxisting productgroup.

## Create new product

**API-ENDPOINT:** [POST /productgroups](https://onlinebon.docs.apiary.io/#reference/v1/products/create-a-productgroup)

When you create a product, you have to add it into a productgroup.
You can set the price nominale to a specific price or to 0. If you set the nominale to 0, you can chosse a price everytime you add the product to a receipt.
You can choose between specific product configurations to influence the receipt when adding a product to it. 