# Crudo Store demo

A static GitHub Pages storefront and role-based dashboard for a compatible Crudo API. Live site: https://demo-crudo.github.io/.

## API

The page works with compatible Crudo API configurations. It calls endpoints such as `/products`, `/tokens`, `/users`, `/me`, `/purchases`, `/top-ups`, `/transactions`, and the documented `/admin/*` endpoints. Enter any compatible custom API base URL with the **API base URL** control at the top of the page; the default is `http://127.0.0.1:3000/v1`.

The API must allow the page origin through CORS. API URL and session data are stored locally in the browser; use the demo `admin` / `admin` account only for local demonstration, never as a real credential. Balance top-ups create simulated demo credits, not payments.

## Run locally

Serve this directory with any static server, for example:

```sh
python3 -m http.server 8080
```

Open `http://localhost:8080`, then set the API URL at the top of the page.
