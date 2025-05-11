# What is Next.js?

Next.js is a React framework for building full-stack web applications with a file-based routing mechanism.

## React
- It's not feasible to create a fully-featured application ready for production using just React.
- React is a library for building user interfaces.
- You need to make decisions about other features such as routing, data fetching, and more.

## Next.js
- Next.js uses React for building user interfaces.
- It provides additional features that enable you to build production-ready applications.
- These features include routing, optimized rendering, data fetching, bundling, compiling, and more.
- You don't need to install additional packages as Next.js provides everything you need.

## Why Learn Next.js?
Next.js simplifies the process of building production-ready web applications:
1. Routing
2. API Routes
3. Rendering
4. Data Fetching
5. Styling
6. Optimization
7. Dev and Prod Build System

## Prerequisites
- HTML
- CSS
- Modern JavaScript
- React Fundamentals

## To Create a Next.js App:

```bash
PS F:\Nextjs> npx create-next-app@latest
Need to install the following packages:
create-next-app@15.3.2
Ok to proceed? (y) y

√ What is your project named? ... hello-world
√ Would you like to use TypeScript? ... No / Yes    yes  
√ Would you like to use ESLint? ... No / Yes    yes
√ Would you like to use Tailwind CSS? ... No / Yes    yes
√ Would you like your code inside a `src/` directory? ... No / Yes   yes
√ Would you like to use App Router? (recommended) ... No / Yes    yes
√ Would you like to use Turbopack for `next dev`? ... No / Yes
√ Would you like to customize the import alias (`@/*` by default)? ... No / Yes
```

## React Server Components (RSC)

React Server Components is a new architecture introduced by the React team and quickly adopted by Next.js.

This architecture introduces a new approach to creating React components by dividing them into two distinct types:

- Server Components
- Client Components

### Server Components
- By default, Next.js treats all components as Server components.
- These components can perform server-side tasks like reading files or fetching data directly from a database.
- The trade-off is that they can't use React hooks or handle user interactions.

### Client Components
- To create a Client component, you need to add the `'use client'` directive at the top of your component file.
- While Client components can't perform server-side tasks like reading files, they can use hooks and handle user interactions.
- Client components are the traditional React components you're familiar with from previous versions of React.

## React Server Components and Routing
In routing, you'll see practical examples of both types of components:

- Work with server components that wait for certain operations to complete before rendering content.
- Use client components to take advantage of hooks from the routing module.

## Routing in Next.js
Next.js has a file-system-based routing system. URLs you can access in your browser are determined by how you organize your files and folders in your code.

### Routing Conventions
- All routes must live inside the `app` folder.
- Route files must be named either `page.js` or `page.tsx`.
- Each folder represents a segment of the URL path.

When these conventions are followed, the file automatically becomes available as a route.

## File-Based Routing

**Scenario 1:**

- `localhost:3000` → Home Page

**Scenario 2:**

- `localhost:3000/about` → About Page
- `localhost:3000/profile` → Profile Page

## Dynamic Routing Scenarios in Next.js App Router

### Scenario 3 - Blog Pages

| URL                          | Description      |
| ---------------------------- | ---------------- |
| `localhost:3000/blog`        | Blog Page        |
| `localhost:3000/blog/first`  | First Blog Page  |
| `localhost:3000/blog/second` | Second Blog Page |

**Folder Structure:**

```
/app
  /blog
    /[slug]
      page.tsx  (Handles dynamic blog posts)
    page.tsx     (Handles /blog route)
```

**Example for \[slug]/page.tsx:**

```tsx
export default function BlogPost({ params }: { params: { slug: string } }) {
  return <h1>Blog Post: {params.slug}</h1>;
}
```

---

### Scenario 4 - Product Listing & Dynamic Details

| URL                           | Description               |
| ----------------------------- | ------------------------- |
| `localhost:3000/products`     | Product List              |
| `localhost:3000/products/1`   | Product 1 Details         |
| `localhost:3000/products/:id` | Product Details (dynamic) |

**Folder Structure:**

```
/app
  /products
    /[productId]
      page.tsx  (Handles dynamic product details)
    page.tsx     (Handles product listing)
```

**Correct version of \[productId]/page.tsx:**

```tsx
export default function ProductDetails({ params }: { params: { productId: string } }) {
  return <h1>Details about product {params.productId}</h1>;
}
```

---

### Scenario 5 - Product Reviews

| URL                                   | Description            |
| ------------------------------------- | ---------------------- |
| `localhost:3000/products/1`           | Product 1 Details      |
| `localhost:3000/products/1/reviews/1` | Review 1 for Product 1 |

**Folder Structure:**

```
/app
  /products
    /[productId]
      /reviews
        /[reviewId]
          page.tsx  (Handles review details)
      page.tsx       (Handles product details)
    page.tsx          (Handles product listing)
```

**\[reviewId]/page.tsx:**

```tsx
export default function ProductReview({ params }: { params: { productId: string; reviewId: string } }) {
  return <h1>Review {params.reviewId} for Product {params.productId}</h1>;
}
```
