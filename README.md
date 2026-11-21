# Inventory and Data Management System

RESTful inventory backend built with Node.js, Express.js, MongoDB, Mongoose, and dotenv.

## Installation

```bash
cd "ASSIGNMENT_3"
npm install
```

## Environment setup

Create `.env` by copying `.env.example`:

```bash
cp .env.example .env
```

Set `MONGO_URI` to a valid MongoDB connection string. The default local example is:

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/inventory_db
```

MongoDB must be running locally, or the URI must point to MongoDB Atlas or another reachable MongoDB deployment.

## Run

```bash
npm start
# Development mode
npm run dev
```

The API is available at `http://localhost:5000/api/products`.

## API endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/products` | Create a product |
| GET | `/api/products` | List products with filtering, sorting, and pagination |
| GET | `/api/products/:id` | Get one product |
| PUT | `/api/products/:id` | Update one or more product fields |
| DELETE | `/api/products/:id` | Delete a product |
| PATCH | `/api/products/:id/stock` | Increase or decrease stock |
| GET | `/api/products/low-stock` | Get products at or below reorder level |
| GET | `/api/products/summary` | Get category inventory aggregation |

## Product JSON

```json
{
  "name": "Gel Pen Pack of 15",
  "sku": "STNY-PN-713",
  "category": "Stationery",
  "price": 120,
  "quantity": 48,
  "reorderLevel": 20,
  "supplier": "Cello Pens"
}
```

## Query examples

```text
GET /api/products?category=Electronics
GET /api/products?minPrice=100&maxPrice=1000
GET /api/products?search=pen
GET /api/products?sortBy=price&order=asc
GET /api/products?sortBy=quantity&order=desc
GET /api/products?page=1&limit=10
```

Stock example:

```json
{ "change": 10 }
```

Use a negative `change` to decrease stock.
