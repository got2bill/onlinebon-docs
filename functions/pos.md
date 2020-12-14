# POS

![POS](./images/pos.png)

## Sessions

Before using the POS, the user has to **start a session**. It represents a timespan a user actively used the POS. At the end of this timespan, a session report will be created.

There can be only 1 active session of a pos.

### Start a new session

**API-ENDPOINT:** https://onlinebon.docs.apiary.io/#reference/v2/sessions/start-a-session

A user has to start a session to use the POS and start creating receipts. He has to option to transfer change funds from the cashbook into the cashdesk.
A user can only start a session if there is no other session active for this cashdesk.

<img src="./images/session_start.png" width="400" />

### End current session

**API-ENDPOINT:** https://onlinebon.docs.apiary.io/#reference/v2/sessions/end-a-session

A user with an active session can end this session every time. When ending the session, a session report will be created which summarize the activity during the session. 

<img src="./images/session_end.png" width="400" />

## Products

### Product Configuration
- **SERIAL:** You have to provide a serial number when adding a product with this option to a receipt
- **ACQUISITION_VALUE:** You have to provie an acquisiton value whe adding a product with this option to a receipt. This has to be used for differential tax usage.
- **COPYRIGHT:** There will be a copyright notice on the receipt if you add an product with this option to the receipt
- **ADDITIONAL_INFORMATION:** You can provide additional information to the receipt item of you add a product with this option to the receipt

### List productgroups

Productgroups can be be structured within multiple layers. Initially only productgroups of the root layer will be displayed.

If you click on a productgroup: 
 - all products of this productgroup will be listed in the product-section. 
 - all sub-productgroup of this productgroup will be displayed in the productgroup navigation.

### List products

A product must be attached to a productgroup. Initially all products will be displayed. 

#### Filter & pagination
- The **product-pagination** can be used to paginate through the product. 
- The products are **ordererd by the past sell count**.
- The **product-search-field** can be used to search for a specific product.

When you click on a product, a new invoice item with this product will be created.

### Create new productgroup
You can create a productgroup in the main level or as a subproductgroup of an already exxisting productgroup.

### Create new product
When you create a product, you have to add it into a productgroup.
You can set the price nominale to a specific price or to 0. If you set the nominale to 0, you can chosse a price everytime you add the product to a receipt.
You can choose between specific product configurations to influence the receipt when adding a product to it. 


## Clients

### Search for a client

### create a new client

### edit a client

## Receipts

### Add receiptItem to receipt

### Edit a receiptItem
### Add a discount to a receiptItem

### Add a discount to a receipt

### Add a client to a receipt

### Persist a receipt

#### The following rules apply when persisting a receipt:
- the account of the user must be in one of the following status: TESTING, ACTIVATED or ACTIVATING
- the cashdesk has to be open (active session)
- the cashdesk of the account has to be started (start-receipt created)
- the overall value of the receipt could not bring the balance of the cashdesk into a negative state

### Cancel a receipt

### Print a receipt

### Send a receipt via email
