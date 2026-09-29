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
- A catalog API available at `http://localhost:8080/items`

The API must return JSON in this shape:

```json
{
  "items": [
    {
      "id": 1,
      "image": "/images/product.jpg",
      "rating": { "stars": 4.5, "count": 120 },
      "company": "Example Brand",
      "item_name": "Product name",
      "current_price": 799,
      "original_price": 1299,
      "discount_percentage": 38
    }
  ]
}
```

Product image URLs must be reachable by the browser. The API/backend is not included in this project.

## Run locally

Open a terminal in the app directory and install dependencies:

```bash
cd Myntra-react-clone
npm install
```

Start the catalog API on port `8080`, then start the Vite development server:

```bash
npm run dev
```

Open the local URL printed by Vite. The app routes are `/` for the product listing and `/bag` for the shopping bag.

## Other commands

```bash
npm run build    # Create a production build in dist/
npm run preview  # Preview the production build
npm run lint     # Run ESLint
```

## Project structure

```text
Myntra-React-Clone/
└── Myntra-react-clone/       # Vite application root
		├── public/images/        # Static product and page images
		└── src/
				├── components/       # Header, product cards, bag, footer, loading UI
				├── routes/           # Home, bag, and shared app layout
				├── store/            # Redux Toolkit slices and store
				├── data/              # Local data module
				├── main.jsx           # React entry point and route setup
				└── index.css          # Global styles
```
