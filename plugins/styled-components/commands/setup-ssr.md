---
description: Configure styled-components for server-side rendering (SSR) in Next.js, Remix, or custom setups
---

I'll help you configure styled-components for server-side rendering with proper style injection, hydration, and performance optimization.

## What This Configures

Complete SSR setup:
- Style sheet collection on server
- Style injection in HTML
- Client hydration
- Babel configuration
- Performance optimization
- Development mode enhancements
- Production optimizations

## Framework Support

### 1. Next.js App Router (13+)
Modern Next.js with app directory.

**What I'll generate:**
- SSR registry component
- Root layout configuration
- Babel configuration
- TypeScript setup
- Performance optimizations

### 2. Next.js Pages Router
Traditional Next.js with pages directory.

**What I'll generate:**
- Custom _document.tsx
- Custom _app.tsx
- Babel configuration
- Style collection logic
- Hydration setup

### 3. Remix
Remix framework SSR.

**What I'll generate:**
- Entry server configuration
- Root component setup
- Style extraction
- Streaming support

### 4. Custom React SSR
Express, Fastify, or custom server.

**What I'll generate:**
- Server rendering function
- HTML template
- Style sheet collection
- Client entry point
- Hydration logic

## Quick Setup

Just tell me:
"Set up SSR for [framework]"

**Examples:**
- "Set up SSR for Next.js 14 App Router"
- "Set up SSR for Next.js Pages Router"
- "Set up SSR for Remix"
- "Set up SSR for Express server"

## Custom Setup

Answer these questions:

### 1. Framework
- **Next.js App Router**: Next.js 13+ with app directory
- **Next.js Pages Router**: Traditional Next.js
- **Remix**: Remix framework
- **Custom**: Express/Fastify/Custom server

### 2. Features
Select all that apply:
- [ ] Style streaming
- [ ] Development mode enhancements
- [ ] Production minification
- [ ] Component display names
- [ ] SSR-specific styles
- [ ] Critical CSS extraction

### 3. Performance
- **Standard**: Basic SSR configuration
- **Optimized**: Performance optimizations enabled
- **Advanced**: Streaming, code splitting, critical CSS

## Next.js App Router Configuration

### Generated Files

**app/registry.tsx:**
```typescript
/**
 * Styled Components Registry
 * @description Handles SSR style injection for Next.js App Router
 * @see https://nextjs.org/docs/app/building-your-application/styling/css-in-js
 */
'use client';

import React, { useState } from 'react';
import { useServerInsertedHTML } from 'next/navigation';
import { ServerStyleSheet, StyleSheetManager } from 'styled-components';

/**
 * Props interface
 */
interface RegistryProps {
  children: React.ReactNode;
}

/**
 * Styled Components Registry Component
 * Collects styles during SSR and injects them into the HTML
 */
export default function StyledComponentsRegistry({
  children,
}: RegistryProps) {
  // Only create stylesheet once with lazy initial state
  const [styledComponentsStyleSheet] = useState(() => new ServerStyleSheet());

  /**
   * Insert styles into HTML during server rendering
   */
  useServerInsertedHTML(() => {
    const styles = styledComponentsStyleSheet.getStyleElement();
    styledComponentsStyleSheet.instance.clearTag();
    return <>{styles}</>;
  });

  // On client, just return children
  if (typeof window !== 'undefined') {
    return <>{children}</>;
  }

  // On server, wrap with StyleSheetManager
  return (
    <StyleSheetManager sheet={styledComponentsStyleSheet.instance}>
      {children}
    </StyleSheetManager>
  );
}
```

**app/layout.tsx:**
```typescript
/**
 * Root Layout
 * @description Root layout with styled-components SSR support
 */
import StyledComponentsRegistry from './registry';
import { ThemeProvider } from 'styled-components';
import { lightTheme } from '../styles/theme';
import GlobalStyles from '../styles/GlobalStyles';

/**
 * Metadata for the application
 */
export const metadata = {
  title: 'Your App',
  description: 'Your app description',
};

/**
 * Root layout component
 */
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>
        <StyledComponentsRegistry>
          <ThemeProvider theme={lightTheme}>
            <GlobalStyles />
            {children}
          </ThemeProvider>
        </StyledComponentsRegistry>
      </body>
    </html>
  );
}
```

**.babelrc:**
```json
{
  "presets": ["next/babel"],
  "plugins": [
    [
      "babel-plugin-styled-components",
      {
        "ssr": true,
        "displayName": true,
        "fileName": true,
        "minify": true,
        "transpileTemplateLiterals": true,
        "pure": true
      }
    ]
  ]
}
```

## Next.js Pages Router Configuration

### Generated Files

