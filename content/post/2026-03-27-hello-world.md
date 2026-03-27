---
title: "Hello World"
date: "2026-03-27"
categories: ["mergram"]
---

Welcome to the Mergram engineering blog. This is where we write about the technical problems we run into while building Mergram — no fluff, just the interesting parts.

## What is Mergram?

Mergram is a PDF mail merge tool. You upload a PDF template and an Excel spreadsheet, place data fields onto the document using a visual canvas editor, and generate personalized PDFs in bulk. It also supports sending those PDFs as email attachments via SMTP.

The stack:

- **Frontend** — React 18, TypeScript, Vite, Tailwind CSS, Fabric.js for the canvas editor
- **Backend** — Node.js, Express, Drizzle ORM, PostgreSQL
- **Worker** — Background job system with `SELECT FOR UPDATE SKIP LOCKED` for concurrency-safe PDF generation
- **Infrastructure** — Turborepo monorepo, Docker, S3-compatible storage, LemonSqueezy for billing

## Why a blog?

Building a product that touches PDF rendering, canvas manipulation, background job processing, credit-based billing, and browser-to-server code sharing means we run into a lot of problems that aren't covered by a typical "build a CRUD app" tutorial.

Some examples of what we'll write about here:

- **Render driver abstraction** — We share PDF rendering logic between the browser (for live previews) and the server (for bulk generation). The browser uses Canvas APIs and data URLs; the server uses Buffers and native libraries. Same interface, two implementations. This pattern has tradeoffs worth discussing.
- **Worker reliability** — Background jobs that process thousands of PDFs need pause/resume, retry logic, stale lock recovery, and progress streaming. We learned a lot getting this right.
- **Credit system correctness** — Atomic deductions with SQL-level guards, idempotent allocations, and the edge cases around enterprise plans with "unlimited" credits.
- **Canvas editor** — Layering a Fabric.js interactive canvas on top of react-pdf's PDF viewer, handling coordinate systems, zoom, field serialization, and cross-browser quirks.

## What to expect

Posts will be technical and specific. We won't rehash documentation — we'll talk about the problems that made us reach for the documentation in the first place. If a post helps one person avoid the same rabbit hole we fell into, it's worth writing.

Thanks for reading.



