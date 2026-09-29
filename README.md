# Myntra React Clone

A Myntra-inspired fashion shopping interface built with React. It includes a product listing and shopping bag with a live price summary. This is a front-end learning project; it does not provide checkout or payment processing.

## Features

- Browse product cards with images, ratings, prices, and discounts
- Add products to or remove products from the shopping bag
- View bag contents and a price breakdown, including a convenience fee
- Navigate between the home page and bag page
- Manage application state with Redux Toolkit

The catalog is loaded from a separate API. The bag is held in Redux state and is not persisted after a page reload. The place-order button is presentational only.

## Tech stack

- React 19 and Vite
- React Router
- Redux Toolkit and React Redux
- Bootstrap 5 and React Icons

## Requirements

- Node.js and npm

The included Express backend listens on port `8080`. `GET /items` returns the catalog in this shape:

```json
{
  "items": [
    {
      "id": "001",
      "image": "images/1.jpg",
      "company": "Example Brand",
      "item_name": "Product name",
      "current_price": 799,
      "original_price": 1299,
      "discount_percentage": 38,
      "return_period": 14,
      "delivery_date": "10 Oct 2026",
      "rating": { "stars": 4.5, "count": 120 }
    }
  ]
}
```

The backend also provides `GET /items/:id` and `POST /items`. New items submitted to the POST endpoint are assigned an ID and saved to `actual-backend/items.json`. Image paths are read by the frontend, so the referenced images must be available under the frontend's public assets.

## Run locally

Install and start the backend in one terminal:

```bash
cd actual-backend
npm install
npm start
```

In a second terminal, install and start the React app:

```bash
cd Myntra-react-clone
npm install
npm run dev
```

Open the local URL printed by Vite. Keep the backend running while using the app. The routes are `/` for the product listing and `/bag` for the shopping bag.

## Other commands

```bash
npm run build    # Create a production build in dist/
npm run preview  # Preview the production build
npm run lint     # Run ESLint
```

## Project structure

```text
Myntra-React-Clone/
├── actual-backend/            # Express API and JSON file storage
│   ├── app.js                  # API routes and port 8080 server
│   ├── items.json              # Persistent product catalog
│   └── data/items.js           # Catalog read/write helpers
└── Myntra-react-clone/       # Vite application root
		├── public/images/        # Static product and page images
		└── src/
  ├── components/        # Header, product cards, bag, footer, loading UI
  ├── routes/            # Home, bag, and shared app layout
  ├── store/             # Redux Toolkit slices and store
  ├── data/              # Local data module
  ├── main.jsx           # React entry point and route setup
  └── index.css          # Global styles
```