**pages/_document.tsx:**
```typescript
/**
 * Custom Document
 * @description Custom document with styled-components SSR
 */
import Document, {
  DocumentContext,
  DocumentInitialProps,
  Html,
  Head,
  Main,
  NextScript,
} from 'next/document';
import { ServerStyleSheet } from 'styled-components';

/**
 * Custom Document class
 * Handles styled-components SSR
 */
export default class MyDocument extends Document {
  /**
   * Get initial props with style collection
   */
  static async getInitialProps(
    ctx: DocumentContext
  ): Promise<DocumentInitialProps> {
    const sheet = new ServerStyleSheet();
    const originalRenderPage = ctx.renderPage;

    try {
      // Wrap rendering with style sheet collection
      ctx.renderPage = () =>
        originalRenderPage({
          enhanceApp: (App) => (props) =>
            sheet.collectStyles(<App {...props} />),
        });

      // Get initial props from parent Document
      const initialProps = await Document.getInitialProps(ctx);

      // Return props with collected styles
      return {
        ...initialProps,
        styles: (
          <>
            {initialProps.styles}
            {sheet.getStyleElement()}
          </>
        ),
      };
    } catch (error) {
      console.error('Error during styled-components SSR:', error);
      throw error;
    } finally {
      sheet.seal();
    }
  }

  /**
   * Render document
   */
  render() {
    return (
      <Html lang="en">
        <Head>
          {/* Additional head elements */}
        </Head>
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}
```

**pages/_app.tsx:**
```typescript
/**
 * Custom App
 * @description Custom app with theme provider
 */
import type { AppProps } from 'next/app';
import { ThemeProvider } from 'styled-components';
import { lightTheme } from '../styles/theme';
import GlobalStyles from '../styles/GlobalStyles';

/**
 * Custom App Component
 */
export default function App({ Component, pageProps }: AppProps) {
  return (
    <ThemeProvider theme={lightTheme}>
      <GlobalStyles />
      <Component {...pageProps} />
    </ThemeProvider>
  );
}
```

## Remix Configuration

### Generated Files

**app/entry.server.tsx:**
```typescript
/**
 * Entry Server
 * @description Server entry point with styled-components SSR
 */
import { PassThrough } from 'stream';
import { renderToPipeableStream } from 'react-dom/server';
import { RemixServer } from '@remix-run/react';
import { Response } from '@remix-run/node';
import type { EntryContext } from '@remix-run/node';
import { ServerStyleSheet } from 'styled-components';
import isbot from 'isbot';

const ABORT_DELAY = 5000;

/**
 * Handle browser request
 */
export default function handleRequest(
  request: Request,
  responseStatusCode: number,
  responseHeaders: Headers,
  remixContext: EntryContext
) {
  const sheet = new ServerStyleSheet();

  return isbot(request.headers.get('user-agent'))
    ? handleBotRequest(
        request,
        responseStatusCode,
        responseHeaders,
        remixContext,
        sheet
      )
    : handleBrowserRequest(
        request,
        responseStatusCode,
        responseHeaders,
        remixContext,
        sheet
      );
}

/**
 * Handle bot requests (non-streaming)
 */
function handleBotRequest(
  request: Request,
  responseStatusCode: number,
  responseHeaders: Headers,
  remixContext: EntryContext,
  sheet: ServerStyleSheet
) {
  return new Promise((resolve, reject) => {
    const { pipe, abort } = renderToPipeableStream(
      sheet.collectStyles(
        <RemixServer context={remixContext} url={request.url} />
      ),
      {
        onAllReady() {
          const body = new PassThrough();
          const styles = sheet.getStyleTags();

          responseHeaders.set('Content-Type', 'text/html');

          resolve(
            new Response(body, {
              headers: responseHeaders,
              status: responseStatusCode,
            })
          );

          // Inject styles into HTML
          body.write(`<!DOCTYPE html>${styles}`);
          pipe(body);
          sheet.seal();
        },
        onShellError(error: unknown) {
          reject(error);
          sheet.seal();
        },
        onError(error: unknown) {
          console.error(error);
          responseStatusCode = 500;
        },
      }
    );

    setTimeout(abort, ABORT_DELAY);
  });
}

/**
 * Handle browser requests (streaming)
 */
function handleBrowserRequest(
  request: Request,
  responseStatusCode: number,
  responseHeaders: Headers,
  remixContext: EntryContext,
  sheet: ServerStyleSheet
) {
  return new Promise((resolve, reject) => {
    const { pipe, abort } = renderToPipeableStream(
      sheet.collectStyles(
        <RemixServer context={remixContext} url={request.url} />
      ),
      {
        onShellReady() {
          const body = new PassThrough();
          const styles = sheet.getStyleTags();

          responseHeaders.set('Content-Type', 'text/html');

          resolve(
            new Response(body, {
              headers: responseHeaders,
              status: responseStatusCode,
            })
          );

          body.write(`<!DOCTYPE html>${styles}`);
          pipe(body);
          sheet.seal();
        },
        onShellError(error: unknown) {
          reject(error);
          sheet.seal();
        },
        onError(error: unknown) {
          console.error(error);
        },
      }
    );

    setTimeout(abort, ABORT_DELAY);
  });
}
```

