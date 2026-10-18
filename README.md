# job_offers

A take-home task: answer geographic questions about a dataset of job offers.

The umbrella has two apps:

- **`job_offers`** — the domain logic. Loads job offers and professions from CSV
  (`apps/job_offers/priv`), groups the offers by continent and profession,
  and finds the offers within a radius of a point (great-circle
  distance).
- **`job_offers_service`** — a Phoenix API on top of it. The dataset is loaded
  once into a `GenServer` at startup, and requests are served from memory:

```
GET /jobs/offers/filter?lat=48.85&lon=2.35&radius=10
```

```sh
mix deps.get
mix test
mix phx.server
```
