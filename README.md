# 📚 Next.js Comprehensive Guide

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

### CSS Modules
- Great way to prevent style name collision by modularizing CSS files
- Files will be processed as a CSS Module if appended with the `.module.css` extension
- Location-wise, CSS Module files can be colocated with the component they are styling

### Global CSS
- Can apply a style to the entire application
- The global CSS file can be imported into any page or layout
- A layout is a special component that will be detailed in the upcoming Routing lesson
- Typically, the global CSS file is imported into the root layout, a layout file that sits in the `/app` directory

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










































































































































**Made with ❤️ for Next.js Learning**
