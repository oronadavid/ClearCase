Original App Design Project - README 
ClearCase

Description
The purpose of ClearCase is to allow local liquor stores, convenience stores and gas stations to order liquor directly from the maker, preventing unwanted and unsellable liquor from being dumped on these stores

App Evaluation

Category: Business
Mobile: Mobile
Story: Convenience stores need a modern technology that tracks alcohol inventory and uses tools like AI to help the store owner bring in products. This will depend on the season or events. The app should also be able to advise on how much product to order to minimize inventory waste and maximize profits.
Market: Liquor store/gas station/convenience store owners or stockers
Habit: As needed
Scope: Narrow
Product Spec
1. User Stories (Required and Optional)

Required Must-have Stories:
- Users can create/log in to account
- Users are able to check stock of items
- Users are able to add items to stock
- Users are able to receive order recommendations
- Users are able to order more product
- Users can view product details

Optional Nice-to-have Stories

- Users can use barcode scanner with their phone camera and add products to inventory and see product details such as price, sales, stock, etc.
- Users can use AI to consider local weather and events when ordering product
- Users can connect POS to app to calculate inventory 

2. Screen Archetypes

Login/Create account
Users are able to create or log into account

Dashboard
Users can see top selling products, items they need more of, and have the ability to navigate to other screens all in one place

Item Details
Gives specific details or a certain item such as price, inventory, sales trends

Inventory
User can see the items in stock, and filter by stock numbers or sales

Recommendation
Users can view what products are recommended to order

Order
User can order items that are low in stock

3. Navigation
Create account leads to creation page
Creation page leads to dashboard
Login leads to dashboard
Dashboard leads to stock or item details depending on needs
Stock or items details leads to order screen
Dashboard leads to recommended orders
Recommended orders leads to order screen


[BONUS] Digital Wireframes & Mockups
![](https://github.com/oronadavid/ClearCase/blob/main/Checkout.png "Checkout page")
![](https://github.com/oronadavid/ClearCase/blob/main/Dashboard.png "Dashboard page")
![](https://github.com/oronadavid/ClearCase/blob/main/Inventory.png "Inventory page")
![](https://github.com/oronadavid/ClearCase/blob/main/Item%20Details.png "Item Details page")
![](https://github.com/oronadavid/ClearCase/blob/main/Recommendations.png "Recommendations page")
![](https://github.com/oronadavid/ClearCase/blob/main/Sign%20In.png "Sign In page")
[BONUS] Interactive Prototype
Schema
Models

Store
Property	Type	Description
id, String,	unique id for the store
name,	String,	name of store
email, String, used for login and contact
password, String, used for authentication
address, String, store's address

Product
Property	Type	Description
id, String, unique id for product
name, String, name of the product
sku, String, SKU identifier
category, String, category of drink (wine, beer, etc.)
price, Decimal, price per unit
imageURL, String, URL for product image

InventoryItem
Property	Type	Description
id, String, unique id
storeId, String, link to store
productId, String, link to product
quantity, Number, current stock amount
lastUpdated, Date, last time inventory was counted 

Order
Property	Type	Description
id, String, unique order id
storeId, String, store placing the order
status, String, pending, shipped, complete
createdAt, Date, order time

Networking
Authentication
[POST] /auth/signup – Register a new store
[POST] /auth/login – Login store
[GET] /stores/:id – Get store profile

Inventory
[GET] /inventory/:storeId – Get current inventory for a store
[POST] /inventory – Add product to inventory
[PATCH] /inventory/:id – Update quantity of an inventory item
[GET] /inventory/:storeId/history – Get historical inventory snapshots
[GET] /inventory/:storeId/sales/:productId – Get total amount sold for all products based on last cycle

Products
[GET] /products – Get list of all available products
[GET] /products/:id – Get detailed info about a specific product
[GET] /products/:id/sales/:storeId – Get sales data for a product in a specific store (amount sold/trends)

Orders
[POST] /orders – Create new order
[GET] /orders/:storeId – Get all orders for a store
[GET] /orders/:id – Get specific order
[POST] /order-items – Add items to an order

Recommendations
[GET] /recommendations/:storeId – Get current product recommendations
[POST] /recommendations/generate – Trigger AI to generate new recommendations
