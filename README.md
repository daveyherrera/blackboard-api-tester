# Blackboard API Tester

> **This is an AI generated initiative.**

A standalone, browser-only tool for exploring and testing the Blackboard LMS REST API. No installation or backend required — runs entirely from a single HTML file and can be hosted anywhere, including GitHub Pages.

---

## Features

- Browse and search all Blackboard LMS REST API endpoints from versioned Swagger specs
- Send authenticated requests directly to any Learn instance from the browser
- Auto-detects your instance version and selects the matching API spec
- Body editor with syntax highlighting, line numbers, and Minimal / Full payload templates
- Required entitlements shown with human-readable descriptions for every endpoint
- Full request log with status codes and response times

---

## Getting started

### 1. Add a client

Open **Settings** and click **+ Add Client**. Fill in:

| Field | Description |
|---|---|
| **Name** | A friendly label (e.g. `DevCon`, `Staging`) |
| **URL** | Your Learn instance root, e.g. `https://devcon.blackboard.com` |
| **App Key** | The application key from your REST API integration |
| **Secret** | The application secret from your REST API integration |
| **API Version** | Leave blank to use the latest, or pick a specific version |

Click **Save**, then **Activate** the client. The sidebar footer will update to show the active client and its detected API version.

> **Where to find your App Key and Secret:** Register your application on the [Blackboard Developer Portal](https://developer.blackboard.com) — credentials are issued there, not from within Blackboard LMS.

---

### 2. Get credentials from the Blackboard Developer Portal

App Key and Secret come from the **Blackboard Developer Portal**, not from within Blackboard LMS:

1. Register your application at the [Blackboard Developer Portal](https://developer.blackboard.com) to receive an **Application ID**, **App Key**, and **Secret**.
2. Log into Blackboard LMS as a **System Administrator**.
3. Go to **Administrator Panel → Integrations → REST API Integrations**.
4. Select **Create Integration** and enter the **Application ID** from the Developer Portal.
5. Set the **Learn User** the integration should act as (use a dedicated integration user).
6. Set **End User Access** to *Yes* or *No* depending on whether individual users will authenticate.
7. Select **Submit** to save.

> **CORS required:** Because this tool makes browser-to-Learn requests, you must allow this app's origin in your Learn instance. Go to **Administrator Panel → Integrations → Cross-origin Resource Sharing → Create Configuration** and set:
> - **Origin:** the URL where the tester is running (e.g. `https://daveyherrera.github.io` or `http://localhost:8099`)
> - **Allowed Headers:** `Authorization`
> - **Available:** Yes → Submit
>
> The Settings page shows the current origin so you know exactly what to enter.

---

### 3. Search and select an endpoint

Use the search bar to find an endpoint by name, path, or tag (e.g. `Create User`, `/courses`, `gradebook`). Select one from the dropdown and the tool will:

- Show the full URL with path parameters highlighted
- Display a plain-English description of what the endpoint does
- List all required entitlements with descriptions
- Pre-fill the Body editor with the minimal required payload

---

### 4. Fill in parameters

Depending on the endpoint, you'll see tabs for:

- **Path Params** — required identifiers in the URL (e.g. `{courseId}`). Use the type picker to switch between `pk1`, `externalId`, `courseId`, etc.
- **Query Params** — optional filters. Check the box next to any param to include it.
- **Body** — JSON payload for POST/PUT/PATCH requests. Use **Minimal** to load only required fields, or **Full** to see all available fields.

---

### 5. Send the request

Click **Send**. The response card shows:

- HTTP status code (green for 2xx, red for errors)
- Response time in milliseconds
- Response body with syntax highlighting
- Response headers
- For errors: the Swagger description of that status code

Use **cURL** to copy the equivalent `curl` command for use in a terminal or sharing with teammates.

---

## API version picker

The **API Version** dropdown lets you switch between Blackboard LMS REST API versions (from `3900.94.0` up to the latest). The app auto-detects your instance version on load and selects the closest matching spec.

---

## Running locally

No build step required:

```bash
cd blackboard-api-tester
python3 -m http.server 8099
# Open http://localhost:8099
```

---

## Deploying to GitHub Pages

1. Fork or push this repo to your GitHub account
2. Go to **Settings → Pages → Source → GitHub Actions**
3. Push to `main` — the included workflow deploys automatically

Your app will be live at `https://<username>.github.io/<repo-name>/`.

---

## Credentials & privacy

- App Key and Secret are stored in your **browser's `localStorage` only**
- They are never sent anywhere except your own Learn instance
- Tokens are fetched directly from your instance and kept in memory for the session

---

## Supported API versions

`4000.20.0` · `4000.19.0` · `4000.18.0` · `4000.17.0` · `4000.16.0` · `4000.15.0` · `4000.14.0` · `4000.13.0` · `4000.12.0` · `4000.11.0` · `4000.10.0` · `4000.9.0` · `4000.8.0` · `4000.7.0` · `4000.6.0` · `4000.5.0` · `4000.4.0` · `4000.3.0` · `4000.2.0` · `4000.1.0` · `3900.98.0` · `3900.97.0` · `3900.96.0` · `3900.95.0` · `3900.94.0`
