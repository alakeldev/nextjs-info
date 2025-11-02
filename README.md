# 📚 Next.js Comprehensive Guide

<div align="center">

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

**A comprehensive learning guide for mastering Next.js development**

[📖 Getting Started](#-evolution-of-web-development) • [🛣️ Routing](#-nextjs-routing) • [🖥️ Server Components](#-server-components) • [📊 Data Fetching](#-data-fetching-with-nextjs) • [⚡ Optimization](#-optimizing-with-nextjs) • [🚀 Deployment](#-nextjs-deployment-with-vercel)

</div>

---

## 📑 Table of Contents

<details>
<summary>🔽 Click to expand full table of contents</summary>

### 📚 **Core Concepts**
- [🌐 Evolution of Web Development](#-evolution-of-web-development)
- [🎨 Next.js Rendering](#-nextjs-rendering)
- [🔄 Rendering Process Steps](#-rendering-process-steps)
- [📊 Server Rendering Strategies](#-server-rendering-strategies)
- [⚡ Adding Interactivity With Hydration](#-adding-interactivity-with-hydration)
- [🗺️ The App Router](#-the-app-router)
- [🎨 Styling in Next.js](#-styling-in-nextjs)

### 🛣️ **Routing**
- [📄 Reserved Files](#-reserved-files)
- [🔀 Dynamic Routes](#-dynamic-routes)
- [🔄 The template.tsx Reserved File](#-the-templatetsx-reserved-file)
- [🔗 Navigation](#-navigation)
- [🔢 Managing Unpredictable URLs](#-managing-unpredictable-urls)
- [📁 Reserved File Names and Component Hierarchy](#-reserved-file-names-and-component-hierarchy)

### 🖥️ **Server Components**
- [⚙️ Server Rendering Strategies](#-server-rendering-strategies)
- [🖥️ Server Components](#-server-components)
- [🔄 Using Client Components with Server Components](#-using-client-components-with-server-components)
- [⏳ Fallback Components with React Suspense](#-fallback-components-with-react-suspense)
- [🎯 Client vs Server Components](#-client-vs-server-components)

### 📊 **Data Fetching**
- [🖥️ Data Fetching on the Client](#-data-fetching-on-the-client)
- [🖥️ Data Fetching on the Server](#-data-fetching-on-the-server)
- [⚡ Parallel vs Sequential Data Fetching](#-parallel-vs-sequential-data-fetching)
- [🚀 Preloading Data](#-preloading-data)
- [🔄 Revalidating Data](#-revalidating-data)
- [🔄 Loading UI](#-loading-ui)
- [🌊 Streaming](#-streaming)
- [📝 Server-Only Forms](#-server-only-forms)

### ⚡ **Optimization**
- [🖼️ Images and Priority](#-images-and-priority)
- [📐 Image Sizes](#-image-sizes)
- [🔤 Fonts](#-fonts)
- [📜 Scripts](#-scripts)
- [⚙️ Config-Based Metadata](#-config-based-metadata)
- [📁 File-Based Metadata](#-file-based-metadata)

### 🚀 **Deployment**
- [Next.js Deployment with Vercel](#-nextjs-deployment-with-vercel)
- [Next.js Deployment with Cloudflare](#-nextjs-deployment-with-cloudflare)

</details>

---

## 🌐 Evolution of Web Development

> **Timeline:** Static Web → Dynamic Interaction → Server-Generated Content → Single Page Applications → React → Next.js

### 🏛️ Static Web Era
- HTML Pages that display the same content to every visitor, no user interaction beyond hyperlinks

### ⚡ Dynamic Interaction Era
- XMLHttpRequests, Enabled users to interact with web page without reloading the whole page

### 🔄 Server-Generated Content Era
- The server generates custom content for users based on their requests and interactions

### 📱 Single Page Applications Era
- Dynamic Client-side interactions, fluid app-like experience, Web applications load a single html page and dynamically render content

### ⚛️ React Era
- Component-based approach, reusable components that are small, isolated, manageable also interactive user experience, Real-time updates without reloading the page

### 🚀 Next.js Era
- Server-side rendering for faster load time, Client-side rendering for interactivity or SEO

---

## 📋 Next.js Sections

- **Core Concepts**
- **Routing**
- **Server Components**
- **Data Fetching**
- **Optimization**
- **Deployment**

---

## 🎨 Next.js Rendering

### What is Rendering?
Rendering is the process of converting code into viewable user interfaces. In Next.js, different rendering strategies can be adopted depending on the application's requirements.

### 🔀 Rendering Environments

Next.js supports two primary rendering environments: **server-side** and **client-side** rendering.

#### 🖥️ Server-Side Rendering (SSR)
- The server infrastructure is used to render the webpage content
- A viewable, non-interactive webpage is sent to the client
- In Next.js, components are server-side rendered by default using server components
- No additional configuration is necessary

#### 💻 Client-Side Rendering (CSR)
- The server sends the client all the necessary files for a webpage
- The client uses the instructions to render the components on the browser and enable interactivity
- In Next.js, a component can be marked for client-side rendering with the `'use client'` directive

---

## 🔄 Rendering Process Steps

### Client-Side Rendering Flow

| Step | Action |
|------|--------|
| **1** | The user's browser sends a request to the website's server when the user visits a website |
| **2** | The server receives the request |
| **3** | The Server composes a response with the interactions for the browser to render the components |
| **4** | The Server sends the response to the user's browser |
| **5** | The user's browser receives the response from the server |
| **6** | The browser processes the received response and prepares to render the page |
| **7** | The browser follows the instructions in the response to build and render the page to the user |
| **8** | The user's browser displays the fully rendered page to the user |

### Server-Side Rendering Flow

| Step | Action |
|------|--------|
| **1** | The user's browser sends a request to the website's server when the user visits a website |
| **2** | The server receives the request |
| **3** | The Server fetches the required data and files |
| **4** | The Server renders the webpage |
| **5** | The server has finished rendering the webpage to HTML and composes a response |
| **6** | The Server sends the response to the user's browser |
| **7** | The user's browser receives the response from the server |
| **8** | The user's browser displays the fully rendered page to the user |

---

## 📊 Server Rendering Strategies

Next.js offers three distinct approaches: **static rendering**, **dynamic rendering**, and **streaming**.

### 1️⃣ Static Rendering
- Pre-generates pages at build time
- Results are cached and efficiently distributed via a Content Delivery Network (CDN)
- Ideal for content that remains unchanged over time
- Significantly reduces server load and enhances delivery speed

### 2️⃣ Dynamic Rendering
- Generates content in real-time for each request
- Caters to personalized or time-sensitive content needs
- More resource-intensive compared to static rendering
- Bypasses the cache to dynamically generate data for each user

### 3️⃣ Streaming
- Divides a route's UI into chunks that are progressively streamed to the client
- Significantly improves perceived load times
- Users can interact with parts of the page as they become available
- Beneficial for pages where data fetching might introduce delays

---

## 💡 Code Examples

### Example: Client-Side Rendering
Create Client Side Component that reacts to a toggle value (switch between Day mode, night mode):

```jsx
'use client'
import {useState} from 'react';
import BackgroundManager from '../components/BackgroundManager';

export default function ThemeSwitch() {
	const [light, setLight] = useState<boolean>(true);
	
	const toggleTheme = () => {
		setLight(!light);
	};
	
	return (
		<>
			<BackgroundManager light={light} />
			<button onClick={toggleTheme}>
				Switch to {light ? 'Night' : 'Day'} Mode
			</button>
		</>
	);
}
```

### Example: Server-Side Rendering
Define a new component with the name TimePage:

```jsx
const fetchCurrentTime = (): string => {
	return new Date().toLocaleString();
};

export default function TimePage() {
	const currentTime = fetchCurrentTime();

	return (
		<p>
			The Current Time Is: {currentTime}
		</p>
	)
}
```

---

## ⚡ Adding Interactivity With Hydration

Previously, we discussed server-side rendering and noted that while our web app is visible, it is not interactive. Let's get deeper into hydration and refine our mental model of how Next.js operates.

If the process of SSR is the first layer of paint, the second layer is hydration. After the server-sent HTML is loaded on the client's browser, the JavaScript bundle accompanying the HTML starts executing. This JavaScript includes the React code, which then "hydrates" the static HTML. Hydration involves attaching event handlers and linking the React components to their HTML counterparts. During this process, React also performs reconciliation, comparing the result from rendering components on the client side with the result from rendering on the server, ensuring they are in sync.

Once hydration is complete, the webpage becomes fully interactive. The interactive elements like buttons and forms can now respond to user inputs. From this point onwards, any updates to the page, such as user interactions or data fetching, lead to a re-render of the affected components. This re-rendering is handled entirely on the client side, and the components are updated to reflect new states or props. Consider it a touch-up of the paint layers!

With hydration, we can see that rendering with Next.js is not confined to one side alone. A Next.js application typically represents a blend of different rendering techniques, leveraging server- and client-side strengths to deliver an optimal user experience.

### 🔄 Hydration Process Steps

| Step | Description |
|------|-------------|
| **1** | A client device receives a fully rendered HTML page, it also receives a bundle of javascript files and any extra data needed to make the page is sent |
| **2** | The Fully rendered HTML page can be represented as a DOM tree |
| **3** | Once the client's device receives the HTML page and the bundle, React constructs a virtual DOM |
| **4** | The virtual DOM is Constructed |
| **5** | React uses the virtual DOM to figure out where event handlers and other interactivity need to be attached |
| **6** | React compares the virtual DOM with the Actual DOM to make sure they are consistent |
| **7** | The two trees go through reconciliation if there are any differences |
| **8** | React identifies where the corresponding elements are in the actual DOM |
| **9** | The Apps start listening to events from the elements |
| **10** | The HTML page is now fully interactive and any buttons on the screen can be clicked! |

### 💡 Key Concept
> **Hydration** executes the bundled JavaScript client-side, attaching event handlers and linking the React components to their HTML counterparts.

---

## 🗺️ The App Router

The App Router is a file-system based router where the structure of your `/app` directory determines the routes and URL paths available for your entire application. We'll explore routing more deeply in the upcoming lesson. For now, we'll explore the `/app` directory and how it generates basic routes.

In the App Router, each folder name determines a route that exists. To make the route accessible, a `page.tsx` file must live in the directory.

For example, the root `/app` folder can be treated as a home page and adding a `page.tsx` makes it accessible; the page will map to the `/` URL path. The UI of the home page, or any pages in a route, is contained in the `page.tsx` file.

---

## 🎨 Styling in Next.js

Next.js provides multiple approaches to styling your applications, each with its own benefits and use cases.

### 📦 CSS Modules
CSS Modules provide a great way to prevent style name collision by modularizing CSS files.

**Key Features:**
- Files will be processed as a CSS Module if appended with the `.module.css` extension
- Location-wise, CSS Module files can be colocated with the component they are styling
- Automatic class name scoping prevents conflicts

```css
/* styles/Button.module.css */
.primary {
  background-color: #0070f3;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
}

.secondary {
  background-color: transparent;
  color: #0070f3;
  border: 1px solid #0070f3;
}
```

```tsx
// components/Button.tsx
import styles from './Button.module.css'

export default function Button({ variant, children }) {
  return (
    <button className={styles[variant]}>
      {children}
    </button>
  )
}
```

### 🌍 Global CSS
Global CSS can apply styles to the entire application.

**Best Practices:**
- The global CSS file can be imported into any page or layout
- Typically, the global CSS file is imported into the root layout
- Use for reset styles, typography, and application-wide themes

```css
/* app/globals.css */
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html,
body {
  max-width: 100vw;
  overflow-x: hidden;
}

body {
  color: rgb(var(--foreground-rgb));
  background: linear-gradient(
      to bottom,
      transparent,
      rgb(var(--background-end-rgb))
    )
    rgb(var(--background-start-rgb));
}
```

### 🎭 Additional Styling Options

| **Method** | **Use Case** | **Benefits** |
|------------|--------------|--------------|
| **Tailwind CSS** | Utility-first styling | Rapid development, small bundle size |
| **Styled Components** | CSS-in-JS | Dynamic styling, component-scoped |
| **Sass/SCSS** | Enhanced CSS | Variables, mixins, nesting |
| **Emotion** | CSS-in-JS | Performance-focused, flexible |

> **💡 Pro Tip:** Choose the styling method that best fits your team's workflow and project requirements. Next.js supports all popular styling solutions out of the box!

---

## 📝 Next.js Summary

- Next.js is a React framework that allows high-performing, scalable, and search-engine-friendly web apps
- Rendering is the process of converting code into viewable user interfaces
- Next.js supports client-side rendering and server-side rendering. It allows developers to create hybrid applications where parts of the application can be on the server and parts can be on the client
- Client-side rendering sends the client instructions to be rendered in the browser
- Server-side rendering renders web pages on the server and sends them to the client's browser
- Hydration makes pages interactive by attaching JavaScript to the relevant components
- The App Router uses the file system to provide routing for a Next.js application
- `create-next-app` can be used to bootstrap a Next.js application quickly
- Next.js supports styling with global CSS, CSS Modules, CSS-in-JS, Tailwind CSS, and Sass

---

# 🛣️ Next.js Routing

## 📄 Reserved Files

### `page.tsx`
`page.tsx` is one of the many reserved files in Next.js. Recall that creating a folder does not automatically create a path that users can visit. We must add a `page.tsx` file to the folder and default export a React component to inform the App Router that the folder (path segment) is accessible.

### `layout.tsx`
Besides `page.tsx`, Next.js uses a `layout.tsx` named file to define a shared UI across any nested path segments. To define the UI, we default export a React component that accepts a prop called `children` of type `ReactNode` like so:

```jsx
import { ReactNode } from "react";

// React component in layout.tsx 
function MyLayout({ children } : { children: ReactNode }) {  // destructured props 
  return (
    <div>  
      <p>Nested UI's will always see me above them!</p>
      <section>
        {children}
      </section>
    </div>
  )
}

// Note: default export is required
export default MyLayout;
```

Due to `layout.tsx` being a shared UI, Next.js requires every application to have at least 1 `layout.tsx` in the topmost segment known as the root layout. This root layout must contain the `<html>` and `<body>` elements. An important aspect of `layout.tsx` is that they maintain their state across any nested segment navigation and do not re-render.

### Folder Structure Example

To create a nested segment, we create a new folder (segment) inside another folder (segment). For example, let's look at the following folder structure:

```
├── app
│   ├── settings
│   │   ├── page.tsx
│   │   ├── billing
│   │   │   ├── page.tsx 
│   ├── info
│   │   ├── MyComponent.tsx
│   ├── layout.tsx
```

The above folder structure:

- Contains the required, shared root layout
- Contains two nested folders within `/app`, `/settings`, and `/info`
- Contains an accessible, nested path (`/settings/billing`) by nesting the `/settings` and `/billing` segments
- Contains an accessible path (`/settings`) by using the `/settings` segment
- Contains an in-accessible path `/info` because its folder does not contain a `page.tsx` file

---

## 🔀 Dynamic Routes

Dynamic segments are dynamic portions of a URL that may change (like `/users/10` and `/users/20`).

### To define a dynamic segment in Next.js:
1. Create an accessible segment (folder) as we've learned in the previous exercise
2. The folder name for a dynamic segment must be wrapped in square brackets `[]`
3. The folder name given will serve as the identifier we use to retrieve the dynamic segment in our `page.tsx`

### Example Folder Structure

```
├── app
│   ├── users
│   │   ├── [userId]
│   │   │   ├── page.tsx 
```

### Accessing Dynamic Segment Data

We access the dynamic segment data by referencing the folder name as a property of the `params` prop in the `page.tsx` component:

```jsx
// destructure params which contain our identifier as a property
export default function MyUserPage( { params } : { params: { userId: string }}) {
  return (
    <h1>Greetings user: {params.userId}</h1>
  )
}
```

In this example:

- We destructure a `params` prop
- We define the `params` type as an object containing the property `userId`
- `params` properties are always of type `string` (or `string[]` — we'll see this later in the lesson)
- We access the dynamic segment data by using the `params` object and accessing the `userId` property

---

## 🔄 The `template.tsx` Reserved File

As we work with dynamic segments, we may find that we'd like to store some analytics about the number of users that have navigated to the page. This sounds like a great place to use a shared UI in a `layout.tsx` file, but, because layouts don't rerender on nested segment navigation, we won't be able to rerun our API call.

To address this issue, we can use the `template.tsx` reserved file. `template.tsx` is similar to `layout.tsx` in that:

- `template.tsx` also defines a sharable UI for its nested segments
- It must default export a React component
- The default exported component receives a `children` prop

But differs in that it gets re-instantiated on nested segment navigation (we'll learn more about navigation next). We can take advantage of this feature by calling an API to update our user's visited counter like:

```jsx
// import statements

// re-instantiated on nested segment navigation
export default function MyTemplate({children}: {children : ReactNode}) {
  useEffect(() => {
    updateUsersCounter()  // API call
  }, [])  // runs on mount
  // other logic for MyTemplate
}
```

---

## 🔗 Navigation

### Using The `<Link>` Component

When exploring web applications, we often use links to navigate.

Next.js provides a few ways to give us Single Page Application (SPA) like browser navigation. Remember that SPA navigation refers to the idea of changing the browser path without needing to make a new request to the server. In this exercise, we will be exploring the `<Link>` component.

#### Example Usage

```jsx
const selectedUser = "25"  // user selected user id
<section>
  <Link href="/users">Users</Link>
  <Link href={`/users/${selectedUser}`}>User: {selectedUser}</Link>  {/* dynamic path*/}
  <Link href="/settings" replace>My Settings</Link> {/* replaces current path in browser history*/}
  <Link href="/info">Info</Link>
</section>
```

Where:

- The `href` prop determines the path we want to navigate to
- The `href` prop can be used to link to a dynamic segment by creating the dynamic path (in the above example, we use a template literal)
- The text content ("Users", "My Settings", "Info") is the text displayed in the UI
- The `replace` prop is used to replace the current URL path with the `href` path

The `<Link>` component is an extension to the `<a>` element that adds prefetching functionality. With prefetching, Next.js will prefetch route segments automatically so when a user navigates to those segments, the browser does not need to reload.

#### Active Link Styling

`<Link>` components can be used in conjunction with the `usePathname()` hook from the `next/navigation` package to apply some "active" styles to the `<Link>`:

```jsx
'use client'
import Link from 'next/link'
import { usePathname } from "next/navigation";

const pathname = usePathname()  // current path: /users
<section>
  <Link href="/users" className={pathname === "/users" ? styles.active : ""}>Users</Link> {/* currently active*/}
  <Link href="/info" className={pathname === "/info" ? styles.active : ""}>Info</Link> {/* not active */}
</section>
```

**Note:** `usePathname()` can only be used within client components so we use the `'use client'` directive.

---

### The `useRouter()` Hook

Next.js provides the `useRouter()` hook, a part of the `next/navigation` package, which we can use to programmatically perform SPA-like navigation in client components. Calling `useRouter()` returns a router object containing the following methods:

- `push(path)`: Navigates to path by pushing path to the top of the browser history stack
- `back()`: Navigates back one entry in the browser history stack
- `forward()`: Navigates forward one entry in the browser history stack
- `replace(path)`: Navigate to path by replacing the top of the browser history stack with path

#### Example Usage

```jsx
'use client'  // required client directive
// other imports
import { useRouter } from "next/navigation";  // import

export default function Authentication() {
  const router = useRouter();  // get router object

  useEffect(() => {
    if(!isAuthenticated()) {
      router.replace("/sign-up")  // redirect user by replacing current path and sending user to /sign-up
    }
  }, [])
  return (
      // use router.back() as callback.  
      <button onClick={router.back}>Return</button>
  ) 
}
```

#### Simple Example

```jsx
export default function Page() {
  const router = useRouter()

  function goBack() {
    router.back()
  }

  function goToDashboard() {
    router.push("/dashboard")
  }

  return (
    <>
      <button onClick={goBack}>Back</button>
      <button onClick={goToDashboard}>Dashboard</button>
    </>
  )
}
```

> **To recap:** if we need to navigate using our application structure (like static links), we use the `<Link>` component, but if we need programmatic navigation (like redirecting), we use the `useRouter()` hook.

---

## 🔢 Managing Unpredictable URLs

We've discussed how we can create dynamic segments and nested segments, but what if our application supports any number of the same dynamic segments? For example, if our application has a feature to compare usage details for its users, the URL paths may look like:

- `/users/123`: Show usage details for users with ID 123
- `/users/123/987`: Show comparison of usage details for users with ID's 123 and 987

How should we handle this? Should we use multiple dynamic segments like `/users/[userId1]/[userId2]/...`? Not quite. This approach will have the same scaling issue we solved by using dynamic segments. Instead, Next.js provides a **catch-all segments** solution.

### Catch-All Segments

Catch-all segments, as the name suggests, will match all paths like `/users/123`, and `/users/123/987` using a single dynamic segment. To create one, we define our dynamic segment as we've done before (using a folder and `[]`) but also add an ellipses (`...`) prefix to the dynamic segment name like:

```
├── app
│   ├── users
│   │   ├── [...userIds]  // catch-all dynamic segment
│   │   │   ├── page.tsx 
```

#### Accessing Catch-All Data

```jsx
// destructure params which contain our identifier as property
export default function MyUserPage( { params } : { params: { userIds: string[] }}) {
const userIds = params.userIds   // access params property with our dynamic segment data.
  return (
    <section>
      {/* display data for all userIds*/}
      {userIds.map((userId) => (
        <UsageDetails key={userId} userId={userId}/>
      ))}
    </section>
  )
}
```

This example will retrieve all userIds from the catch-all dynamic segment `[...userIds]` from a params property named `userIds` of type `string[]`.

### Optional Catch-All Segments

Before we wrap up dynamic segments, let's add a new feature where a user will be able to select the users to compare if they navigate to the base `/users` URL segment. Navigating to that path now will yield a 404 error.

One way we can fix this is by taking advantage of Next.js **optional catch-all segments**. Optional catch-all segments, as the name suggests, are optional and will match paths like: `/users`, `/users/123`, and `/users/123/987`. To create one, we wrap another pair of square brackets `[]` around our catch-all segment folder like `[[...userIds]]`.

#### Accessing Optional Catch-All Data

```jsx
// Destructure params which contain our identifier as property
export default function MyUserPage( { params } : { params: { userIds?: string[] }}) {
  // Using optional chaining
  // In path /users, `userIds` will not exist in the object
  const userIds = params?.userIds

  // ...body
}
```

---

## 📁 Reserved File Names and Component Hierarchy

Notice that each reserved file we've seen so far has a single purpose with special functionality, for example:

- `page.tsx`: Makes a URL segment accessible and displays a unique UI
- `layout.tsx`: Creates a shared UI and wraps any nested UIs, maintains state on nested segment navigation
- `template.tsx`: Creates a shared UI and wraps any nested UIs, re-instantiates on nested segment navigation

### Additional Reserved Files

These are only some of the reserved files Next.js provides. Let's explore three more of the commonly used ones:

- `error.tsx`: Creates an ErrorBoundary component using the defined UI for the current segment and its nested segments
- `not-found.tsx`: Creates an ErrorBoundary component using the defined UI for 404 errors for the current segment and its nested segments
- `loading.tsx`: Creates a Suspense component for the current segment and its nested segments

### Examples

```jsx
/* in error.tsx */

'use client' // Must be client components
//receives error object and reset function as props
export default function MyErrorBoundary( { error, reset }: { error: Error; reset: () => void} ) {
  // body
}

/* in not-found.tsx */
export default function MyNotFoundUI() {
  return (
    <>
      <h1>Sorry, I don't recognize this page!</h1>
      {/* rest of components */}
    </>
  )
}

/* in loading.tsx */
export default function Loading() {
  return <h1>Loading content...</h1>
}
```

In the example, the `not-found.tsx` and `loading.tsx` exported components do not receive props. `error.tsx` receives an Error object named `error` and a reset callback named `reset()`. Note that `error.tsx` components must be client components and they do not catch errors thrown in `layout.tsx` or `template.tsx`.

### Component Hierarchy

The component hierarchy establishes how all the default exported components in the route segment's reserved files are rendered.

```
├── app
│   ├── layout.tsx
│   ├── template.tsx
│   ├── loading.tsx
│   ├── settings
│   │   ├── layout.tsx
│   │   ├── template.tsx
│   │   ├── loading.tsx
│   │   ├── error.tsx
│   │   ├── not-found.tsx
```

For an app with the above folder structure:

```jsx
<Layout>
  <Template>
    <Suspense>
      <Layout>
        <Template>
          <ErrorBoundary>
            <Suspense>
              <ErrorBoundary>
                <Page/>
              </ErrorBoundary>
            </Suspense>
          </ErrorBoundary>
        </Template>
      </Layout>
    </Suspense>
  </Template>
</Layout>
```

In this hierarchy:

- `<Layout>` is the root of a segment
- `<Template>` wraps all but `<Layout>`
- `<ErrorBoundary>` wraps `<Suspense>`, the not-found `<ErrorBoundary>`, and `<Page>`
- `<Suspense>` wraps not-found `<ErrorBoundary/>` and `<Page>`
- not-found `<ErrorBoundary/>` wraps `<Page>`
- Nested segments hierarchy follows the same hierarchy rules and is wrapped entirely within the parent hierarchy

Understanding the component hierarchy will help us master Next.js routing and understand where certain reserved files are needed.

---

## 📚 Routing Section Review

Great job learning about routing in Next.js. In this lesson, you've learned about:

- The Next.js file-system App Router and how it creates a tree data structure
- The roles of folders and reserved files in building URL segments
- The shared UI reserved file `layout.tsx` and how it preserves state on nested segment navigation
- The shared UI reserved file `template.tsx` and how it gets re-instantiated on nested segment navigation
- Creating nested URL segments by nesting folders
- Creating dynamic URL segments and how to use the `params` prop to retrieve the data
- Using `<Link>` components for declarative navigation
- Using the `useRouter()` hook for programmatic navigation
- Creating catch-all and optional catch-all dynamic routes
- `error.tsx`, `loading.tsx`, and `not-found.tsx` reserved files and their specific use cases
- The Next.js component hierarchy and how it determines how things are rendered in the UI

In this lesson, we covered the core routing concepts in Next.js. There are many more features you can learn about that build off of the concepts you've learned in this lesson.

---

# ⚙️ Server Rendering Strategies

Following Next.js' philosophy of streamlining web development, it offers three server rendering strategies to suit different needs: **static**, **dynamic**, and **streaming**, each with tailored caching and content delivery approaches.

## 1️⃣ Static Rendering
Static rendering pre-generates pages at build time, allowing the results to be cached and efficiently distributed via a Content Delivery Network (CDN). This method is ideal for content that remains unchanged over time, significantly reducing server load and enhancing delivery speed by serving cached, pre-rendered content to all users.

## 2️⃣ Dynamic Rendering
Dynamic rendering, on the other hand, generates content in real-time for each request, catering to personalized or time-sensitive content needs. This approach ensures the freshness of content but is more resource-intensive compared to static rendering, as it bypasses the cache to dynamically generate data for each user, potentially slowing down the response time.

Both static and dynamic methods are influenced by the performance of data fetching operations, where delays in fetching can impact the overall speed of page rendering.

## 3️⃣ Streaming
Streaming divides a route's UI into chunks that are progressively streamed to the client. This method significantly improves perceived load times, as users can interact with parts of the page as they become available rather than waiting for the entire page to load. Streaming is especially beneficial for pages where data fetching might introduce delays, as it allows for the immediate display of available content not blocked by fetching.

Next.js intelligently selects the optimal rendering strategy for each route, but developers have the flexibility to adjust caching settings, revalidation times, and decide whether to utilize UI streaming.

It is essential to consider, though, that most web pages do not fall neatly into purely static or purely dynamic categories. By leveraging Next.js' caching mechanisms and rendering strategies, you can fine-tune the balance between serving static content and dynamically generated responses.

### Summary:
- **Static Rendering:** A developer builds a webpage and caches it onto a CDN. When a user requests a webpage, the CDN delivers a cached webpage to the user
- **Dynamic rendering:** Generates content in real-time for each request, catering to personalized or time-sensitive content needs
- **Streaming rendering:** Divides a route's UI into chunks that are progressively streamed to the client

---

# 🖥️ Server Components

## Implementing Server Components

Here's an example of what a Server Component looks like:

```jsx
// UserProfile.tsx
import React from 'react';

export default function UserProfile({ userId }: { userId: string }) {
  const userData = fetchUserData(userId);
    return (
      <div>
        <h1>Viewing {userData.firstName}</h1>
        <p>Name: {userData.fullName}</p>
        <p>Contact: {userData.email}</p>
      </div>
    );
}
```

This example demonstrates a Server Component fetching and displaying user data. Unlike typical React components, Server Components are tailored for server-side operations like this — rendering content based on server-side logic without involving client-side interactivity.

### Server Components differ from traditional React components in several key ways:

- They execute on the server, utilizing server resources for tasks like rendering content
- They don't contribute to the client-side JavaScript bundle, lightening the load on the client
- They're capable of fetching data on the server and sending just the necessary output to the client

### 💡 Practical Tip
A practical tip when working with Server Components is to consider where the `console.log()` outputs appear. Logs from Server Components will appear in the server's terminal, not the browser console. This distinction is a helpful reminder of the server-client divide, indicating where your code is executing.

### Where do logs from Client Components appear?
Logs from Client Components may be in both the server terminal and the browser console, as they are pre-rendered on the server by default to generate the initial HTML.

---

## 🔄 Using Client Components with Server Components

We've utilized the `'use client'` directive in previous lessons to define components requiring user interactions. This directive is crucial for delineating the execution environment of components.

Consider a scenario in a Next.js application where both static and dynamic content coexist in the same view. We need to ensure that each part is delegated to the appropriate execution environment: the server handling static content, like user profiles, and the client managing interactive content, like widgets, where appropriate. Putting a Client Component within a Server Component is straightforward; an import with direct usage is a valid pattern.

### Client Component in Server Component

```jsx
//ServerComponent.tsx
import ClientComponent from './ClientComponent';
export default function ServerComponent() {
  return (
    <div>
      <h1>My Server Component</h1>
      <ClientComponent />
    </div>
  );
}
```

### Server Component in Client Component

Components can be nested in both directions. Server Components can also be nested within Client Components. This pattern is tricker — to pass a Server Component into a Client Component, we must pass it in as a prop. One common way of doing this is through the `children` prop.

The following example demonstrates using a Server Component in a Client Component:

```jsx
//ClientComponent.tsx
'use client'
 
import { useState } from 'react';

export default function ClientComponent({ children }: { children: React.ReactNode }) {
  const [state, toggleState] = useState(true);
  return <div> {children} </div>
}

//Page.tsx
import ClientComponent from './ClientComponent.tsx'
import ServerComponent from './ServerComponent.tsx'

export default function Page() {
  return (
    <ClientComponent>
      <ServerComponent />
    </ClientComponent>
  )
}
```

In this example, `ServerComponents` is passed into `ClientComponents` as a child. When a request comes in, the server processes all Server Components first, including any inside Client Components. The server then sends back a payload containing instructions for arranging these components on the client side. React on the client side uses this payload to combine the Server and Client Components into a coherent structure that the user can interact with.

This approach allows us to use a hybrid rendering approach.

### Important Composition Pattern

When we choose to handle components in this way, it is essential to consider the composition pattern. As Server Components render before Client Components, you cannot embed a Server Component within a Client Component without causing an unnecessary server request.

Without passing it as a prop, the Server Component would adopt its parent's rendering environment and be rendered client-side. Instead, if we pass the Server Component through a prop to a Client Component — or, specifically, through the `children` prop as demonstrated in the example — they could be decoupled and rendered independently, preventing server-intended code from sneaking into the client.

Using the composition patterns of Server Components and Client Components, you'll update the web app with a category filter such that users can filter and only see the emails by the selected category.

---

## ⏳ Fallback Components with React Suspense

Continuing with effectively implementing Server Components, we will look at React Suspense and Fallback Components to ensure users encounter a responsive and engaging UI, even as the server performs the heavy lifting of fetching or rendering components.

Since Server Components are executed on the server, users may experience brief waits while they wait for the server to render and deliver the components. This pause may result in temporary blank screens or unresponsive UIs. Instead, we can use Fallback Components within React Suspense as interim placeholders that signal activity through loaders, skeleton screens, or custom placeholders during loading.

### What is React Suspense?

React Suspense is a built-in React feature that lets you "suspend" component rendering while waiting for some asynchronous operation, such as data fetching or code splitting. It works by catching promises thrown by components waiting for asynchronous data, and it manages the rendering of fallback content until the data is ready.

It introduces a **Suspense Boundary**, a powerful pattern for structuring your application's UI to handle loading states gracefully. This boundary not only signals ongoing server-side activity through a visual placeholder but also ensures that, upon completion of the action, the actual content is smoothly transitioned into view, defining the scope within which React should display fallback content.

We've seen this before with the `loading.tsx` reserved file, which serves as a loading indicator but wraps the whole page. Instead, we can manually create Suspense Boundaries, giving us full control over which components require a loading state and manage that logic ourselves.

Next.js enhances this mechanism with its streaming capabilities, allowing components within a Suspense Boundary to be streamed to the client as they are rendered on the server. This streaming process, coupled with Suspense, means that users can start interacting with parts of the page that are ready while others are still being prepared server-side.

### Example

Here's an example of how this would look in Next.js:

```jsx
import { Suspense } from 'react'
import UtilityBill from './UtilityBill.tsx'

const FallbackComponent = () => <p>Loading bill details...</p>

export default function BillingPage() {
  return (
    <main>
      <h1>Your Utility Bill</h1>
      <Suspense fallback={<FallbackComponent />}>
        <UtilityBill billType="electric" userId="codey24" />
      </Suspense>
    </main>
  );
}
```

Let's break it down:

- A `<FallbackComponent>` component with a loading indicator is defined
- A `<Suspense>` wraps the `<UtilityBill>` component
- The `<FallbackComponent>` is specified as a fallback UI while `<UtilityBill>` loads

### Considerations When Placing Suspense Boundaries

When placing your Suspense Boundaries, consider the following questions:

- Considering the user's experience, what specific aspects of page streaming would you focus on?
- Regarding content prioritization, which parts of the page would you deem most crucial to load first?
- Given that some components require data fetching, how would you structure the dependencies between components and data sources?

To practice our understanding of Fallback Components and Suspense Boundaries, we'll take a look at the email web application once again with the goal of implementing a Suspense Boundary and using Fallback Components.

In the following checkpoints, the email web app has received a few updates. The `fetchEmailData()` function in `utils.tsx` is now asynchronous and simulates network latency with a delay. The `<EmailFilter>` component has been updated to become asynchronous to properly handle the Promise returned by `fetchEmailData()`.

---

## 🎯 Client vs Server Components

### Server Components

Server Components are the backbone of Next.js's efficiency; use Server Components when:

- **Fetching data:** the component is inherently "closer" to the data source and can access the data with less latency that may exist in a client-side data fetch operation
- **Accessing backend resources:** the component can interact with backend resources securely without exposing the operations to the client
- **Securing sensitive information:** the component can keep data like access tokens and API keys on the server
- **Optimizing performance:** by managing large dependencies on the server, the component reduces the size of the client-side JavaScript bundle

### Client Components

Client Components are responsible for the interactivity of your application; use Client Components when:

- **Adding interactivity:** They make your app responsive to user inputs and interactions
- **Managing state and effects:** Allow applications to have state and side effects with React Hooks
- **Using browser APIs:** Client Components allow us to use browser-specific features like geolocation or localStorage
- **Adding custom hooks:** Apply React custom hooks to manage stateful logic

---

## 📚 Server Components Section Review

- Server Components, referred to as React Server Components (RSCs), are the default component type in Next.js that render on the server
- The rendering of Server Components involves server-client coordination for task distribution and DOM updating
- There are three rendering strategies for Server Components. These strategies provide efficient content distribution, real-time content generation, and improved load times
- The static rendering strategy is ideal for static content as it pre-generates pages for efficient CDN distribution
- The dynamic rendering strategy is best for personalized or time-sensitive content as it generates real-time per request, though it may slow response times
- The streaming strategy works by progressively delivering UI chunks, allowing users to interact with parts of the page as they load
- A Server Component can be implemented by creating a React component and letting Next.js manage server-side rendering
- Server Components function server-side, reducing client-side load by avoiding contributions to the JavaScript bundle and optimizing application performance by fetching data server-side
- React Suspense and Fallback Components allow developers to create custom Suspense Boundaries, offering informative feedback to users during a loading delay
- Next.js applications can use Client Components and Server Components together in a composition pattern, creating a hybrid rendering approach
- Server Components should not be directly imported into Client Component modules but passed through a prop for independent rendering
- Server Components and Client Components each have their roles: Server Components handle data and backend interactions efficiently, while Client Components boost interactivity and manage state

---


# 📊 Data Fetching with Next.js

In a Next.js app, we can fetch data on the server as well as the client. There will be circumstances when fetching data on the client is inevitable, but ideally, data should be fetched on the server. Since the server has direct access to the databases, the client-server waterfalls can be reduced by fetching data on the server. Additionally, when server components are used, data can be fetched and rendered in the same environment.

Fetching data on the server also means that we can avoid exposing sensitive data to the client. However, this can also create a false sense of security. Server components may render on the client if they are used in a client component template. Although this flexibility is by design, it can lead to the exposure of sensitive data if, for example, API credentials used when data fetching in a server component are included in the client bundle. To prevent these critical scenarios, we’ll take a look at how to use the 'server-only' package to ensure that certain server-specific code
modules are never imported into client components.



## 🖥️ Data Fetching on the Client

We can use Route Handlers to define our custom request handlers, which run on the server to fetch data and deliver responses back to the client.

To define Route Handlers, we create a route.ts file inside the /app directory. Note that Route Handlers are only available inside the /app directory, and a route.ts file also cannot exist on the same level as the page.tsx file. So, we’ll need to create a directory inside our /app directory to host our Route Handlers. It’s common practice to name this directory api.

In `route.ts` located in our `app/api` directory, we can define our request handlers for any of the HTTP methods supported by Next.js, such as **GET**, **POST**, **PUT**, **PATCH**, **DELETE**, **HEAD**, and **OPTIONS**.

We can define our GET request handler using the fetch handler using the following structure:

```typescript
// app/api/route.ts
export async function GET() {
  const response = await fetch('https://api.com/some/route');
  
  if (!response.ok) {
    throw new Error('Failed to fetch data.');
  }
  
  const result = await response.json();
  return Response.json(result);
}
```


By default, Next.js will automatically cache the fetched data. To disable cache, we’ll need to pass cache: 'no-store' in the options object:

```typescript
const response = await fetch('https://api.com/some/route', {
  cache: 'no-store',
});
```

### 🗂️ **Nested API Routes**

We can also build nested routes by creating a folder inside the `/api` directory and defining Route Handlers for the route inside a separate `route.ts` file. 

For example, if we wanted to define an API to get users, we can create a folder called `user` inside the `/app/api` folder and create a separate `route.ts` file inside `/app/api/user`:

```
├── app
│   ├── api
│   │   ├── route.ts          // Main API route
│   │   ├── user
│   │   │   ├── route.ts      // User-specific API route
│   │   ├── posts
│   │   │   ├── route.ts      // Posts-specific API route
```

**Example User API Route:**

```typescript
// app/api/user/route.ts
export async function GET() {
  const users = await fetchUsers();
  return Response.json(users);
}

export async function POST(request: Request) {
  const userData = await request.json();
  const newUser = await createUser(userData);
  return Response.json(newUser, { status: 201 });
}
```





## 🖥️ Data Fetching on the Server 


We can also fetch data directly in our server component. For example, we can add the fetch call inside our <Home> component like the following:



```tsx
// app/page.tsx
export default async function Home() {
  const response = await fetch('https://api.com/some/route', { 
    cache: 'no-store' 
  });
  
  if (!response.ok) {
    throw new Error('Failed to fetch data.');
  }
  
  const result = await response.json();
  
  // other logic for the component
  return (
    <div>
      {/* Render your component with the fetched data */}
      <h1>Data: {JSON.stringify(result)}</h1>
    </div>
  );
}
```


Remember that fetching data in a server component can lead to exposure of sensitive data, such as API keys. In order to prevent this, we can fetch data in a separate file using the 'server-only' package. For example, we can create a folder in the root directory called utils and create a folder called getData.ts. Inside the file, we’ll import the 'server-only' package to prevent this file from being included in the client bundle.


```typescript
// utils/getData.ts
import 'server-only';

export default async function getData() {
  const response = await fetch('https://api.com/some/route', {
    cache: 'no-store'
  });

  if (!response.ok) {
    throw new Error('Failed to fetch data.');
  }

  return response.json();
}
```


We can then import the `getData()` function from `utils/getData` in any server component:

```tsx
// app/page.tsx
import getData from '../utils/getData';

export default async function Home() {
  const data = await getData();
  
  return (
    <div>
      <h1>Secure Data Fetching</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}
```




## ⚡ Parallel vs Sequential Data Fetching

There are two data fetching patterns when working with React components: parallel and sequential.

* When using a parallel data fetching pattern, requests in a route happen at the same time. We’ve already seen an example of a parallel data fetching pattern where our <Activity> component and <FriendActivity> component fetched data simultaneously when our / route is loaded.


* When using the sequential data fetching pattern, requests create waterfalls as they happen one after the other. We might choose to sequentially load data when a data fetch needs to depend on the result of another fetch.




## 🚀 Preloading Data

We can further optimize parallel data fetching by preloading data.

We can create a function, typically named preload(), to eagerly fetch and cache data before it needs to be rendered. When fetching data on the server, we can define the preload function inside the file that uses the 'server-only' directive. Then, we can use React’s cache function to cache fetched data.

```typescript
// utils/getPosts.tsx
import { cache } from 'react'
import 'server-only'

export const preload = () => {
  void getPosts();
}

export const getPosts = cache(async () => {
  const response = await fetch('https://api.com/some/route');
  
  if (!response.ok) {
    throw new Error('Failed to fetch posts');
  }
  
  return response.json();
})
```

In the above code example, the `getPosts()` function is called inside the `preload()` function with the `void` operator that evaluates the `getPosts()` function and returns `undefined`, meaning that the data is fetched and cached for later use.

We can call the `preload()` function before the `getPosts()` call is triggered in a component:

```tsx
// pages/Home.tsx
import { preload } from '../utils/getPosts'
import Posts from '../components/Posts/Posts'

export default function Home() {
  preload();
  
  return (
    <div>
      <Posts />
    </div>
  );
}


Here, given that getPosts() function is called inside the <Posts> component, the preload() function will trigger the fetch and have the data cached before it needs to be used within the <Posts> component.




## 🔄 Revalidating Data


Remember that Next.js will cache data by default. To control how existing data is purged and the latest data is re-fetched, we can revalidate our data.

We can revalidate our cached data in two ways: time-based revalidation and on-demand revalidation.

Using time-based revalidation, we can specify how often our data should be revalidated. With on-demand revalidation, we group data within a path or a tag that should be updated simultaneously when a particular event is triggered.

To use time-based revalidation, we add the next.revalidate option to specify the lifetime of our data in seconds to our fetch call:

const response = await fetch('https://api.com/some/route', {
  next: { revalidate: 60 }
});


In the example code above, the next.revalidate option has the value of 60 seconds, meaning that the data will be revalidated every minute.

We can use on-demand validation by cache tags or by path. To use tags, we’ll need to add next.tags option in our fetch call:

```typescript
const response = await fetch('https://api.com/some/route', {
  next: { tags: ['posts'] }
});
```


To use on-demand revalidation, we’ll create a Server Action, an asynchronous function executed on the server. To create a server action, we used the 'use server' directive. Then, we can import the revalidateTag() function from 'next/cache' to use inside a server action.

```typescript
'use server'

import { revalidateTag } from 'next/cache'

export async function updatePost(){
  revalidateTag('posts')
}
```


In the example above, the updatePost() server action calls the revalidateTag() function on cached data with the posts tag.

Similarly, we can also validate by path using the revalidatePath() function from 'next/cache'.

```typescript
'use server'

import { revalidatePath } from 'next/cache'

export async function updatePost(){
  revalidatePath('/posts')
}
```


In the example above, the updatePost() server action calls the revalidatePath() function on the /posts route.

This server action can be used on form submission in client and server components:

```typescript
import { updatePost } from './actions';

export default async function EditPost(){
  // logic for the component
  
  return(
    // return other elements
    <form action={updatePost}>
      <button type="submit">Update</button>
    </form>
  )
}
```


In the above code, we provide the updatePost() server action as the value of the form’s action attribute.




## 🔄 Loading UI

Fetching large amounts of data can take time. This is where loading UIs will be helpful, as an instant loading state can be rendered in place of a segment while data loads. Loading UIs provide visual feedback to the users that the data is currently being fetched. A loading UI can be a spinner, a skeleton, a progress indicator, or a loading message. 


Recall that to create an instant loading state, we create a file named loading.tsx in the folder containing the component that will use the loading UI. Inside, define the <Loading> component that contains the loading UI.

```tsx
export default function Loading(){
  return (
      <p>Loading data...</p>
  )
}
```


In the above code example, we have our <Loading> component display “Loading data…” as our loading message.

We can then use the <Loading> component as the fallback of a <Suspense> boundary, which we’ll look more closely at in the next exercise.




## 🌊 Streaming

Compared to how server-side rendering can be sequential and blocking, using streaming techniques allows a web app to progressively render and incrementally stream parts of the UI to the client. 

Streaming can be achieved with the <Suspense> component:

```tsx
return (
  <main>
    <Suspense>
      <UserProfile />
    </Suspense>
    <Suspense>
      <UserPosts />
    </Suspense>
  </main>
)
```

In the code example above, each of the <UserProfile> and <UserPosts> components are wrapped inside <Suspense> blocks. This will allow <UserProfile> and <UserPosts> to be loaded independently from each other and rendered on the client as soon as each component is ready.

We can provide a loading UI as the fallback of each <Suspense> boundary. The loading UI will be rendered in place of the component inside the <Suspense> until all actions inside the component complete and it is ready to be rendered.

```tsx
<Suspense fallback={<Loading />} >
   <UserPosts />
</Suspense>
```


Here, until our <UserPosts> component is ready to be rendered, the loading UI defined in the <Loading> component will be displayed in place.





## 📝 Server-Only Forms

We’ve looked at how to fetch and use data in our Next.js apps. Now, let’s take a look at how we can get, validate, and process user data.

To do this, we’ll create a server-only form by creating a server component and Server Actions.

First, we’ll create a server component:

```tsx
// components/FeedbackForm/FeedbackForm.tsx
export default function FeedbackForm(){
  return(
    <form>
      <label>
          Name:
        <input type="text" name="name" required />
      </label>
      <label>
          Email:
        <input type="email" name="email" />
      </label>
      <label>
          Feedback:
        <textarea name="feedback" required />
      </label>
      <button type="submit">Submit</button>
    </form>
  )
}
```


In the above code, we have a form that has three fields:

    A required name input field of text type.
    An email input field of email type.
    A required feedback text area.

Here, we use HTML form validation by setting the appropriate type for each field and using the required validation where necessary.

To handle the form, we’ll create a Server Action. Remember that we can create a Server Action using the 'use server' directive.

```typescript
// components/FeedbackForm/actions.ts
'use server'

export async function handleFeedback( formData: FormData ){
  const rawFormData = {
    name: formData.get('name') as string || '',
    email: formData.get('email') as string || '',
    feedback: formData.get('feedback') as string || '',
  }
  
  // do more with form data
}
```


In the above code, we create a file called actions.ts in the same folder where our <FeedbackForm> component is located. The handleFeedback() function will accept and process the form data.

Now that we’ve defined the Server Action, we can import and call it as the action attribute of <form>.

```tsx
// components/FeedbackForm/FeedbackForm.tsx
import { handleFeedback } from './action'

export default function FeedbackForm(){
  return(
    <form action={handleFeedback}>
      {/* more form fields */}
    </form>
  )
}
```


Here, we’ve imported the handleFeedback() function from actions.ts and passed the function as the value of the action attribute of the <form> element.

Once we’re done processing the form data in our handleFeedback() server action, we can redirect users to a new route using the redirect() function from 'next/navigation'.

```typescript
// components/FeedbackForm/actions.ts
'use server'

import { redirect } from 'next/navigation'

export async function handleFeedback( formData: FormData ){
  // process form data
  
  redirect('/feedback/thankyou');
}
```

In our example code above, after the form data has been processed, we call the redirect() function to redirect users to the /feedback/thankyou route.



### Review for Data Fetching section:

In this lesson, we learned how to fetch data both on the server and the client. Let’s review:

    Data should ideally be fetched on the server as the server has direct access to the database, client-server waterfalls can be reduced, data can be fetched and rendered in the same environment, and security is increased as sensitive data can remain unexposed to the client.
    Route Handlers are used to define custom request handlers for fetching data on the client.
    fetch() can directly be called within a server component.
    The 'server-only' package is used to prevent a server component from being sent to the client.
    By default, Next.js will automatically cache the fetched data. To disable cache, 'cache: 'no-store' is passed in the options object of a fetch call.
    When using the sequential data fetching pattern, requests create waterfalls as they happen one after the other.
    When using a parallel data fetching pattern, requests in a route happen at the same time.
    Parallel data fetching patterns can be optimized by preloading data.
    Cached data can be revalidated in two ways: time-based revalidation and on-demand revalidation.
    Time-based revalidation revalidates data after a specified duration of time in seconds.
    A Server Action is an asynchronous function executed on the server. To create a server action, use the 'use server' directive.
    On-demand revalidation revalidates data based on a path or a tag when a particular event is triggered.
    Loading UIs are rendered in place of a segment while data loads.
    Streaming using <Suspense> boundaries allows a web app to progressively render and incrementally stream parts of the UI to the client.
    Server-only forms can be created in a server component and using Server Actions.


### Optimizing with Next.js

Next.js offers essential optimization features for enhancing website performance and user experiences. As a web developer, leveraging these features is key to creating responsive and efficient applications.

The following are considerations to think about when optimizing web pages:

    Improve Core Web Vitals: Core Web Vitals, introduced by Google, are three key metrics measuring webpage speed, interactivity, and visual stability. High scores enhance user experience and SEO.
        Largest Contentful Paint (LCP): Measures the time from when a user navigates to a page until its largest content item is displayed. Ideal pages load their largest content in under 2.5 seconds. The goal is to reduce load times.
        First Input Delay (FID): Measures the time taken to respond to a user interaction, such as clicking a link or calling a JavaScript function. The ideal webpage will respond to user interactions in under 100ms. The aim is to enhance user interactivity.
        Cumulative Layout Shift (CLS): Measures the largest burst of layout shift scores for every unexpected layout shift during a page’s lifecycle. A layout shift occurs when a visible element changes position. Ideal webpages will have a CLS score under 0.1. The objective of CLS is to improve visual stability.
    Layout Shift: Proactively manage media to ensure elements are loaded properly, stay in place, and provide a stable shift-free user experience.
    Search Engine Optimization (SEO): Improve search engine rankings of web pages with properly optimized metadata.
    Scalability and Cost Reduction: Optimizing resources, reducing unnecessary overhead, and improving various development strategies.
    Mobile Optimization: Ensure that user experiences are consistent across all devices and view sizes.
    Developer Maintenance and Efficient Development: Cleaner code, better architecture, and smoother workflows.

With those considerations in mind for the following exercises, we’ll use Next.js’ built-in optimization tools to optimize:

    image loading and resizing
    font loading and creation
    script importing and usage
    metadata creation






## 🖼️ Images and Priority

Optimizing webpages can reduce LCP, significantly improving user experience. A broad list of common culprits include <img>, <Image>, <video>, <url>, url() calls, any text blocks, and animated images.

    Remember, LCP (Largest Contentful Paint) is the time from when a user navigates to a page until its largest content item is displayed.

LCP is calculated using each element’s visible size. The only exceptions are images. If an image is resized larger, it will report its original size. If resized smaller, it reports the smaller size.

An element is only considered the LCP after rendering. The LCP can change as new elements render. If a removed element was the LCP, it will still be the LCP unless a larger element is rendered.

Similar to LCP is the First Contentful Paint (FCP). FCP measures the time between page load and the first element appearing. Ideal webpages will load their FCP element within 1 second.

Although FCP indicates initial load times, web developers focus on LCP due to impact. The FCP element could be an empty <img> tag. Conversely, LCP is going to focus on the largest impact item.

Next.js optimizes images using their <Image> component, which extends the HTML <img> element with features for automatic optimization. These optimization features include:

    Size Optimization: Correctly sized images reduce unexpected layout shifts.
    Faster Page Loads: Images are only loaded when displayed on the webpage.
    Image Flexibility: Can resize any image as needed.

In this exercise, we’ll focus on improving image and page load times. In the next exercise, we’ll focus on optimizing image sizing.

Let’s properly and efficiently display an image using the <Image> component. Here’s how we would display a local image:

```tsx
import Image from 'next/image';

function localImage() {
  return (
    <div>
      <h1>Local Image</h1>
      <Image
        src="Local Image.png"
        alt="Local Image"
      />
    </div>
  );
};

export default localImage;
```


Remote images require specified width and height attributes and an updated src property with the online URL.

```tsx
<Image
  src="Online Location.png"
  alt="Local Image"
  width={500}
  height={500}
/>
```


If we know that an image is the LCP, we can assign it the priority property. Next.js will prioritize this <Image> and preload it, reducing the overall load time.

```tsx
<Image
  ...
  priority={true}
/>
```





## 📐 Image Sizes

Images can be further optimized by sizing them appropriately to prevent layout shifts and maintain aspect ratio. Sizing images occurs in three methods: automatically, explicitly, and implicitly.

    Automatic sizing is letting the webpage handle the Image size without setting a width or height. Automatic sizing is only applicable to local images because Next.js is unable to deduce image dimensions for remote images. Next.js uses static imports to automatically size local images.

```tsx
import Image from 'next/image'
import localImage from '../public/localImage.png'
 
export default function Page() {
  return (
    <Image
      src={localImage}
      alt="Image located within project folder"
      {/* width={500} automatically provided */}
      {/* height={500} automatically provided */}
      {/* blurDataURL="data:..." automatically provided */}
      {/* placeholder="blur" - Optional blur-up while loading */}
    />
  )
}
```
  )
}


    Explicit sizing defines both the width and height. Next.js explicit sizing is identical to HTML <img> sizing.

```tsx
import Image from 'next/image'
 
export default function Page() {
  return (
    <Image
      src="https://s3.amazonaws.com/my-bucket/remoteImage.png"
      alt="Image remotely stored on an AWS bucket"
      width={500}
      height={500}
    />
  )
}
```



    Implicit sizing stretches the images to fill its parent. Next.js uses the fill property to expand the image to fill its parent element.

```tsx
import Image from 'next/image'
 
export default function Page() {
  return (
    <Image
      src="https://s3.amazonaws.com/my-bucket/remoteImage.png"
      alt="Image remotely stored on an AWS bucket"
      fill
    />
  )
}
```


    Remember, to improve LCP, we want to make sure there is enough space such that an image does not unexpectedly move other elements. 

The last consideration when optimizing images is cybersecurity. Malicious actors are always out to disrupt web pages. Fortunately, the <Image> component contains two primary configuration options to protect against online attackers: remotePatterns and loaderFile.

    remotePatterns: Allows Next.js applications to request only certain resources or allow certain directory paths. This configuration permits wildcards in the path if requesting images with varied names.

    Here is an example that only allows images using the https protocol accessed from https://awsBucket123.com/myImages/. Any other access point will return a 400 Bad Request.

```javascript
/* next.config.js */
module.exports = {
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: 'awsBucket123.com',
        port: '',
        pathname: '/myImages/**',
      },
    ],
  },
}
```



loaderFile: Allows a developer to use a cloud provider to optimize remote images instead of the Next.js built-in optimization API.

```javascript
/* next.config.js */
module.exports = {
  images: {
    loader: 'custom',
    loaderFile: './my/image/loader.js',
  },
}
```


Given the above config file, your loaderFile might look something like below:

```javascript
/* ./my/image/loader.js */
'use client'

export default function myImageLoader({ src, width, quality }) {
  return `https://awsBucket123.com/${src}?w=${width}&q=${quality || 75}`
}
```




## 🔤 Fonts


External fonts can place strain on webpages. Next.js optimizes fonts using the built-in Font module. The Font module downloads the required CSS and font files at build time, preparing fonts ahead of time and avoiding unnecessary layout shifts.

Next.js identifies and establishes all project fonts at build time, no additional network requests are sent.

Fonts are not globally available to each component. Fonts are accessible depending on where the font is created.

    If placed on the root layout, it is available on all routes
    If placed on a different layout, it is available on all routes wrapped by that layout
    If placed on an individual page, it is preloaded on the unique route for that page

Local fonts are created using the localFont() function call. Google fonts are created by importing them from 'next/font/google'. The following is an example of how to create a local font and a Google font using the Font module.

    You can reference the Next.js Github Google Fonts list to find available Google fonts. 

```typescript
/* Local Font */
import localFont from 'next/font/local'
 
const myFont = localFont({
  src: './some-font.woff2',
})

/* Google Font */
import { Comfortaa } from 'next/font/google'
 
const comfortaa = Comfortaa({
  subsets: ['latin'],
})
```


Each time a font is created using localFont() or 'next/font/google', it creates a new instance of a font in an application. This can result in multiple instances of the same font if created in various files. Instead, we can reuse a font, optimizing the Next.js application. There are 3 steps to reuse fonts.

    Create a font loader in a shared file
    Export the font loader as a constant
    Import the constant in each file you would like to use this font

```typescript
/* Loader.ts */
import localFont from 'next/font/local'
 
export const spaceMono = localFont({
  src: '../public/fonts/SpaceMono-Bold.ttf',
  variable: '--font-SpaceMono-Bold',
})
```

```tsx
/* Page.tsx */
import { spaceMono } from 'Loader.ts';

export default function Home() {
  return <h1 className={spaceMono.className}>HomePage</h1>;
}
```


## 📜 Scripts

Next.js also optimized importing third-party scripts with the `<Script>` component. It ensures that scripts are loaded only one time, even if referenced in multiple files.

    Remember, the FID is the First Input Delay. It measures the time taken for a webpage to respond to user interactions. 

The `<Script>` component minimizes the FID by reducing script load times. Scripts are preloaded by Next.js, preparing them to be executed when called upon.

The following is an example of how to load a script.

```tsx
<Script
    src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"
></Script>
```


We can further calibrate how the scripts are loaded. Depending on how busy a webpage is, scripts can be loaded at different times to ensure it doesn’t block other components, maintaining user interactivity and optimizing FID. There are four (4) ways to modify script loading via the strategy property.

    beforeInteractive: Loads the script before Next.js code is executed and before page hydration
    afterInteractive: (default) Loads the script immediately after the page becomes interactive, after the initial page hydration
    lazyOnload: Load the script later during the browser’s idle time
    worker: Delegate script handling to a web worker (this is experimental)

It can be helpful to know when the script is loaded. In Next.js, there are three (3) event handlers available to the `<Script>` component.

    onLoad(): Execute code after the script loads
    onReady(): Execute code after the script has finished loading and every time the component is mounted
    onError(): Execute code if the script fails to load

```tsx
/* app/page.tsx */
'use client'
 
import Script from 'next/script'
 
export default function Page() {
  return (
    <>
      <Script
        src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"
        strategy="beforeInteractive"
        onLoad={() => {
          console.log('Script has loaded')
        }}
        onReady={() => {
          console.log('Script has loaded and component is mounted')
        }}
        onError={() => {
          console.log('Script loading error')
        }}
      />
    </>
  )
}
```

## ⚙️ Config-Based Metadata

The last optimization feature is the Metadata API. The Metadata API helps define web application metadata to improve SEO (Search Engine Optimization) and drive web traffic. Next.js optimizes metadata by assisting in generating metadata.

We can define a Metadata object in two 2:

    Config-based metadata
    File-based metadata

This exercise will introduce Config-based metadata and the next exercise will introduce File-based metadata.

Config-based metadata focuses on adding metadata to individual pages, such as a title or description. This metadata is created using a static Metadata object or a dynamic generateMetadata() function call in layout.tsx or page.tsx. We’ll create 2 instances of Config-based metadata using the Next.js Metadata API.

    Static Metadata object. Static metadata is used when the metadata object will not change.

```typescript
import type { Metadata } from 'next'

export const metadata: Metadata = {
  title: 'Title of Page',
  description: 'Description of Page',
} 

export default function Page() {}
```


Dynamic Metadata object. If a Metadata object is variable based on input, we’ll need to use a dynamic object.

```typescript
import type { Metadata, ResolvingMetadata } from 'next'

export function generateMetadata({ params }) {
  return {
    title: params.title,
  }
}
```

## 📁 File-Based Metadata


Next.js also uses File-based metadata to optimize webpage accessibility. File-based metadata optimizes metadata through specific files:

    robots.txt: Information showing site structure and permitting search engine crawlers
    sitemap.xml: Assists in indexing websites and information regarding webpage timelines
    favicon.ico, apple-icon.jpg, icon.jpg: Optimized to add icons to webpage tabs
    opengraph-image.jpg, twitter-image.jpg: Assists in images when users share your webpage

File-based metadata has a higher priority and will override config-based metadata. We’ll focus on robots.txt and sitemap.xml to create 2 instances of File-based metadata using the Next.js Metadata API.

    robots.txt: robots.txt is a file in the root directory of the application to tell search engine crawlers which URLs they are allowed to access.

    We can generate a robots.txt programmatically with robots.ts. Here is an example of a Robots object, indicating which pages are permitted to be crawled. This example allows crawlers to access any route starting with the main route '/' while prohibiting access to the '/private route.

```typescript
import { MetadataRoute } from 'next'

export default function robots(): MetadataRoute.Robots {
  return {
    rules: {
      userAgent: '*',
      allow: '/',
      disallow: '/private/',
    },
    sitemap: 'https://mainPage.xml',
  }
}
```


sitemap.xml: sitemap.xml is a special file to help search engine crawlers index a site efficiently. It contains information about the last update, how often it updates, and relationships between all site pages.

We can generate a sitemap.xml programmatically with sitemap.ts. Here is an example of a Sitemap object containing all page routes and information regarding the last modified dates, how often they change, and their level of priority. The priority property indicates how Next.js application pages compare to one another for the search engine crawlers. The default page priority is 0.5 and ranges from 0.0 to 1.0.

```typescript
import { MetadataRoute } from 'next'

export default function sitemap(): MetadataRoute.Sitemap {
  return [
    {
      url: 'https://mainPage.com',
      lastModified: new Date(),
      changeFrequency: 'yearly',
      priority: 1,
    },
    {
      url: 'https://mainPage.com/route1',
      lastModified: new Date(),
      changeFrequency: 'monthly',
      priority: 0.7,
    },
    {
      url: 'https://mainPage.com/route2',
      lastModified: new Date(),
      changeFrequency: 'weekly',
      priority: 0.4,
    },
  ]
}
```


Metadata is evaluated in a specific order, starting from the root segment and going to each page. Metadata objects exported from multiple pages in the same route are shallowly combined to create a final metadata output. Duplicate metadata objects are removed based on ordering. 


Review Optimization Section:

Great work! You’ve learned how to optimize Next.js applications using images, scripts, fonts, and metadata.

Throughout the exercises, a Lighthouse score was presented to you. In order, those scores were:

Images and Priority:    54 -> 88
Images and Sizing:      88 -> 95
Fonts:                  95 -> 97
Scripts:                97 -> 98
Config-Based Metadata:  98 -> 98
File-Based Metadata:    98 -> 98


As noted in the first exercise, images drastically impact LCP. Conversely, metadata has a smaller impact because the files were pre-built with minor changes throughout the exercise.

Let’s recap:

  - Web applications can and should be optimized to minimize loading performance, interactivity delays, and visual stability.
  - Largest Contentful Paint (LCP) is the time from the start of the navigation until the largest block of content is visible to the user. This should occur within 2.5 seconds when the page initially loads.
  - First Input Delay (FID) is the time from when the user first interacts, such as a click, to when the browser begins processing the events. This should take no longer than .1 seconds or 100ms.
  - Cumulative Layout Shift (CLS) measures the largest burst of layout shift for every unexpected layout during the lifespan of a page. This should score less than .1.
  - Next.js has built-in tools to optimize images, fonts, scripts, and metadata.
  - Next.js contains a built-in <Image> component which extends the HTML <img> element with features for automatic optimization.
  - Next.js contains a built-in Font module to add web fonts with zero layout shift and zero requests to Google.
  - Next.js contains a built-in `<Script>` component to help load third-party scripts, only loading them once, even if the user navigates between pages.
  - Next.js has a Metadata API to help define application metadata for improved SEO and shareability.
  - Config-based Metadata exports a metadata object to a layout.tsx or page.tsx file.
  - File-based Metadata adds a statically or dynamically generated file to a route file.
  - Lighthouse is an open-source, automated tool to measure and assess web performance. Its primary goal is to enhance a website’s overall experience.


###### Next.js Deployment with Vercel:


Before Deploying

We’ve finished building our Next.js application, and we’d like to share it with others by deploying an optimized version of our application. Next.js makes getting our application deployment ready straightforward by providing the following:

    Out-of-the-box configurations like prefetching and code splitting.
    Built-in features like <Link> components.
    A next build command that generates a production-ready build.

Once we have an optimized build, we need to decide how we want to deploy our application. Next.js applications can be deployed in various ways like:

    Self-hosting in a Node.js server.
    Using a docker container.
    A limited static export.
    Using managed services like Cloudflare and Vercel.

In this article, we will deploy our Next.js application using a UNIX command line interface (CLI) and by connecting a git remote repo using Vercel.
Deploying To Vercel

Vercel is a front-end cloud provider and creator/maintainer of the Next.js framework, which makes deploying Next.js applications fast and easy.

We can deploy our Next.js applications to Vercel using the vercel CLI tool by:

    Installing the vercel CLI tool.
    Authenticating vercel with our Vercel account.
    Executing the vercel --prod command in our repo to deploy our application to production.
    Creating a feature branch and running the vercel command to deploy to a preview deployment.

Alternatively, we can deploy to Vercel using a GitHub repo by:

    Creating a new project in Vercel by setting up a connection to our GitHub account.
    Selecting the GitHub repo to deploy.
    Designating a production branch in our GitHub repo and deploying it to production.
    Creating automatic preview deployments by pushing feature branches to our GitHub repo.
    Creating automatic production deployments by merging pull requests to our production branch.




###### Next.js Deployment with Cloudflare

Before Deploying

We’ve finished building our Next.js application, and we’d like to share it with others by deploying an optimized version of our application. Next.js makes getting our application deployment ready straightforward by providing the following:

    Out-of-the-box configurations like prefetching and code splitting.
    Built-in features like <Link> components.
    A next build command that generates a production-ready build.

Once we have an optimized build, we need to decide how we want to deploy our application. Next.js applications can be deployed in various ways like:

    Self-hosting in a Node.js server.
    Using a docker container.
    A limited static export.
    Using managed services like Cloudflare and Vercel.

In this article, we will deploy our Next.js application using a UNIX command line interface (CLI) and by connecting a git remote repo using Cloudflare.
Deploying To Cloudflare

Cloudflare Pages is a front-end hosting service provided by Cloudflare. Before deploying Next.js applications to Cloudflare, it is important to understand that Cloudflare Pages can only host Node.js-like applications using the edge runtime. The edge runtime is a secure and lightweight environment that contains a subset of Web APIS, and therefore, not all Node.js features are available, like reading the file system.

We can deploy our Next.js applications to Cloudflare Pages using the wrangler CLI (a tool used to manage Cloudflare Workers and Pages) by:

    Enabling the edge runtime in Next.js applications.
    Installing the wrangler CLI tool.
    Authenticating wrangler with our Cloudflare account.
    Creating a new Cloudflare Page.
    Setting the nodejs_compat compatibility flag to enable Node.js in Cloudflare Pages.
    Installing and using the @cloudflare/next-on-pages adapter to build our Next.js application so they can be deployed in Cloudflare Pages.
    Creating preview deployments based on feature branches.
    Creating local deployments with the edge runtime.
    Using npm create cloudflare/latest to create and deploy a new Next.js project all in one go.

Alternatively, we can deploy to Cloudflare pages using a GitHub repo by:

    Setting up a Cloudflare Page connection to our GitHub account.
    Selecting the GitHub repo to deploy.
    Selecting the production branch.
    Selecting the Next.js framework preset.
    Enabling the nodejs_compat compatibility flag for production and preview deployments in the Cloudflare Page function settings.
    Creating automatic preview deployments by pushing feature branches to our repo.
    Creating automatic production deployments by merging pull requests into our production branch.

---



## 📚 **Additional Resources:**

<div align="center">

| **Resource** | **Description** | **Link** |
|--------------|-----------------|----------|
| **📖 Official Docs** | Complete Next.js documentation | [Next.js Docs](https://nextjs.org/docs) |
| **💬 Community** | Discussion forum and support | [GitHub Discussions](https://github.com/vercel/next.js/discussions) |
| **🎓 Learn More** | Advanced tutorials and courses | [Next.js Learn](https://nextjs.org/learn) |
| **📝 Blog** | Latest updates and best practices | [Vercel Blog](https://vercel.com/blog) |

</div>

---

<div align="center">

[![Next.js](https://img.shields.io/badge/Built%20with-Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/Powered%20by-React-61DAFB?style=flat&logo=react&logoColor=white)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/Written%20in-TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)

**Made with ❤️ for Next.js Learning**

</div>