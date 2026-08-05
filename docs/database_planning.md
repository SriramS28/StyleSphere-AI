##User Module
users
roles
addresses

##Vendor Module
vendors
vendor_documents

##Product Module
products
categories
subcategories
brands
product_images
product_variants

##Inventory Module
inventory
stock_history

##Shopping Module
cart
cart_items
wishlist

##Order Module
orders
order_items

##Payment Module
payments
refunds

##Review Module
reviews

##Coupon Module
coupons
coupon_usage

##AI Module
ai_recommendations
style_history
virtual_tryon_history

##Notification Module
notifications




Relationships
Let's understand how the data connects.

One Customer can place Many Orders
Customer
↓
Order
↓
Order
↓
Order
This is called: One-to-Many


One Product can have Many Reviews
Product
↓
★★★★★
↓
★★★★☆
↓
★★★★★
Again: One-to-Many 


One Category contains Many Products
T-Shirts
↓
White Tee
↓
Black Tee
↓
Blue Tee
Again: One-to-Many


One Order contains Many Products
Example:
Order #101
↓
T-Shirt
↓
Jeans
↓
Shoes


But...The same T-Shirt can also be in:
Order #102
↓
T-Shirt
This is:Many-to-Many

We solve it with an extra table:
Order
↓
Order Items
↓
Product




Naming Convention

We'll use consistent naming throughout the project.

Tables Lowercase, plural.
users
products
orders
reviews

Columns Snake case.
first_name
last_name
created_at
updated_at

Primary Key
user_id
product_id
order_id

Foreign Key
user_id
product_id
vendor_id

The names stay the same across tables.


Final Database Flow
Users
   │
   ├── Addresses
   │
   ├── Orders
   │      │
   │      ├── Order Items
   │      │
   │      └── Payments
   │
   ├── Wishlist
   │
   └── Reviews

Vendors
   │
   ├── Products
   │      │
   │      ├── Product Images
   │      ├── Inventory
   │      └── Categories