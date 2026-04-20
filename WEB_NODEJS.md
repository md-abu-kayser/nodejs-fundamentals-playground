# Fundamentals of Web Application with Nodejs

## 1. How The Web Works?

The web is a network of clients and servers communicating over HTTP/HTTPS. A browser or other client sends a request to a server URL, the server processes that request, and sends back a response. Key components:

- Browser: renders HTML, CSS, JavaScript and requests resources.
- Server: hosts applications, APIs, files, and responds to requests.
- URL: locates resources using a protocol, domain, path, and optional query.
- DNS: translates a domain name into an IP address.
- HTTP/HTTPS: the protocol for request/response messages.
- TCP/IP: transports the data packets across the internet.

Request lifecycle:

1. User enters a URL.
2. Browser resolves domain through DNS.
3. Browser establishes a TCP connection to the server.
4. Browser sends an HTTP request.
5. Server processes and returns an HTTP response.
6. Browser renders the response.

Important web concepts:

- Stateless communication: each HTTP request is independent.
- Cookies and tokens: used to manage sessions and authentication.
- Caching and CDNs: improve performance by storing content closer to users.

## 2. Frontend, Backend Development

Frontend development handles the user-facing part of applications:

- HTML: structure of pages.
- CSS: visual styling.
- JavaScript: interactivity, DOM manipulation, client-side logic.
- Frameworks/libraries: React, Vue, Angular, Svelte.
- Browser runtime: executes frontend JS, handles events, updates UI.

Backend development handles server-side logic and data:

- Application logic: business rules, authentication, authorization.
- Databases: storing and retrieving data (SQL or NoSQL).
- APIs: expose endpoints for frontend or other clients.
- Servers: Node.js, Python, Java, Go, PHP, etc.
- Middleware: request processing before handlers run.

Full-stack development combines both frontend and backend in one project or team. In modern web apps, the frontend often consumes backend APIs.

## 3. Web Application Scaling

Scaling means making an application handle more users or load. Two common approaches:

- Vertical scaling: add more resources to a single machine (CPU, RAM, faster disks).
- Horizontal scaling: add more machines or instances and distribute traffic.

Factors in scaling:

- Traffic volume: concurrent users and requests per second.
- Data size: database growth and queries.
- Resource bottlenecks: CPU, memory, disk I/O, network.
- State management: session storage, caching, and stateless services.

Scaling patterns:

- Load balancing: distribute requests across multiple servers.
- Caching: reduce repeated work using in-memory caches or CDNs.
- Database sharding and replication: split and replicate data for performance.
- Microservices: divide functionality into smaller services for independent scaling.

## 4. Static Website vs Dynamic Website

Static website:

- Consists of fixed files like HTML, CSS, JavaScript, images.
- Content is the same for every visitor.
- Fast and easy to host, often served from CDNs.
- Good for landing pages, documentation, blogs without user-specific content.

Dynamic website:

- Generates pages or data on demand using server-side code or client-side JS.
- Content can change based on user, time, or request parameters.
- Requires runtime processing and often a database.
- Example: e-commerce stores, dashboards, social media.

Comparison:

- Performance: static sites are faster and simpler.
- Flexibility: dynamic sites support personalization, search, user accounts.
- Complexity: dynamic sites require backend logic and infrastructure.

## 5. Dynamic Website using API

A dynamic website can use APIs to fetch data or actions without full page reloads. Common pattern:

- Browser sends API request (XHR/fetch/Axios) to a backend endpoint.
- Backend returns JSON, HTML fragments, or other data.
- Browser updates the page dynamically using JavaScript.

Example flow:

1. User opens a dashboard.
2. Frontend calls `GET /api/user/profile`.
3. Backend reads the database and returns user data.
4. Frontend renders the data inside the page.

APIs allow:

- interactive pages,
- partial updates,
- SPA architecture,
- mobile app integration,
- decoupling frontend and backend.

## 6. Benefits of using API

APIs provide a clean contract between systems.
Benefits include:

- Reusability: same API can serve web, mobile, desktop, or third-party clients.
- Decoupling: frontend and backend can evolve independently.
- Scalability: APIs can be scaled separately from the UI.
- Security: APIs centralize authentication and authorization.
- Maintainability: clear endpoints and versioning improve long-term support.
- Automation: APIs support scripts, bots, and integrations.

