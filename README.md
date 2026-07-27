# Dropshipping Marketplace Workflow

## Overview
A multi-vendor dropshipping marketplace connects **admins, sellers, customers, and external suppliers** in one coordinated system. The platform supports product listing, variant management, order routing, fulfilment, returns, refunds, commissions, and seller payouts.

---

## User Roles

### 1) Admin
Responsible for platform governance, seller approval, operations control, dispute handling, wallet oversight, and reporting.

### 2) Seller
Manages store setup, product publishing, inventory or supplier mappings, order fulfilment, returns, and earnings.

### 3) Customer
Browses products, places orders, pays online, tracks shipments, submits reviews, and requests returns or refunds.

---

## High-Level Marketplace Flow

```mermaid
flowchart TD
    A[Seller Registration] --> B[Seller Verification]
    B --> C[Store Created]
    C --> D[Products Added]
    D --> E[Customer Browses Products]
    E --> F[Customer Places Order]
    F --> G[Payment Successful]
    G --> H[Order Routed to Seller]
    H --> I[Fulfilment]
    I --> J[Shipment]
    J --> K[Delivery]
    K --> L[Review / Return]
    L --> M[Seller Payout]
```

---

## Seller Onboarding Workflow

```mermaid
flowchart TD
    A[Seller Creates Account] --> B[Admin Reviews Seller]
    B --> C{Approved?}
    C -- No --> D[Rejected / Resubmission Required]
    C -- Yes --> E[Seller Dashboard Activated]
    E --> F[Create Store]
    F --> G[Add Products]
    G --> H[Start Selling]
```

### Key Seller Steps
- Create account
- Submit verification details
- Receive admin approval
- Configure store profile
- Add and publish products

---

## Product Creation Workflow

Sellers can add products from three sources:

- **Own Product**
- **Amazon Product**
- **AliExpress Product**

```mermaid
flowchart TD
    A[Add Product] --> B{Product Source}
    B --> C[Own Product]
    B --> D[Amazon Product]
    B --> E[AliExpress Product]

    C --> F[Enter Product Details]
    D --> F
    E --> F

    F --> G[Publish Product]
```

### Product Fields
- Product title
- Description
- Images
- Category
- Variants
- Selling price
- Profit margin
- Stock / availability
- Shipping details
- Return policy

---

## Product Variant Structure

Example:

```text
Nike Shoes
├── Black
│   ├── UK7
│   ├── UK8
│   └── UK9
└── White
    ├── UK7
    ├── UK8
    └── UK9
```

### Variant Data
Each variant can store:
- SKU
- Supplier SKU
- Supplier price
- Selling price
- Weight
- Stock quantity
- Barcode

---

## Customer Shopping Workflow

```mermaid
flowchart TD
    A[Visit Website] --> B[Search / Browse Products]
    B --> C[Apply Filters]
    C --> D[Open Product Page]
    D --> E[Select Variant]
    E --> F[Add to Cart]
    F --> G[Checkout]
    G --> H[Payment]
    H --> I[Order Created]
```

### Customer Actions
- Search products
- Filter by category, price, brand, and availability
- Select variant
- Add to cart
- Checkout securely
- Track order status

---

## Order Processing Workflow

```mermaid
flowchart TD
    A[Customer Order] --> B[Payment Confirmed]
    B --> C[Order Split by Seller]
    C --> D[Seller Receives Order]
    D --> E[Fulfilment Starts]
```

If a single checkout contains products from multiple sellers, the system automatically splits the order into separate seller sub-orders.

---

## Fulfilment Workflows

### 1) Seller-Owned Product
```mermaid
flowchart TD
    A[Order Received] --> B[Seller Packs Product]
    B --> C[Seller Ships Product]
    C --> D[Tracking Uploaded]
    D --> E[Customer Receives Product]
```

### 2) Amazon Product
```mermaid
flowchart TD
    A[Customer Places Order] --> B[Seller Receives Notification]
    B --> C[Seller Places Order on Amazon]
    C --> D[Amazon Ships Product]
    D --> E[Tracking Added to Marketplace]
    E --> F[Customer Receives Product]
```

### 3) AliExpress Product
```mermaid
flowchart TD
    A[Customer Places Order] --> B[Marketplace Sends Supplier Order]
    B --> C[AliExpress Supplier Ships]
    C --> D[Tracking Returned]
    D --> E[Marketplace Updates Order]
    E --> F[Customer Receives Product]
```

---

## Inventory Management

### Seller-Owned Products
- Marketplace maintains actual stock quantity
- Stock reduces after successful purchase
- Stock increases after approved restock or return

Example:
```text
Inventory = 100
Customer buys 2
Inventory = 98
```

### Amazon Products
- Marketplace does not manage physical inventory
- System only stores supplier mapping and availability link

### AliExpress Products
- Supplier stock can be synced
- Marketplace updates product availability based on supplier data

---

## Payment and Payout Workflow

```mermaid
flowchart TD
    A[Customer Pays] --> B[Payment Gateway Confirms]
    B --> C[Platform Receives Payment]
    C --> D[Order Created]
    D --> E[Seller Balance Pending]
    E --> F[Delivery Completed]
    F --> G[Return Window Ends]
    G --> H[Seller Balance Released]
    H --> I[Seller Withdraws Funds]
```

