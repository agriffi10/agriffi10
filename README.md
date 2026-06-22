## 👋 About me

Hey, I'm Andrew. I've spent 10+ years in software and worn a lot of hats along the way — I started out as a frontend engineer, got deep into accessibility, and over time grew into platform and data work. I write SDKs, infrastructure, and the data pipelines that everything else runs on.

These days I mostly build cloud-native data platforms and developer tooling in AWS. The work I like best is owning a problem end to end. Scoping it, shaping the architecture, shipping it, and watching people actually use it. That frontend background still sneaks in whenever I'm thinking about how a platform feels to the people building on it.

Fun fact: my degree is a BFA in Computer Game Design, so I came into all this from a pretty unusual angle.

## ⬆ What I'm up to

Leaning further into platform and data engineering and building developer tools, internal platforms, and the AI/LLM infrastructure space. I'm also tinkering with open source on the side (see below).

## 🛠 Projects

### Data Analysis Tool - a serverless, multi-tenant data workspace on AWS
[Live Site](https://d1kbh4bnvh1je8.cloudfront.net)

Codebase walkthrough available upon request.

A web portal where authenticated users bring their own data, manage it, and query it with SQL all in the browser, with no backend server. A React + TypeScript SPA talks directly to AWS using short-lived, scoped credentials.

Users can:

- **Upload & manage files** in their own private S3 space — download, move, rename, copy, delete, and organize into folders, with a familiar filesystem-style UX.
- **Define tables over their data** — register schemas in the Glue Data Catalog and create views directly from the app.
- **Query with SQL through Amazon Athena** — an in-app query workspace (Monaco editor, schema browser, multi-tab, database switcher) runs interactive queries and saves results back to their own files.

Every user is confined to their own data at the IAM layer, not in app code. A Cognito Identity Pool stamps a verified `username` principal tag server-side (ABAC), and a single shared IAM role scopes S3 prefixes, Glue databases/tables, and Athena results to `${aws:PrincipalTag/username}` so tenancy can't be spoofed by the client. Lake Formation registers the user-space bucket in hybrid mode to extend the same model to the analytics catalog.

The entire stack, auth, storage, analytics, and per-user IAM is provisioned with OpenTofu and shipped through GitHub Actions via OIDC.

**Stack:** React 18 · Vite · TypeScript (strict) · TanStack Query · AWS SDK v3 · Cognito/Amplify · Athena + Glue + Lake Formation · OpenTofu · GitHub Actions

## 📫 How to reach me

Find me on LinkedIn! The link is on my GitHub profile.

## 🙋 Ask me about

- AWS & infrastructure-as-code ☁️
- Developer tooling & observability 🔎
- Video Games 🎮
- Coffee ☕