## 7. JavaScript runtime in browser

In the browser, JavaScript runs inside a JavaScript engine like V8 (Chrome), SpiderMonkey (Firefox), or JavaScriptCore (Safari). Browser runtimes provide:

- `window` and `document` objects.
- DOM APIs to read and manipulate HTML/CSS.
- Fetch/XHR for network requests.
- Event loop for handling user input and asynchronous tasks.
- Web APIs such as `localStorage`, `sessionStorage`, `WebSockets`, `Canvas`, `WebGL`.

The browser runtime is sandboxed for security, restricting access to file system or raw network sockets.

## 8. What if we can use JS?

Using JavaScript beyond the browser means it can run on servers and other environments.

- Server-side JS can serve APIs and web applications.
- JS can be used for command-line tools, build systems, scripting, and automation.
- It enables a unified language across frontend and backend.

This led to platforms like Node.js, which let JavaScript access file systems, networking, databases, and process control.

## 9. What is Node.js?

Node.js is a JavaScript runtime built on the V8 engine. It allows JavaScript to run outside the browser and provides server-side APIs for building networked applications. Core features:

- Event-driven architecture.
- Non-blocking I/O.
- Built-in modules for `fs`, `http`, `path`, `crypto`, `stream`, and more.
- NPM ecosystem for packages.

Node.js is commonly used to build web servers, APIs, CLI tools, real-time applications, and microservices.

## 10. Why Node.js is popular?

Key reasons for Node.js popularity:

- JavaScript everywhere: same language on client and server.
- Fast performance: V8 engine compiles JS to optimized native code.
- Non-blocking I/O: handles many concurrent connections efficiently.
- Large ecosystem: NPM provides hundreds of thousands of libraries.
- Lightweight and extensible: easy to build small services and prototypes.
- Strong community: many tutorials, frameworks, and enterprise adoption.

## 11. Cons of using Node.js?

Downsides to consider:

- Single-threaded event loop: long-running CPU tasks can block the entire process.
- Callback complexity: can lead to hard-to-read code if not handled with Promises/async-await.
- Maturing ecosystem: some packages may have inconsistent quality.
- Not ideal for CPU-heavy work: tasks like image processing or large computations may require worker threads or a different language.
- Callback stack traces: debugging asynchronous code can be harder.

## 12. Dependencies of Node.js

Node.js depends on several core technologies:

- V8: JavaScript engine from Chromium.
- libuv: asynchronous I/O library for event loops, file system, networking, and threading.
- OpenSSL: crypto and TLS support.
- c-ares: DNS resolution library.
- zlib: compression.
- ICU: Unicode and globalization support.
- HTTP parser: request and response parsing.

These dependencies power Node.js features such as networking, security, and cross-platform support.

## 13. Event Driven Architecture of Node.js

Node.js uses event-driven architecture around a central event loop.

How it works:

- Events are emitted by sources like timers, sockets, or file reads.
- Callbacks or event listeners are registered for those events.
- When the event occurs, the callback runs.

This model enables asynchronous programming and high concurrency by avoiding blocking waits. Instead of pausing for I/O, Node.js continues processing other work and handles results later.

Example:

- `fs.readFile()` starts reading a file and returns immediately.
- Once the file is ready, Node.js emits an event and runs the callback.

This architecture is ideal for I/O-heavy workloads like web servers and APIs.

## 14. Single Threaded Node.js vs Multithreaded Server

### Single Threaded Node.js

Node.js runs JavaScript in a single main thread. Because most server work is I/O-bound, non-blocking calls let Node.js handle many requests without multiple threads.

Advantages:

- Simpler concurrency model.
- Fewer race conditions.
- Lower memory overhead.

Disadvantages:

- A heavy CPU task can block the event loop.
- Cannot use shared-memory multithreading for request handling by default.

### Multithreaded Server

Traditional multithreaded servers use multiple threads to handle requests in parallel.

Advantages:

- Better for CPU-bound workloads.
- Each request can run independently on its own thread.

Disadvantages:

- More complex concurrency.
- Higher memory usage.
- Need careful locking and synchronization.

### I/O Intensive Task

Node.js excels at I/O-intensive tasks because it can start many I/O operations and handle callbacks when they complete. It does not block while waiting for disk, network, or database responses.

