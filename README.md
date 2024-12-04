# Next.js Starter App

**_App Template: BigCommerce Product Management Dashboard_**

If you are building an app for BigCommerce using Catalyst or BigDesign, you can use this app template serves as a starting point.

## Purpose
This app allows merchants to manage their product catalog efficiently. It integrates BigCommerce's API and leverages BigDesign for UI components and Catalyst for seamless API connectivity.

## Features

Product Listing: Display a paginated list of products.
Product Search: Search for products by name or SKU.
Inventory Management: Edit product stock levels directly in the app.
Theme Customization: Use BigDesign to provide a consistent BigCommerce-style UI.
Catalyst Integration: Authenticate and communicate with the BigCommerce API.

## Technologies

Frontend: React.js (with BigDesign components)
Backend: Node.js with Express (using Catalyst for BigCommerce API integration)
Authentication: OAuth2 flow with BigCommerce
Styling: BigDesign's design system

## Template Structure

Here's how the directory structure of the app template might look:

```java
bigcommerce-product-dashboard/
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── ProductList.js
│   │   │   ├── ProductCard.js
│   │   │   └── SearchBar.js
│   │   ├── pages/
│   │   │   ├── HomePage.js
│   │   │   └── ProductPage.js
│   │   ├── App.js
│   │   ├── index.js
│   │   └── styles.css
│   ├── public/
│   │   └── index.html
│   └── package.json
├── server/
│   ├── routes/
│   │   ├── productRoutes.js
│   │   └── authRoutes.js
│   ├── utils/
│   │   ├── bigcommerceClient.js
│   │   └── helpers.js
│   ├── server.js
│   └── package.json
└── README.md
```

## Steps to Scaffold

1. Frontend Setup with BigDesign

- Install BigDesign components:

```bash
npm install @bigcommerce/big-design
```

- Use BigDesign components for UI:
  
```js
import { Box, Button, H1 } from '@bigcommerce/big-design';

const HomePage = () => (
  <Box margin="medium">
    <H1>Product Management Dashboard</H1>
    <Button>Add Product</Button>
  </Box>
);
```

2. Backend Setup with Catalyst

- Install Catalyst SDK
  
```bash
npm install @bigcommerce/catalyst
```

- Create a BigCommerce API client using Catalyst

```js
const { createClient } = require('@bigcommerce/catalyst');

const client = createClient({
  clientId: process.env.CLIENT_ID,
  accessToken: process.env.ACCESS_TOKEN,
  storeHash: process.env.STORE_HASH,
});

app.get('/api/products', async (req, res) => {
  const products = await client.catalog.products.list();
  res.json(products);
});
```

3. Authentication: Follow BigCommerce's OAuth2 flow to authenticate users.

4. Deployment: Host the app on a platform like Heroku or AWS and configure it in your BigCommerce control panel.


## How to Use the Template

1. Clone the repository

```bash
git clone https://github.com/your-repo/bigcommerce-product-dashboard.git
```

2. Install dependencies

```bash
cd bigcommerce-product-dashboard/client && npm install
cd ../server && npm install
```

3. Run the app

```bash
npm start
```
