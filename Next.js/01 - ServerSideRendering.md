Server-Side Rendering is a technique used to render web pages on the server before sending them to the client's browser. With SSR, the server generates the complete HTML markup of a page with dynamic data, which is then sent to the client for display.

## Benefits of Server-Side Rendering

Improved initial loading speed: SSR allows the server to send a fully rendered HTML page to the client, reducing the time required to display content.

Better SEO: Search engines can easily crawl and index the content of server-rendered pages.

Improved user experience: Users can see the content faster, even on slower connections.

## Next.js and Server-Side Rendering

Next.js is a popular React framework that provides built-in support for server-side rendering. It allows you to easily create SSR-enabled applications.

## Basic Next.js Setup

To get started with Next.js, you'll need Node.js installed on your machine. Follow these steps:

a. Create a new directory for your project.
b. Open a terminal in the project directory and run npm init -y to initialize a new npm project.
c. Install Next.js by running npm install next react react-dom.

## Creating a Server-Side Rendered Page

Next.js provides a special directory structure for creating pages. By default, any file in the pages directory is treated as a page.

a. Create a new file named index.js inside the pages directory.
b. Add the following code to index.js:

```javascript
function HomePage() {
  return <h1>Hello, Server-Side Rendering!</h1>;
}

export default HomePage;

```

c. Save the file.

Starting the Next.js Development Server:
To start the Next.js development server, run npm run dev in the terminal. Next.js will automatically compile your code and start the server.

Accessing the Server-Side Rendered Page:
Open your browser and navigate to http://localhost:3000. You should see the text "Hello, Server-Side Rendering!" rendered on the page.

Dynamic Data Fetching:
Next.js allows you to fetch data during server-side rendering by using the getServerSideProps function.

a. Modify index.js as follows:

```javascript
function HomePage({ data }) {
  return <h1>Hello, {data}!</h1>;
}

export async function getServerSideProps() {
  // Simulating data fetching
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();

  return {
    props: {
      data: data.message,
    },
  };
}

export default HomePage;

```

b. Save the file and refresh the page. The dynamic data fetched from the API will be rendered on the server and displayed.
