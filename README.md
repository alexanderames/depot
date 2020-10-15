# Depot

This application was built using the Pragmatic Programmer's book on Rails 6.

<!-- TOC -->

- [Tables](#tables)
- [Endpoints](#endpoints)
- [Background Job](#background-job)
- [Testing](#testing)

<!-- /TOC -->

## Tables

The following are the models/tables in this application:

- Cart
  - Where products are added using Line Items

- Line Item
  - Belongs to Order, Cart, and Product
  - Represents Products in the Order

- Order
  - Where the Line Items are summarized
  - Pay Type enum is used to help a user choose how they will pay for their Order

- Product
  - What the Depot sells to it's users
  - `rails db:seed` will populate database with Products

- User
  - An admin User, that can inspect what Orders have been made
  - Requires authentication
  - Stores encrypted password

## Endpoints

The following are RESTful endpoints.

- Store:

```curl
GET /
```

The StoreController's #index operation is the application's root route.

- Carts:

```curl
GET /carts
GET /carts.json
GET /carts/1
GET /carts/1.json
GET /carts/new
GET /carts/1/edit
POST /carts
POST /carts.json
PATCH/PUT /carts/1
PATCH/PUT /carts/1.json
DELETE /carts/1
DELETE /carts/1.json
```

- Line Items:

```curl
GET /line_items
GET /line_items.json
GET /line_items/1
GET /line_items/1.json
GET /line_items/new
GET /line_items/1/edit
POST /line_items
POST /line_items.json
PATCH/PUT /line_items/1
PATCH/PUT /line_items/1.json
DELETE /line_items/1
DELETE /line_items/1.json
```

- Orders:

```curl
GET /orders
GET /orders.json
GET /orders/1
GET /orders/1.json
GET /orders/new
GET /orders/1/edit
POST /orders
POST /orders.json
PATCH/PUT /orders/1
PATCH/PUT /orders/1.json
DELETE /orders/1
DELETE /orders/1.json
```

- Products:

```curl
GET /products
GET /products.json
GET /products/1
GET /products/1.json
GET /products/new
GET /products/1/edit
POST /products
POST /products.json
PATCH/PUT /products/1
PATCH/PUT /products/1.json
DELETE /products/1
DELETE /products/1.json
```

- Users:

```curl
GET /users
GET /users.json
GET /users/1
GET /users/1.json
GET /users/new
GET /users/1/edit
POST /users
POST /users.json
```

## Background Job

This application has one background job called **ChargeOrderJob**, which is enqueued when an Order is created.

## Testing

There are two ways to test the features of this application:

- rails test (runs all the unit testing)
- rails test:system (runs system tests using headless chrome)

All tests should pass.