**app/root.tsx:**
```typescript
/**
 * Root Component
 * @description Root component with theme provider
 */
import {
  Links,
  LiveReload,
  Meta,
  Outlet,
  Scripts,
  ScrollRestoration,
} from '@remix-run/react';
import { ThemeProvider } from 'styled-components';
import { lightTheme } from './styles/theme';
import GlobalStyles from './styles/GlobalStyles';

/**
 * Root component
 */
export default function App() {
  return (
    <html lang="en">
      <head>
        <meta charSet="utf-8" />
        <meta name="viewport" content="width=device-width,initial-scale=1" />
        <Meta />
        <Links />
      </head>
      <body>
        <ThemeProvider theme={lightTheme}>
          <GlobalStyles />
          <Outlet />
        </ThemeProvider>
        <ScrollRestoration />
        <Scripts />
        <LiveReload />
      </body>
    </html>
  );
}
```

## Custom Express Server Configuration

**server.tsx:**
```typescript
/**
 * Express Server with SSR
 * @description Custom Express server with styled-components SSR
 */
import express from 'express';
import React from 'react';
import { renderToString } from 'react-dom/server';
import { ServerStyleSheet, ThemeProvider } from 'styled-components';
import App from './App';
import { lightTheme } from './styles/theme';

const app = express();
const PORT = process.env.PORT || 3000;

/**
 * Serve static files
 */
app.use(express.static('dist'));

/**
 * SSR render function
 */
function renderApp(req: express.Request, res: express.Response) {
  const sheet = new ServerStyleSheet();

  try {
    // Render app with style collection
    const html = renderToString(
      sheet.collectStyles(
        <ThemeProvider theme={lightTheme}>
          <App />
        </ThemeProvider>
      )
    );

    // Get style tags
    const styleTags = sheet.getStyleTags();

    // Send complete HTML
    res.send(`
      <!DOCTYPE html>
      <html lang="en">
        <head>
          <meta charset="UTF-8" />
          <meta name="viewport" content="width=device-width, initial-scale=1.0" />
          <title>Your App</title>
          ${styleTags}
        </head>
        <body>
          <div id="root">${html}</div>
          <script src="/client.js"></script>
        </body>
      </html>
    `);
  } catch (error) {
    console.error('SSR Error:', error);
    res.status(500).send('Internal Server Error');
  } finally {
    sheet.seal();
  }
}

/**
 * Handle all routes
 */
app.get('*', renderApp);

/**
 * Start server
 */
app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

**client.tsx:**
```typescript
/**
 * Client Entry Point
 * @description Client-side hydration
 */
import React from 'react';
import { hydrateRoot } from 'react-dom/client';
import { ThemeProvider } from 'styled-components';
import App from './App';
import { lightTheme } from './styles/theme';

/**
 * Hydrate the app
 */
const root = document.getElementById('root');

if (root) {
  hydrateRoot(
    root,
    <ThemeProvider theme={lightTheme}>
      <App />
    </ThemeProvider>
  );
}
```

## Babel Configuration Options

```json
{
  "plugins": [
    [
      "babel-plugin-styled-components",
      {
        "ssr": true,
        "displayName": true,
        "fileName": true,
        "minify": true,
        "transpileTemplateLiterals": true,
        "pure": true,
        "namespace": "your-app"
      }
    ]
  ]
}
```

**Configuration Options:**
- **ssr**: Enable SSR mode (required)
- **displayName**: Add display names (helpful for debugging)
- **fileName**: Add file names to components
- **minify**: Minify styles in production
- **transpileTemplateLiterals**: Faster compilation
- **pure**: Mark components as pure for tree-shaking
- **namespace**: Prefix for component names

## Performance Optimizations

### Style Streaming
For frameworks that support streaming:
- Styles are sent incrementally
- Faster First Contentful Paint
- Better user experience

### Critical CSS
Extract critical styles for above-the-fold content:
```typescript
const criticalStyles = sheet.getStyleElement();
```

### Code Splitting
Split styles by route:
```typescript
// Load styles only for current route
const styles = await import('./styles/route.styles');
```

## Testing SSR

I'll provide verification steps:

### 1. Check HTML Source
View page source and verify:
- `<style>` tags are present in `<head>`
- Styles are inlined
- No Flash of Unstyled Content (FOUC)

### 2. Disable JavaScript
Disable JS in browser:
- Page should still be styled
- Layout should be correct
- Content should be readable

### 3. Performance Metrics
Check metrics:
- First Contentful Paint < 1.5s
- Time to Interactive < 3s
- No hydration errors in console

### 4. Hydration Test
Watch for hydration issues:
- No React hydration warnings
- No style duplication
- Smooth client-side transitions

## Common Issues & Solutions

### Issue: FOUC (Flash of Unstyled Content)
**Solution**: Ensure styles are in `<head>` before content

### Issue: Hydration Mismatch
**Solution**: Ensure server and client render same markup

### Issue: Missing Styles
**Solution**: Verify style collection in SSR logic

### Issue: Performance Issues
**Solution**: Enable minification and streaming

## What Happens Next

1. I'll detect your framework
2. Generate SSR configuration files
3. Set up Babel configuration
4. Add TypeScript types
5. Provide testing instructions
6. Include troubleshooting guide
7. Add performance tips

Let me know what framework you're using!
