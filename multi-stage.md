# Multi-stage Dockerfile (Dev vs Production)

This Dockerfile uses a **multi-stage build** to create an optimized production image for a frontend application (React / Vue / Angular).

The key idea is:
> **Build the app with Node.js, then serve the built static files with Nginx.**

---

## Dockerfile

```dockerfile
FROM node:alpine AS builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
```

<img width="1151" height="447" alt="image" src="https://github.com/user-attachments/assets/2cb991ea-b214-4482-b23f-bc6aef006830" />

🚢 Dev vs Production: Why Frontend Dockerfiles Look Different

One thing that often confuses people new to Docker is this:

“Why do we run npm start in development, but npm run build in production?”

The answer comes down to how frontend apps are meant to run.

🔹 Development

We run npm start

Node.js serves the app

Hot reload, source maps, file watching

Optimized for developer experience, not performance

🔹 Production

We run npm run build

This generates optimized static files (HTML, CSS, JS)

No hot reload, no rebuilds, no dev tooling

That’s where multi-stage Docker builds shine 👇

1️⃣ Stage 1 (Node.js)
Use Node only to:

Install dependencies

Build the app (npm run build)

2️⃣ Stage 2 (Nginx)

Copy only the build output

Serve static files with Nginx

No Node, no npm, no source code

✅ Smaller image
✅ Faster startup
✅ Better security
✅ Production best practice

Mental model:

Dev: Browser → Node dev server → source code

Prod: Browser → Nginx → pre-built static assets

Once this clicks, frontend Dockerfiles suddenly make a lot more sense.
