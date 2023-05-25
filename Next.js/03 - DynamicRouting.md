Dynamic routing allows you to create pages with dynamic routes that can handle variable data. Instead of creating individual files for each page, you can use a single template page and handle the routing based on dynamic parameters.

# Benefits of Dynamic Routing

## Code efficiency

Dynamic routing allows you to handle similar pages with different parameters using a single template page, reducing code duplication.

## Flexible URLs

Dynamic routes enable you to create more user-friendly and SEO-friendly URLs by incorporating dynamic parameters.

## Simplified data fetching

Dynamic routing can be combined with data fetching methods to retrieve and display dynamic content based on the route parameters.

## Dynamic Routing in Next.js

Next.js provides a straightforward way to implement dynamic routing using the file system-based routing approach.

## Basic Next.js Setup

Before diving into dynamic routing, make sure you have set up Next.js as described in the earlier crash course section.

## Creating a Dynamic Route

To create a dynamic route in Next.js, you need to use the file system-based routing and specify the dynamic parameter using brackets ([]) in the file name.

a. Create a new file named [id].js inside the pages directory.
b. Add the following code to [id].js:

```javascript
function DynamicPage({ id }) {
  return <h1>Dynamic Page - {id}</h1>;
}

export async function getServerSideProps({ params }) {
  const { id } = params;

  // Simulating data fetching based on the ID
  const res = await fetch(`https://api.example.com/data/${id}`);
  const data = await res.json();

  return {
    props: {
      id,
      data: data.message,
    },
  };
}

export default DynamicPage;

```

c. Save the file.

## Accessing the Dynamic Route

To access the dynamic route, you can use the corresponding URL pattern with the dynamic parameter.

For example, if the dynamic parameter is 123, you can access the page by navigating to http://localhost:3000/123. The text "Dynamic Page - 123" will be rendered on the page.

## Dynamic Parameter Extraction

In the example above, the id parameter is extracted from the params object in the getServerSideProps function. It is then used to fetch dynamic data based on the ID.

## Data Fetching with Dynamic Routing

You can combine dynamic routing with data fetching methods, such as getServerSideProps or getStaticProps, to fetch and display dynamic content.

In the example above, the getServerSideProps function is used to fetch data based on the dynamic ID. You can modify it to use getStaticProps for static site generation if desired.

That's a crash course on dynamic routing in Next.js! Next.js provides additional features for more complex dynamic routing scenarios, including nested dynamic routes and optional parameters. You can explore these topics further in the Next.js documentation.