### CPU Intensive Tasks

CPU-intensive tasks can block Node.js. To manage them:

- offload work to worker threads,
- use child processes,
- move heavy computations to native modules or separate services.

### Horizontal Scaling

Horizontal scaling adds more server instances behind a load balancer. Node.js apps can be scaled horizontally by:

- running multiple processes on the same machine,
- using Docker containers,
- deploying across multiple machines.

Horizontal scaling is often the most practical way to increase throughput.

### Vertical Scaling

Vertical scaling means adding more CPU, RAM, or faster storage to a single server. It can improve performance, but it has limits and is generally less flexible than horizontal scaling.

## 15. How Node.js handles multiple requests?

Node.js uses an event loop and non-blocking I/O. When requests arrive:

- Node accepts the request and schedules work.
- If the work is I/O-bound, Node performs it asynchronously.
- The main event loop continues accepting other requests.
- When I/O completes, the callback executes to finish the request.

This means Node.js can keep many connections open and delegate I/O without using one thread per request.

### Non-blocking I/O

Non-blocking I/O means the server does not wait for an operation to finish before moving on. Instead, Node.js initiates the operation and uses callbacks or Promises to handle the result later.

Example:

- `readFile` returns immediately.
- Node handles other requests.
- After reading finishes, callback runs.

This is the core reason Node.js can handle high concurrency with fewer resources.

## 16. Runtime Differences & the Game Changer Concept of IIFE

### Browser runtime

Browser runtime includes:

- DOM and BOM APIs (`document`, `window`, `navigator`).
- Event handling for clicks, keyboard, network.
- UI rendering and layout engine.
- Browser security model and sandbox.
- Browser-specific features like `localStorage`, `serviceWorker`, and `fetch`.

### Node.js runtime

Node runtime includes:

- `global` object instead of `window`.
- Built-in modules like `fs`, `http`, `path`, `os`.
- Access to file system and network sockets.
- `process` object for environment, arguments, and exit codes.
- Module loading system (`require`, `import`).

### IIFE (Immediately Invoked Function Expression)

IIFE is a pattern where a function is defined and executed immediately. It is useful for creating a local scope and avoiding global variables in both browser and Node.js code.

Example:

```js
(function () {
  const privateValue = 42;
  console.log("IIFE executed");
})();
```

**Why it is a game changer:**

- Creates encapsulation before modules became standard.
- Avoids polluting the global scope.
- Allows initialization code to run immediately.

In modern Node.js, modules provide scope, but the IIFE pattern still appears in bootstrapping and legacy code.

## 17. Exploring CommonJS, Import, Export & Name Alias

CommonJS is Node.js’s original module system.

**Example export:**

```js
// math.js
function add(a, b) {
  return a + b;
}
module.exports = { add };
```

Example import:

```js
const { add } = require("./math");
console.log(add(2, 3));
```

Named alias example:

```js
const { add: sum } = require("./math");
console.log(sum(2, 3));
```

CommonJS details:

- `require()` loads modules synchronously.
- `module.exports` and `exports` expose functionality.
- Works in Node.js by default.

## 18. Exploring ESM & transforming CommonJS to ESM

ESM (ECMAScript Modules) is the standardized module format.

Example export:

```js
// math.mjs or package.json type: module
export function add(a, b) {
  return a + b;
}
```

Example import:

```js
import { add } from "./math.mjs";
console.log(add(2, 3));
```

ESM advantages:

- Static analysis for tree shaking and better tooling.
- Standard syntax across browser and Node.
- `import`/`export` support top-level scope and asynchronous loading.

Transforming CommonJS to ESM:

- Replace `module.exports =` with `export default` or named exports.
- Replace `require()` with `import`.
- Use `export const` or `export function` for named exports.

CommonJS:

```js
const fs = require("fs");
const { add } = require("./math");
module.exports = { add };
```

ESM:

```js
import fs from "fs";
import { add } from "./math.js";
export { add };
```

If using Node.js with `package.json`:

```json
{
  "type": "module"
}
```

Or use `.mjs` file extension when mixing module formats.

---

This document is designed for interview preparation, with a focus on the core concepts, real-world usage, and the differences between browser and Node.js runtimes.

---
