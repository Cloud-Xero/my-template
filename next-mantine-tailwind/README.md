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

-
-
-
