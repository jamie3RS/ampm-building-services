# AMPM Building Services — Ghost theme

Custom Ghost theme for **AMPM Building Services Limited** — the M&E, fit-out, roofing and groundworks subsidiary of AMPM Group. Hosted on its own Ghost(Pro) at `ampmbuilding.services`.

Lives in the AMPM Group knowledge base under `04-website/ampm-building-services-theme/`.

---

## Structure

```
ampm-building-services-theme/
├── package.json
├── routes.yaml             ← upload separately in Ghost Admin → Labs → Routes
├── default.hbs             ← base layout (BS header, footer, fonts, palette)
├── custom-bs.hbs           ← slug-routed template — picks the right partial per page
├── index.hbs · post.hbs · page.hbs · tag.hbs · author.hbs · error.hbs
├── partials/
│   └── bs/
│       ├── header.hbs · footer.hbs       ← BS-branded chrome
│       └── home.hbs · services.hbs · about.hbs · work.hbs · contact.hbs
└── assets/
    ├── css/main.css        ← shared design tokens + layout primitives (lifted from AMPM Group)
    ├── css/bs-site.css     ← BS-specific styling (green lead colour, capability grid, etc.)
    └── favicon.svg         ← meridian four-quarter (shared brand)
```

## Content model

Five Ghost pages drive the five public routes via flat slugs and `routes.yaml` mapping:

| URL          | Page slug       | Template assignment (in Ghost Admin) |
| ---          | ---             | ---                                  |
| `/`          | `bs-home`       | "AMPM BS" (custom-bs)                |
| `/services/` | `bs-services`   | "AMPM BS"                            |
| `/about/`    | `bs-about`      | "AMPM BS"                            |
| `/work/`     | `bs-work`       | "AMPM BS"                            |
| `/contact/`  | `bs-contact`    | "AMPM BS"                            |

Page bodies are intentionally minimal — content is rendered by the template from `partials/bs/<section>.hbs`. To edit website copy, edit the partial and push.

## Auto-deploy

GitHub Actions workflow at `.github/workflows/deploy-theme.yml` uses `TryGhost/action-deploy-theme@v1` to upload the theme on every push to `main`. Requires two repo secrets:

- `GHOST_ADMIN_API_URL` — e.g. `https://ampmbuilding.ghost.io`
- `GHOST_ADMIN_API_KEY` — from Ghost Admin → Settings → Integrations → custom integration `id:secret`

## Brand notes

- **Lead colour:** `--bs-lead: #3D8E2E` (working green)
- **Meridian:** shared with AMPM Group — `#E8742C / #5BAA47 / #2E5FAB / #7A2E8F`
- **Typography:** Source Serif 4 · Inter Tight · JetBrains Mono (shared with the brand family)
- **"Part of AMPM Group"** badge is intentionally prominent in the header and footer.

## Email

Email convention: `@ampm.co.uk` (per Group policy, all new entities consolidate on the Group's email domain).
- General: `hello@ampm.co.uk`
- Tender: `tenders@ampm.co.uk`
- Supply chain: `suppliers@ampm.co.uk`
- Careers: `careers@ampm.co.uk`
- MD: `dan.small@ampm.co.uk`
