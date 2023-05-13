# Next.js v13.4.2 × Mantine v6 × Tailwind CSS v3.3.2

### Features

- Next.js v13.4.2 (/pages)
- Mantine v6
- Tailwind CSS v3.3.2
- TypeScript
- Prettier
- ESLint

### Usage

- Create Next.js Project

  ```bash
  npx create-next-app --ts
  ```

- Start local server

  ```bash
  npm run dev
  ```

  Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

- Prepare Mantine

  [reference](https://github.com/mantinedev/mantine-minimal-next-template/tree/master)

  ```bash
  npm install @mantine/core @mantine/hooks @mantine/next @emotion/server @emotion/react
  ```

  index.tsx

  ```typescript
  import { Button, Group } from "@mantine/core";

  export default function IndexPage() {
    return (
      <Group mt={50} position="center">
        <Button size="xl">Welcome to Mantine!</Button>
      </Group>
    );
  }
  ```

  \_app.tsx

  ```typescript
  import "../styles/globals.css";
  import type { AppProps } from "next/app";
  import Head from "next/head";
  import { MantineProvider } from "@mantine/core";

  export default function App(props: AppProps) {
    const { Component, pageProps } = props;

    return (
      <>
        <Head>
          <title>Page title</title>
          <link rel="shortcut icon" href="/favicon.svg" />
          <meta
            name="viewport"
            content="minimum-scale=1, initial-scale=1, width=device-width"
          />
        </Head>

        <MantineProvider
          withGlobalStyles
          withNormalizeCSS
          theme={{
            /** Put your mantine theme override here */
            colorScheme: "dark",
          }}
        >
          <Component {...pageProps} />
        </MantineProvider>
      </>
    );
  }
  ```

  \_document.tsx

  ```typescript
  import { createGetInitialProps } from "@mantine/next";
  import Document, { Head, Html, Main, NextScript } from "next/document";

  const getInitialProps = createGetInitialProps();

  export default class _Document extends Document {
    static getInitialProps = getInitialProps;

    render() {
      return (
        <Html>
          <Head />
          <body>
            <Main />
            <NextScript />
          </body>
        </Html>
      );
    }
  }
  ```

- Prepare Tailwind CSS

  [reference](https://tailwindcss.com/docs/guides/nextjs)

  1. Install Tailwind CSS

     ```bash
     npm install -D tailwindcss postcss autoprefixer
     npx tailwindcss init -p
     ```

  2. Configure your template paths

     tailwind.config.js

     ```javascript
     /** @type {import('tailwindcss').Config} */
     module.exports = {
       content: [
         "./app/**/*.{js,ts,jsx,tsx,mdx}",
         "./pages/**/*.{js,ts,jsx,tsx,mdx}",
         "./components/**/*.{js,ts,jsx,tsx,mdx}",

         // Or if using `src` directory:
         "./src/**/*.{js,ts,jsx,tsx,mdx}",
       ],
       theme: {
         extend: {},
       },
       plugins: [],
     };
     ```

  3. Add the Tailwind directives to your CSS

     globals.css

     ```css
     @tailwind base;
     @tailwind components;
     @tailwind utilities;
     ```

  4. Start your build process

     ```bash
     npm run dev
     ```

  5. Start using Tailwind in your project

     index.tsx

     ```typescript
     import { Button, Group } from "@mantine/core";

     export default function IndexPage() {
       return (
         <Group mt={50} position="center">
           <Button size="xl" className="text-red-400">
             Welcome to Mantine!
           </Button>
         </Group>
       );
     }
     ```

-
