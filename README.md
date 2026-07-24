# Crudo Store demo

A static GitHub Pages storefront and role-based dashboard for a compatible Crudo API. Live site: https://demo-crudo.github.io/.

## API

The page works with compatible Crudo API configurations. It calls endpoints such as `/products`, `/tokens`, `/users`, `/me`, `/addresses`, `/purchases`, `/top-ups`, `/transactions`, `/payment-methods`, `/challenge`, and the documented `/admin/*` endpoints. Enter any compatible custom API base URL with the **API base URL** control at the top of the page; the default is `http://127.0.0.1:3000/v1`.

The API must allow the page origin through CORS. API URL and session data are stored locally in the browser; use the demo `admin` / `admin` account only for local demonstration, never as a real credential. Balance top-ups create simulated demo credits, not payments.

`/challenge` must provide ALTCHA PBKDF2/SHA-256 challenges. Both registration and sign-in require a verified ALTCHA proof; the invisible browser component generates it automatically during submission and supplies its Base64 JSON `altcha` value in the JSON request body. Challenges are one-time and reset after every submission. The app loads the official pinned ALTCHA browser component from `https://cdn.jsdelivr.net/npm/altcha@3.2.1/+esm`, so this CDN must be reachable (or be permitted by the applicable content-security policy).

`GET /payment-methods` is optional capability metadata. When available, its returned array is displayed without assuming specific assets, networks, or payment schemes; failure only marks payment capabilities unavailable. If an authenticated purchase returns HTTP 402, the chosen product remains open, the API-provided payment information is shown when present, and **Add balance** takes the customer to the demo-balance form with the shortfall prefilled. Customers selecting a product while signed out are asked to register or sign in, then return to its purchase confirmation after authentication.

## Run locally

Serve this directory with any static server, for example:

```sh
python3 -m http.server 8080
```

Open `http://localhost:8080`, then set the API URL at the top of the page.