### Commission Flow
- Customer pays full order amount
- Platform deducts commission
- Seller receives net earnings
- Approved earnings move to seller wallet
- Seller requests withdrawal
- Admin approves transfer

---

## Wallet System

### Seller Wallet Balances
- Available balance
- Pending balance
- Withdrawn amount
- Total earnings

### Withdrawal Flow
```mermaid
flowchart TD
    A[Seller Requests Withdrawal] --> B[Admin Reviews Request]
    B --> C{Approved?}
    C -- No --> D[Request Rejected]
    C -- Yes --> E[Payment Sent]
    E --> F[Transaction Recorded]
```

---

## Return and Refund Workflow

### Return Request
```mermaid
flowchart TD
    A[Customer Requests Return] --> B[Select Reason]
    B --> C[Seller Reviews Request]
    C --> D{Approved?}
    D -- No --> E[Return Rejected]
    D -- Yes --> F[Return Accepted]
```

### Seller-Owned Product Return
```mermaid
flowchart TD
    A[Customer Ships Return] --> B[Seller Receives Item]
    B --> C[Inspection]
    C --> D{Restock?}
    D -- Yes --> E[Inventory Increased]
    D -- No --> F[Damaged / Discarded Stock]
```

### Refund Flow
```mermaid
flowchart TD
    A[Return Approved] --> B[Refund Created]
    B --> C[Gateway Processes Refund]
    C --> D[Customer Receives Refund]
    D --> E[Refund Logged]
    E --> F[Seller Balance Updated]
```

---

## Review Workflow

```mermaid
flowchart TD
    A[Order Delivered] --> B[Customer Rates Product]
    B --> C[Customer Writes Review]
    C --> D[Seller Rating Updated]
    D --> E[Product Rating Updated]
```

Reviews help improve trust, conversion rate, and product visibility.

---

## Notification System

### Trigger Events
- New order
- Payment success
- Shipment update
- Delivery confirmation
- Return request
- Refund processed
- New review
- Withdrawal approved

### Delivery Channels
- Email
- SMS
- Push notification
- In-app notification

---

## Admin Dashboard Responsibilities

The admin can manage:
- Sellers
- Customers
- Products
- Orders
- Categories
- Brands
- Returns
- Refunds
- Wallets
- Withdrawals
- Coupons
- Reviews
- Reports
- Settings

---

## Seller Dashboard Responsibilities

The seller can manage:
- Store profile
- Products
- Variants
- Orders
- Customers
- Wallet
- Returns
- Reviews
- Coupons
- Analytics
- Withdrawals

---

## Customer Dashboard Responsibilities

The customer can manage:
- Profile
- Addresses
- Orders
- Wishlist
- Cart
- Returns
- Refunds
- Reviews
- Notifications

---

## Supplier Mapping Structure

Each marketplace variant should map to its supplier record:

```text
Marketplace Variant
├── Supplier
├── Supplier Product ID
├── Supplier Variant ID
├── Supplier URL
└── Supplier Price
```

This mapping ensures correct fulfilment, tracking, pricing, and automation.

---

## Core Database Flow

```mermaid
flowchart TD
    U[User]
    U --> S[Seller]
    U --> C[Customer]

    S --> P[Products]
    P --> V[Variants]
    P --> I[Images]
    P --> M[Supplier Mapping]

    S --> O[Orders]
    S --> R[Returns]
    S --> W[Wallet]
    S --> X[Withdrawals]

    C --> CA[Cart]
    C --> WI[Wishlist]
    C --> CO[Orders]
    C --> PA[Payments]
    C --> AD[Addresses]
    C --> RE[Reviews]
    C --> RT[Returns]
```

---

## Complete Marketplace Lifecycle

```mermaid
flowchart TD
    A[Seller Registers] --> B[Store Approved]
    B --> C[Product Listed]
    C --> D[Customer Purchases]
    D --> E[Payment Received]
    E --> F[Seller Fulfilment]
    F --> G[Shipment]
    G --> H[Delivery]
    H --> I[Review]
    I --> J[Return Optional]
    J --> K[Refund Optional]
    K --> L[Seller Payout]
    L --> M[Order Completed]
```

---

## Recommended Improvements for Production Use

- Use **order splitting** for multi-seller checkout
- Store **separate seller sub-orders** under one master order
- Add **commission rules** by seller or category
- Support **wallet holds** until delivery or return window expiry
- Keep **supplier mapping** at variant level, not just product level
- Track **audit logs** for approvals, refunds, withdrawals, and edits
- Add **notification templates** for every major event
- Design **status-driven workflows** for better operations control

---

## Suggested Order Statuses

```text
Pending Payment
Payment Confirmed
Processing
Partially Fulfilled
Shipped
Delivered
Return Requested
Return Approved
Refunded
Completed
Cancelled
```

---

## Suggested Seller Earnings Statuses

```text
Pending
On Hold
Available
Withdrawn
Rejected
Reversed
```

---

## Final Summary
This marketplace workflow supports a full multi-vendor commerce system with seller onboarding, product sourcing, order routing, fulfilment, shipping, returns, refunds, commissions, wallets, and dashboards. The structure is designed to scale across **seller-owned products**, **Amazon-based fulfilment**, and **AliExpress dropshipping** while keeping operations clear and trackable.

